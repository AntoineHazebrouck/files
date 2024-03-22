# Rapport d'alternance final

## Ingénieur Logiciel chez Société Générale

### Antoine HAZEBROUCK, BUT3A, Groupe M

### Maître d'apprentissage : Pascal Rat, pascal.rat@socgen.com

### Tuteur pédagogique : Antoine Nongaillard, antoine.nongaillard@univ-lille.fr

### Début du contrat : 25/09/2023
### Fin du contrat : 31/08/2024

# Remerciements (1 page max)

Je tiens tout d'abord à remercier l'équipe pédagogique de l'IUT de Villeneuve d'Ascq, et particulièrement Mr.Nongaillard pour l'accompagnement délivré au long de la formation et de mon apprentissage.

Je pense aussi à Thibaud Levasseur et Tigran Slama, à l'origine de mes débuts chez Société Générale.

Je souhaiterais remercier particulièrement Pascal Rat et Jordan Martin qui m'ont activement suivi lors de mon année dans l'entreprise. Ils m'ont épaulé au cours de mon apprentissage, ils m'ont transmis leur expertise sur de nombreux sujets et apportés leur expérience au sein de l'entreprise. Merci aussi à toute l'équipe BSDQM et Illiqo pour l'accueil et la collaboration dont ils ont fait preuve.

Cette période d'alternance m'a permis d'affiner mon projet professionnel et donné la visibilité nécessaire à ma continuation en suite du BUT. Je suis donc reconnaissant envers tous les acteurs qui m'ont accompagné lors de mon cursus, et qui vont potentiellement m'accompagner par la suite.

# Sommaire

- Abstract
- Introduction
	- Contexte et objectif du rapport
- Présentation de l'entreprise
	- Historique et secteur d'activité
	- Structure organisationnelle
- Introduction à l'écosystème Hadoop
- Description des missions et des tâches réalisées
	- Mission 1 : ...
		- Objectifs de la mission
		- Taches et responsabilités
	- Mission 2 : ...
		- Objectifs de la mission
		- Taches et responsabilités
- Analyse des problématiques rencontrées et des solutions proposées
	- Problématique 1 : ...
		- Description de la problématique
		- Solutions proposées
	- Problématique 2 : ...
		- Description de la problématique
		- Solutions proposées
- Réflexion personnelle sur l'expérience vécue
	- Acquisitions de compétences et développement personnel
	- Réussites et échecs
	- La formation par rapport au poste
	- Enseignements tirés et perspectives futures
- Conclusion
- Annexes

# Abstract

TODO

# Introduction

## Contexte de l'alternance

Je suis arrivé chez Société Générale lors de mon stage de BUT2 en tant que développeur web, dans une équipe nommée Illiqo. Je travaillais alors dans le domaine de la liquidité sur une interface utilisateur restituant les données financières du groupe. L'origine de cette application, ainsi que du service liquidité émerge originellement de la crise de 2008. Nous verrons plus de détails sur le projet par la suite.

Actuellement, je travaille dans une autre équipe de la chaine de liquidité nommée Basyliq, juste en amont d'Illiqo. J'y occupe un poste plus orienté sur du traitement, de l'enrichissement et de la qualité des données. Ce sont ces "mêmes" données qui sont affichées dans l'application d'Illiqo.

## Contexte et objectif du rapport


Dans ce rapport, nous introduirons rapidement l'entreprise et de ses détails notables, notamment au niveau de son envergure et des contraintes majeures que cela engendre d'un point de vue technique comme organisationnel. On pourra également relier ces problèmes à mon expérience dans l'entreprise.

Nous expliquerons globalement le contexte de mon alternance au sein du service liquidité chez Société Générale. Nous verrons l'origine historique du projet, ses problématiques et son évolution, aussi nous aurons l'occasion de considérer l'organisation structurelle du projet et du flux des données.

Ces enjeux d'entreprise seront aussi l'occasion d'introduire une des solutions techniques qui permettent d'y palier. L'écosystème Hadoop s'est démocratisé en entreprise car il répond à des problèmes de volumétrie, de flexibilité et d'organisation. Cette technologie constitue le cœur de mon travail en alternance, et n'est que très peu abordée dans la formation. Il est donc intéressant et important d'apprendre les bases de cet écosystème pour comprendre la suite du rapport.

On parlera plus concrètement par la suite de mes missions et de mes tâches réalisées chez Basyliq. Depuis 2008, le début projet, beaucoup de changements opérationnels, technologiques et organisationnels ont pris forme. Nous allons explorer ces changements historiques et notamment le contexte de transition du système legacy vers l'écosystème Hadoop, moins couteux et plus flexible.

Je ferais par la suite un bilan personnel sur ces tâches, dans lequel je parlerais de mes réussites et mes difficultés. Je mettrais aussi en valeur les avantages de la formation par rapport au poste.

# Présentation de l'entreprise

## Historique et secteur d'activité

Société Générale est une multinationale financière d'origine française. Elle opère principalement en tant que banque de détail, banque d'investissement et gestionnaire d'actifs. Le groupe agit aussi comme assureur et propose des services aux entreprises comme de la gestion de la dette, des solutions de financement ou du conseil. Société Générale est en autre l'entité principale du groupe SG (SocGen à l'international), qui contient notamment :
- Crédit du Nord
- ALD Automotive
- Boursorama
- Rosbank
- ...

La banque a été créée en 1864 à Paris par des banquiers ayants pour objectif de financer le développement industriel Français. Au fil des décennies, l'entreprise s'est diversifiée dans ses services, et s'est aussi étendue à l'international.

Société Générale opère à l'international, ce qui amène encore un grand nombre de défis à relever mais aussi de possibilités. Le service liquidité et notamment Basyliq, mon équipe, est situé à Paris La Défense, en collaboration avec un site localisé à Bangalore (Inde). Toute la communication écrite est en anglais, sauf exception.


Afin de nous concentrer sur le domaine d'activité que j'exerce en entreprise. Nous allons par la suite introduire le concept de liquidité, ainsi que son histoire

## Structure organisationnelle

D'un point de vue global, l'organisation de l'entreprise est assez hiérarchique. A titre d'exemple, il y a une dizaine de "N plus ..." entre moi et M.Slawomir Krupa, directeur général du groupe. Cette hiérarchie est cependant nécessaire considérant la variété des services et projets menés par le groupe.

Le groupe est divisé en entités, comme SG CIB (Société Générale Corporate & Investment Banking) ou SG RB (Société Générale). Ces entités sont définies par leur domaines d'activités ou leur localisations.
On peut aussi noter la délimitation par départements. Ces départements prennent typiquement la forme suivante: ABC/DEF/GEH/IJK, à titre d'exemple, je suis dans le département TODO/TSR/DEF (/Treasury and Structural Risks/ TODO) et notre projet est chapeauté par /DFIN/ (TODO). 

Nous verrons plus de détails sur l'organisation en nous concentrant sur le projet.

# Présenter les missions et le projet

## Présenter l'écosystème Hadoop

### Son histoire

Les entreprises, y compris SG, ont toujours un besoin de traiter, d'utiliser et d'analyser les/leurs données. Ce utilisations émergent peuvent émerger d'un besoin concurrentiel: limiter les coûts et améliorer le rendement, ou de besoins légaux. Les deux cas nous concernent dans le domaine de la liquidité. 

Historiquement, le moyen de palier à ces demandes est de centraliser le stockage et le traitement de ces données dans une grande base relationnelle. Au fur et à mesure que les volumes des données grimpent, il faut améliorer la machine hôte: on parle de scaling vertical.
Les entreprises faisaient généralement appel à des solutions spécialisées externes, qui permettent des répondre au besoin. La solution choisie par Société Générale est Oracle Exadata, c'est une solution deux en un qui gère à la fois la partie logicielle et matérielle.

Cependant, cette approche à la manipulation des données volumineuses apporte beaucoup de contraintes.

Premièrement, ces systèmes tout en uns sont très couteux. Il nécessitent l'intervention d'acteurs tiers comme Oracle non open-sources et qui laissent difficilement de la place à l'évolution.
Aussi, la contrainte la plus évidente pour ces systèmes est la volumétrie. A titre d'exemple, PostgreSQL gère jusque 32To, on imagine donc que même les meilleurs systèmes relationnels verticaux ne multiplieront pas la charge indéfiniment comme le feraient des solutions distribuées.
Un autre désavantage de ces systèmes monolithiques est le manque de flexibilité, notamment par rapport à Hadoop. La ou certains systèmes relationnels sont capables de manipuler des données destructurées, structurées et semi-structurées, Hadoop peut explicitement stocker tout ces types de données sans contraintes et en volumétries massives. On combine donc les avantages des "meilleures" bases relationnelles et la scalabilité des non-relationnelles.
De plus, ces solutions rendent la maintenance et l'évolution assez difficiles. D'un coté l'architecture par tables traditionnelle donne beaucoup d'avantages, et not
- difficiles à maintenir
	- tout est tables
	- progiciel Informatica
	- trouver du staff pour maintenir
	- on perd le pourquoi on a fait quoi dans les traitements, les changements ne sont pas en cascade
- manque de flexibilité par rapport à Hadoop

- l'histoire
- stockage
- traitement

## Le contexte

### La liquidité et son histoire

- apparition de la liquidité
	- coté juridique 
	- SVB, 2008, Lehman Brothers

- les départements
- les équipes



- architecture micro services
- les indiens/l'international 
- intro aux périmètres

### L'historique du projet

### Pourquoi la migration ?

## L'architecture et l'organisation actuelle du projet


- architecture micro services
- les indiens/l'international 
- intro aux périmètres

- agile, meetings ...


### Illiqo


### Basyliq, ce que je fais

- l'international
- le fonctionnement de l'entreprise
	- hiérarchie
	- agile
	- ambiance de travail

- international
- les activités
- les départements
	- dfin
	- info
- les équipes


## Un exemple de but du projet

- risque de liquidité
- mon travail
- est-ce que j'ai répondu aux attentes

# Conclusion

- reprendre les objectifs de l'introduction, ont ils étés atteints, pourquoi
- ce que j'ai appris
- ce que j'ai apporté
- dans la formation et dans l'entreprise
- professionnellement et personnellement
- représenter mon projet d'avenir 


- préciser la suite professionnelle et scolaire

# Annexes