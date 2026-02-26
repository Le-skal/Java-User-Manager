<div align="center">

# User Management System
### *Application de Gestion d'Utilisateurs avec Interface Graphique*

<p><em>Administrez vos profils utilisateurs via une interface JavaFX intuitive, connectée à MySQL.</em></p>

![Status](https://img.shields.io/badge/status-functional-success?style=flat)
![Version](https://img.shields.io/badge/version-1.0-blue?style=flat)
![License](https://img.shields.io/badge/license-MIT-green?style=flat)

<p><em>Built with:</em></p>

![Java](https://img.shields.io/badge/Java-20-ED8B00?style=flat&logo=openjdk&logoColor=white)
![JavaFX](https://img.shields.io/badge/JavaFX-20-007396?style=flat&logo=java&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat&logo=mysql&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.x-C71A36?style=flat&logo=apachemaven&logoColor=white)
![JDBC](https://img.shields.io/badge/JDBC-8.0.33-orange?style=flat)
![FXML](https://img.shields.io/badge/FXML-layouts-blueviolet?style=flat)
![CSS](https://img.shields.io/badge/CSS-custom--styles-1572B6?style=flat&logo=css3&logoColor=white)
![MVC](https://img.shields.io/badge/Architecture-MVC-lightgrey?style=flat)

</div>

---

## Table des Matières

- [Objectif du Projet](#objectif-du-projet)
- [Fonctionnalités](#fonctionnalités)
- [Stack Technique](#stack-technique)
- [Architecture](#architecture)
- [Installation](#installation)
- [Structure du Code](#structure-du-code)

---

## Objectif du Projet

Développer une application de bureau complète permettant d'**administrer des profils utilisateurs** stockés dans une base de données MySQL, via une interface graphique moderne construite avec JavaFX.

Le projet illustre une architecture **MVC simplifiée** avec séparation claire entre logique métier, accès aux données et interface utilisateur.

---

## Fonctionnalités

### Interface Graphique Dynamique
Navigation entre plusieurs vues grâce à des layouts **FXML personnalisés** et une gestion fine des styles CSS (changement de thème, polices à la volée).

### Opérations CRUD Complètes
Création, lecture, mise à jour et suppression de profils utilisateurs directement en base de données, sans rechargement de l'application.

### Recherche Filtrée
Recherche dynamique par **nom ou email** avec mise à jour en temps réel de la liste affichée.

### Exportation CSV
Génération d'un fichier `utilisateurs.csv` dans le dossier des ressources pour le partage ou l'analyse des données.

### Personnalisation Visuelle
Système de gestion de polices permettant de basculer entre les styles **VT323** et **FFF Forward**.

---

## Stack Technique

| Catégorie | Technologie |
|---|---|
| Langage | Java 20 |
| Framework UI | JavaFX 20 |
| Base de données | MySQL (via JDBC 8.0.33) |
| Build tool | Maven |
| Architecture | MVC simplifié |

---

## Architecture

```
┌────────────────────────────────────────────────┐
│              VIEW (JavaFX + FXML)              │
│                                                │
│  ┌──────────────┐  ┌──────────────┐            │
│  │  Liste View  │  │  Ajout View  │   ...      │
│  └──────────────┘  └──────────────┘            │
└──────────────────────┬─────────────────────────┘
                       │ Events / Actions
                       ▼
┌────────────────────────────────────────────────┐
│            CONTROLLER (App.java)               │
│      Gestion des scènes & initialisation       │
└──────────────────────┬─────────────────────────┘
                       │ Appels métier
                       ▼
┌────────────────────────────────────────────────┐
│         MODEL / SERVICE                        │
│                                                │
│  ┌──────────────────────────┐                  │
│  │  GestionUtilisateur.java │  Logique métier  │
│  │  Requêtes SQL, CSV export│                  │
│  └──────────────────────────┘                  │
│                                                │
│  ┌──────────────────┐  ┌──────────────────┐    │
│  │  Utilisateur.java│  │  Connexion.java  │    │
│  │  Modèle objet    │  │  Pool JDBC       │    │
│  └──────────────────┘  └──────────────────┘    │
└──────────────────────┬─────────────────────────┘
                       │ JDBC
                       ▼
┌────────────────────────────────────────────────┐
│              MySQL Database                    │
│  Table : utilisateurs                          │
│  - id (PK, Auto-increment)                     │
│  - nom (VARCHAR)                               │
│  - email (VARCHAR)                             │
└────────────────────────────────────────────────┘
```

---

## Installation

### Prérequis
- Java 20+
- Maven 3.x
- Serveur MySQL actif

### 1. Configuration de la base de données

Créez la table `utilisateurs` sur votre serveur MySQL :

```sql
CREATE TABLE utilisateurs (
  id    INT PRIMARY KEY AUTO_INCREMENT,
  nom   VARCHAR(255),
  email VARCHAR(255)
);
```

### 2. Compilation

```bash
mvn clean install
```

### 3. Lancement

```bash
mvn javafx:run
```

---

## Structure du Code

```
src/
├── main/
│   ├── java/
│   │   ├── App.java                  # Point d'entrée, gestion des scènes
│   │   ├── GestionUtilisateur.java   # Logique métier + SQL + CSV export
│   │   ├── Utilisateur.java          # Modèle objet utilisateur
│   │   └── Connexion.java            # Connexion MySQL via JDBC
│   └── resources/
│       ├── layouts/
│       │   ├── liste.fxml            # Vue liste des utilisateurs
│       │   ├── ajout.fxml            # Vue formulaire d'ajout
│       │   └── update.fxml           # Vue formulaire de modification
│       ├── styles/
│       │   └── main.css              # Styles globaux
│       └── utilisateurs.csv          # Export généré automatiquement
└── pom.xml
```

---

<div align="center">
<em>Projet académique — Java 20 + JavaFX + MySQL</em>
</div>
