Architecture générale :
* Socle de base : 4me.core
* Briques additionelles : 4me.xman, 4me.arcid, 4me.eap

Architecture 4me.core :
* 4me.core.ui : framework d'UI basé sur angular et angular material, accepte des plugins via une API à définir
* 4me.core.mapping : webservice qui conserve un mappage de la salle en mémoire et effectue le mapping position/secteur, envoie des events sur la message queue
* 4me.core.mapping.ui-plugin : plugin interface CDS mapping
* 4me.core.mq : message queue, AMQP seul ? Webservice ? Gestion des websockets ?

MicroServices :
* 4me.xman
* 4me.arcid
* 4me.eap
* 4me.meteo ?
* 4me.cigale ?

4me.xman :
* 4me.xman.client-ui-plugin : plugin ui du client XMAN, affichage des réductions de vitesse, filtrage par secteur
* 4me.xman.manager-ui-plugin : plugin ui XMAN pour le chef de salle : affichage de la liste globale
* 4me.xman.service : 
  * recevoir les données des AMAN, les stocker dans une bdd (quel format ? polling XML ? cluster AMQP ?)
  * transmettre aux clients les réductions de vitesse à appliquer (envoyer via 4me.mq ?)
  * recevoir les réductions données par les clients
  * compiler et transmettre les statistiques vers l'ui chef de salle