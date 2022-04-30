# SAE-21
## Construire un réseau informatique pour une petite structure</br></br> 

## 24/03/2022 (td):

Premier pas dans cette SAE avec la présentation du sujet par Frederic Comby. 

## 25/03/2022 (td):

Revoir, cette fois-ci, en groupe tous les objectifs, les livrables et toutes les consignes d'exécution.

## 28/03/2022 (td):

Suite à un brainstorming chacun à choisi sa partie suivant nos capacités ou par préférence. La **répartition des tâches** est donc la suivante : 

Adrien BOURLANGES-GABARRE : La partie vituelle sur GNS3.</br></br>
Thibault Garcia : Création des serveurs Web (Physique + Virtuel)</br></br>
Moi : Configuration du routeur externe en physique.</br></br>

## 08/04/2022 (tp):

Recherches configuration du routeur avec le pare-feu, protocole etc. 

## 14/04/2022 (td):

Faire un point avec le groupe + continuer les recherches.

## 15/04/2022 (td+tp):

Séances entièrement dédiées aux essais de la premiere version du firewall du MikroTik pour ce rendre compte à la fin avec, Philippe Pujas, que les paquets acceptés et bloqués n'était pas les bons et que donc le firewall laisait passer ce qu'il ne fallait pas.  </br>
Propriétés de base du routeur (onglet Quickset):</br>
<img src="https://github.com/guilhemmas/SAE-21/blob/main/Mikrotik_quickset.png"/> </br></br>

- Pour commencer j'ai tapé cette commande dans le terminal du routeur en tant que prmier filtre pour le firewall:
<img src="https://github.com/guilhemmas/SAE-21/blob/main/Config1_Firewallport80.png"/> </br>
Cette commande permet d'accepter les paquets en entré ayant comme port de destination le Port 80 en TCP.
- J'ai ensuite rajouté un deuxième filtre, exactement le même que le précédent, mais cette fois pour laisser passer les paquets entrant sur le Port 53 en UDP. 
- Pour finir le dernier filtre permettait de drop tous les autres paquets entrant mais sans aucunes autres précisions. </br></br>

Au final le firewall ressemblait à cela :
<img src="https://github.com/guilhemmas/SAE-21/blob/main/Congi1firewall.png"/> </br>
## 21/04/2022 (2 td):

Problème sur le routeur MikroTik n°17 impossible d'arriver à me reconnecter dessus, même avec le reset et tout ce qui est adressage sur ma machine (adresse ip de ma machine sur le même réseau que le routeur et en ayant ajouté l'adresse du routeur en tant que route par défaut sur ma machine) il etait impossible d'accéder à la page de configuration MikroTik. J'ai perdu 1h40 à essayer de résoudre ce problème et je me suis dit que de toute façcon la configuration précédente, étant pas la bonne, j'ai décidé de prendre un nouveau routeur MikroTik n°2 et de tout recommencer à 0.</br></br>

J'ai décidé cette cette fois-ci grâce à la discussion avec Monsieur Pujas puis aussi grâce aux recherches d'utiliser la politique FORWARD car elle permet à un administrateur de contrôler où les paquets peuvent être routés au sein d'un LAN. Par exemple, pour autoriser la retransmission du LAN entier. Comme on peut voir sur les captures d'écarn ci-dessus, il n'y a que les nouveaux paques et les paquets déjà connus qui sont acceptés. Ce choix s'est fait pour les paquets TCP donc pour le port 80 mais aussi les paquets UDP et donc sur le port 53 : </br></br>
Paquets TCP:
<img src="https://github.com/guilhemmas/SAE-21/blob/main/Config2TCP.png"/> </br></br></br>
Paquets UDP:
<img src="https://github.com/guilhemmas/SAE-21/blob/main/config2UDP.png"/> </br></br></br>
Le reste est DROP:
<img src="https://github.com/guilhemmas/SAE-21/blob/main/config2DROP.png"/> </br></br></br>

## 22/04/2022 (tp):

Finition de la config routeur en voyant avec Adrien les adresses qu’il a distribué au Serveur WEB et aussi au Routeur se trouvant dans la partie virtuelle pour pouvoir ajouter l’accès sur le firewall du routeur MikroTik. Et ensuite on a fait tous les tests pour cloturer cette SAE. Pour ma part, le firewall semblait fonctionner comme il le fallait. Les filtres ajoouter sont les bons.

