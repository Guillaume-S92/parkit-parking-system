# Park'it - Tests et évolution d'une application Java

Projet réalisé dans le cadre de ma formation de développeur Java.

Ce projet consiste à reprendre une application existante de gestion de parking, appelée **Park'it**, afin de corriger des bugs, ajouter de nouvelles fonctionnalités et renforcer la qualité du code grâce aux tests unitaires et aux tests d'intégration.

Repository de base fourni par OpenClassrooms :  
https://github.com/OpenClassrooms-Student-Center/parkingsystem

Repository final du projet :  
https://github.com/Guillaume-S92/SIMON_Guillaume_tester_java

---

## Contexte du projet

Park'it est une application de paiement de parking automatisé développée pour la société fictive **Move'it**, spécialisée dans les solutions de mobilité urbaine.

L'application est encore en phase bêta. Elle permet actuellement de simuler les actions principales d'un utilisateur dans un parking :

- entrer dans le parking ;
- choisir un type de véhicule, voiture ou moto ;
- saisir une plaque d'immatriculation ;
- obtenir une place disponible ;
- sortir du parking ;
- calculer le prix du stationnement selon la durée et le type de véhicule.

L'application ne possède pas encore d'interface graphique. Elle fonctionne pour le moment via un terminal de commande.

---

## Objectifs du projet

L'objectif principal était de reprendre une base de code existante, d'en corriger les défauts et d'améliorer sa fiabilité en ajoutant des tests.

Les objectifs demandés étaient les suivants :

- corriger les bugs présents dans l'application ;
- ajouter une fonctionnalité de stationnement gratuit pour les 30 premières minutes ;
- ajouter une réduction de 5 % pour les utilisateurs récurrents ;
- faire passer les tests unitaires existants ;
- compléter les tests d'intégration indiqués par des commentaires `TODO` ;
- atteindre une couverture de code minimale de 70 % ;
- générer les rapports de tests avec JaCoCo et Surefire.

---

## Fonctionnalités réalisées

### Stationnement gratuit les 30 premières minutes

Une nouvelle règle métier a été ajoutée :  
si un utilisateur reste garé moins de 30 minutes, le stationnement est gratuit.

Cette règle permet de répondre au besoin produit demandé pour améliorer l'expérience utilisateur.

---

### Réduction pour les utilisateurs récurrents

Une réduction de 5 % a été ajoutée pour les utilisateurs récurrents.

Un utilisateur est considéré comme récurrent lorsqu'il a déjà utilisé le parking auparavant avec le même véhicule.

Cette réduction est appliquée lors du calcul du prix final du stationnement.

---

### Correction des bugs existants

Le code existant contenait plusieurs comportements incorrects empêchant certains tests de passer.

Le projet a donc été corrigé afin de fiabiliser les fonctionnalités principales :

- entrée d'un véhicule dans le parking ;
- sortie d'un véhicule ;
- attribution d'une place disponible ;
- calcul du prix ;
- gestion des véhicules déjà connus ;
- gestion des places disponibles.

---

### Ajout et correction des tests

Le projet met l'accent sur la qualité logicielle et la validation du comportement de l'application.

Les tests ont été complétés afin de vérifier :

- les règles de calcul du prix ;
- la gratuité sous 30 minutes ;
- la réduction de 5 % pour les utilisateurs récurrents ;
- le bon fonctionnement du service de parking ;
- les scénarios d'entrée et de sortie d'un véhicule ;
- les cas d'intégration entre les différentes couches de l'application.

---

## Technologies utilisées

- Java
- Maven
- JUnit
- Mockito
- JaCoCo
- Maven Surefire Plugin
- SpotBugs
- JDBC
- MySQL

---

## Structure générale du projet

Le projet est organisé autour de plusieurs couches :

```text
src
├── main
│   └── java
│       └── com.parkit.parkingsystem
│           ├── config
│           ├── constants
│           ├── dao
│           ├── model
│           ├── service
│           └── util
│
└── test
    └── java
        └── com.parkit.parkingsystem
            ├── dao
            ├── service
            └── integration
```

### Principaux dossiers

- `model` : contient les objets métier comme les tickets, véhicules et types de véhicules.
- `dao` : gère l'accès aux données.
- `service` : contient la logique métier de l'application.
- `util` : contient les classes utilitaires.
- `test` : contient les tests unitaires et les tests d'intégration.

---

## Prérequis

Avant de lancer le projet, il faut installer :

- Java 8 ou une version compatible avec le projet ;
- Maven ;
- MySQL ;
- Git.

---

## Installation du projet

Cloner le repository :

```bash
git clone https://github.com/Guillaume-S92/SIMON_Guillaume_tester_java.git
```

Se placer dans le dossier du projet :

```bash
cd SIMON_Guillaume_tester_java
```

Installer les dépendances Maven :

```bash
mvn clean install
```

---

## Configuration de la base de données

Le projet utilise une base de données MySQL.

Il faut créer la base de données attendue par l'application, puis exécuter les scripts SQL fournis dans le projet afin de créer les tables nécessaires et d'insérer les données de départ.

Les informations de connexion à la base sont configurées dans le projet, notamment pour permettre aux tests d'accéder aux données nécessaires.

---

## Lancement de l'application

Pour lancer l'application :

```bash
mvn exec:java
```

L'application démarre ensuite dans le terminal et propose un menu permettant de :

- faire entrer un véhicule ;
- faire sortir un véhicule ;
- quitter l'application.

---

## Lancement des tests

Pour exécuter les tests du projet :

```bash
mvn test
```

Cette commande lance les tests unitaires et les tests d'intégration configurés avec Maven Surefire.

---

## Génération du rapport JaCoCo

Pour générer le rapport de couverture de code :

```bash
mvn clean test
```

Le rapport JaCoCo est ensuite disponible dans le dossier :

```text
target/site/jacoco/index.html
```

Ce rapport permet de vérifier la couverture de code du projet.

L'objectif demandé était d'atteindre au minimum **70 % de couverture** sur le code travaillé.

---

## Rapport Surefire

Le rapport Surefire est généré automatiquement lors de l'exécution des tests.

Il est disponible dans le dossier :

```text
target/surefire-reports
```

Ce rapport permet de consulter le résultat détaillé des tests exécutés.

---

## Qualité du code

Le projet s'inscrit dans une démarche de qualité logicielle.

Les points importants travaillés sont :

- correction du code existant ;
- ajout de tests unitaires ;
- ajout de tests d'intégration ;
- validation des règles métier ;
- amélioration de la couverture de tests ;
- vérification des rapports JaCoCo et Surefire ;
- maintien d'un code plus fiable et plus maintenable.

Le kit technique d'onboarding du projet rappelle notamment l'importance de la qualité technique continue, des tests, de JaCoCo, de Surefire et de SpotBugs.

---

## Ce que j'ai appris avec ce projet

Ce projet m'a permis de travailler sur une application Java existante et de mieux comprendre l'importance des tests dans un projet professionnel.

J'ai notamment appris à :

- analyser une base de code déjà existante ;
- identifier et corriger des bugs ;
- ajouter de nouvelles règles métier ;
- écrire des tests unitaires avec JUnit et Mockito ;
- compléter des tests d'intégration ;
- interpréter un rapport de couverture JaCoCo ;
- vérifier les résultats de tests avec Surefire ;
- améliorer progressivement la qualité d'une application.

---

## Améliorations possibles

Plusieurs améliorations pourraient être envisagées pour faire évoluer le projet :

- ajouter une interface graphique web ;
- intégrer un vrai système de paiement ;
- améliorer la gestion des utilisateurs récurrents ;
- renforcer la gestion des erreurs ;
- externaliser davantage la configuration ;
- ajouter plus de scénarios de tests d'intégration ;
- mettre en place une intégration continue avec GitHub Actions.

---

## Auteur

Projet réalisé par **Guillaume Simon** dans le cadre d'une formation de développeur Java.
