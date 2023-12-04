# Compte rendu d'alternance mensuel

### Entreprise : Société Générale

### Maître d'apprentissage : Pascal Rat, pascal.rat@socgen.com

### Tuteur pédagogique : Antoine Nongaillard, antoine.nongaillard@univ-lille.fr

### Début du contrat : 25/09/2023

## Introduction contextuelle

Je travaille, depuis mon arrivée en stage, sur le pilotage de la liquidité. J'ai été repris en alternance par une autre équipe et sur d'autres sujets par manque de budget dans l'ancienne. 

Mon ancienne équipe (Illiqo) s'occupait de la partie restitution des données de liquidité, elle était le dernier maillon avant les utilisateurs (la direction financière).

Ma nouvelle équipe (BSDQM sous-équipe de Basyliq) s'occupe principalement du module "Fond De Carte" dit FDC.
 Le but de ce module est de récupérer au mieux des données de liquidité sur les entités du groupe qui n'ont pas la possibilité de les créer/transmettre (ex. entité trop petite pas de section informatique, problèmes "politiques") sous le format standardisé ABL.
La récupération de ces données se fait par conséquent depuis les données comptables qui sont légalement obligatoires.

Le contexte de mon recrutement est la migration d'un système legacy coûteux et difficile à maintenir (Informatica, Oracle) vers l'architecture cible (Java/Spark, Datalake). 
Le module FDC est un des plus petits de la partie Informatica, il est donc le premier à effectuer la transformation en tant que prise d'expérience.

Aussi la compagnie ayant une branche à Bangalore, Inde, toutes les communications sont majoritairement en anglais. 

## Définitions & explications

#### Situation

Une situation correspond à un flux de données en entrée reçu par une certaine source. Elle est différente de la source, elle représente une arrivée de donnée. Le cours des monnaies par exemple correspond à la sourde 902 et une situation est créée à chaque entrée de la donnée.

#### Frequency

La frequency correspond à la fréquence de réception d'un flux de données. Cela peut prendre la valeur : DAILY, MONTHLY, YEARLY, ... Le cours des monnaies par exemple est reçu en DAILY.

#### Treatment

Un treatment correspond à un workflow Informatica (l'équivalant d'un job Spark). On l'identifie par son ID_TREATMENT.

#### idf_trt_sit

Lorsqu'on reçoit des données en entrée, on créé une situation. Le <u>[situationId](#situation)</u> correspond donc à telle donnée reçue à telle date de telle source. Par la suite on effectue des traitements sur ces données (data quality par exemple) puis on les réinsère avec un idf_trt_sit. On peut donc retrouver les données après avoir subit tel traitement avec l'idf_trt_sit.

## Septembre/Octobre

#### 1 - Ce que j'ai fait :
- intégré l'équipe, participé aux meetings agiles, daylies
- participé avec Arun (nouvel arrivant en tant que business analyst) aux présentations explicatives du système legacy
- beaucoup de membres de l'équipe travaillant sur le legacy partent en ce moment, beaucoup de présentations de transfert de connaissances sont organisées

- reçu, fini, testé mon premier ticket : résoudre les quelques dependabots issues sur un projet annexe (Referentials) qui sert à récupérer des référentiels privés (depuis l'API de Mars) pour les poser sur le lake afin d'être utilisé par FDC
- terminé le développement de mon deuxième ticket : créer un  profil local sur Referentials afin de faciliter le développement sur ce projet
- corrigé un bug du projet sur la route, les pipelines CI/CD ne sont pas encore implémentées, je me suis rendu compte du bug en testant à la main
- documenté mon travail sur Jira

#### 2 - Ce que j'ai appris :

- déployer l'application via Jenkins
- tester l'application (à la main pour l'instant) via le scheduler Mercury
- comprendre la base de Spark
- profiler l'application avec Spring

#### 3 - Ce que j'ai ressenti (problèmes rencontrés et réussites)

- la qualité de code est très poussé sur le passage au système cible
- un problème majeur actuellement est la documentation en général, étant donné le départ de beaucoup de membres du legacy, il est urgent de documenter un maximum de connaissances à la fois pour les futurs remplaçants et pour le développement du système cible
- n'ayant jamais travaillé sur une architecture datalake, je ne comprends pas totalement la partie infrastructure ainsi que la stack liée à celle-ci (Oozie, Yarn, Hadoop, Hive, hdfs, ...)

#### 4 - Ce qui est prévu pour la semaine prochaine

- documenter, tester et intégrer mon développement sur Referentials
- commencer mon 3ème ticket : documenter mon arrivée pour les futurs arrivants

## Lundi 13/11/2023 -> Vendredi  17/11/2023

#### 1 - Ce que j'ai fait :

- terminé mes quelques développement sur BBC_Referentials 
	- ce projet est un premier jet afin permettre une transmission des référentiels privés sur le lake
	- les référentiels sont "simplement des jeux de données" sur lesquels se basent des opérations
	- il y a deux catégories de référentiels : privés et globaux
		- globaux = les données doivent être les mêmes pour toutes les opérations sur la liquidité
		- privés = les données concernent une/quelques opérations en particulier

- analysé la possibilité d'utilisation (+ charge de travail) de l'API Basyliq pour transmettre les référentiels globaux
	- fonctionnellement parlant, l'API à déjà été imaginée (<u>entre autres</u>) comme transmetteur de référentiel, cependant cette utilisation a été délaissée sur le temps
	- d'un point de vue architectural, il faudrait avoir un moyen centralisé de récupérer ces référentiels globaux, cela permettrait à toutes les équipes (notamment l'équipe Restit qui s'occupe de peupler la base d'Illiqo avec les données reçues de Basyliq) d'éviter de créer des solutions concurrentes répondants au même problème
	- l'API est actuellement basée sur un jeu de tables Oracle qui définit une liste des référentiels, on récupère pour chaque référentiel son <u>[situationId](#situation)</u> à partir de son <u>inventoryDate</u> + <u>[frequency](#frequency)</u>
	- depuis ce <u>[situationId](#situation)</u> on peut trouver l'<u>[IDF_TRT_SIT](#idf_trt_sit)</u> qui nous sert à retrouver le bonnes données du référentiel.

- documenté tout ce que j'ai compris du système existant et tout ce que j'ai fait (principalement préparé des requêtes SQL à exposer sur l'API) sur Jira

#### 2 - Ce que j'ai appris :

- comprendre mieux l'architecture datalake et son histoire, ainsi que le rôle des différentes applications dans écosystème (yarn = orchestrateur, scaling horizontal, hive, etc)
- comprendre les concepts de base utilisés sur la liquidité : idf_trt_sit, situation, etc
- comprendre petit à petit le modèle de données
- utiliser le système de user/schema d'Oracle

#### 3 - Ce que j'ai ressenti (problèmes rencontrés et réussites)

- difficultés à comprendre le modèle de données actuel, l'utilisation concrète des tables et des données
- problèmes d'accès sur les différents outils Oracle homologation, API Basyliq, etc
- difficultés à créer des requêtes sur un modèle de données et des process que je ne comprend pas entièrement

#### 4 - Ce qui est prévu pour la semaine prochaine

- Discuter du problème de transmission des référentiels avec Jordan (à l'origine des spécifications sur ce sujet) qui était en congés cette semaine.
- potentiellement commencer un jet d'implémentation sur cette API pour mieux visualiser la faisabilité



## Lundi 27/11/2023 -> Vendredi  1/12/2023

#### 1 - Ce que j'ai fait :

- continué l'analyse de la possibilité d'utilisation de l'API Basyliq comme moyen de transmettre les référentiels

- créé une simple implémentation schématique (en omettant les détails techniques en dessous) pour présenter notre idée à l'équipe en charge de l'API afin d'avoir les droits Git pour le futur développement

- l'idée de cette API pour transmettre des référentiels n'est pas nouvelle, quelques documentations spécifient déjà leur implémentation et quelques endpoints sont déjà faits. Cependant, beaucoup de ces spécifications fonctionnelles ne sont plus à jour et surtout incomplètes.

- fonctionnellement parlant, je ne suis pas encore suffisamment autonome pour définir les besoins et les données spécifiques à exposer sur les endpoints. J'ai donc simplement exposé les tables des référentiels à une <u>date</u> et <u>fréquence</u> donnée.

- dans l'attente d'avoir des spécifications fonctionnelles plus claires, j'ai commencé à travailler sur le transfert d'une lecture Spark vers un appel API pour récupérer les référentiels sur le <u>Fond De Carte</u>

- un des points clef du Fond De Carte, est la qualité du code et notamment des concepts comme:
	- Domain Driven Development = séparation de la couche métier et de l'infrastructure, l'application de cette idée  et du Repository Pattern me permet de ne modifier que la partie infra sans faire d'erreurs dans le métier
	- Behavior Driven Development = conserver une documentation vivante grâce aux tests automatiser
	- potentiellement à termes Test Driven Development


- participé à des meetings expliquant le coté technique, fonctionnel et historique sur le fonctionnement du legacy. Le système legacy (Oracle Exadata/Informatica) fonctionne presque entièrement en tables et certains choix sont historiques/deprecated, il est donc assez difficile d'en retirer les informations sans documentation externe.

#### 2 - Ce que j'ai appris :

- visualiser le fonctionnement de base du système legacy, comprendre les choix historiques
- comprendre et utiliser les principes de qualité de code dans l'infra du Fond De Carte
- comprendre les besoins concurrents dans l'enjambement du legacy au lake 
- comprendre le système d'exécution des workflows Informatica

#### 3 - Ce que j'ai ressenti (problèmes rencontrés et réussites)

- difficultés à planifier du transfert de connaissances, notamment les connaissances fonctionnelles et historiques

- difficultés (sur le Fond De Carte) à trouver une solution propre à la double configuration `application.yaml` et `job.json` nécessaire au scheduler interne Mercury utilisé pour lancer les jobs Spark

- difficultés à créer des requêtes sur un modèle de données et des process que je ne comprend pas entièrement

#### 4 - Ce qui est prévu pour la semaine prochaine

- après ces meetings, Jordan devrait avoir terminé des documentations fonctionnelles sur le transfert des référentiels et je pourrais donc développer en conséquence sur l'API

- par la suite, en attendant les validations diverses, je pourrais adapter le Fond De Carte à ces changements 