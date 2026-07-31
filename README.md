# GTEL SPACE — Système de Gestion de la filiere GTEL
 
> **GTEL SPACE** est un site on web complète pour le GTEL, representant une vitrine numérique centralisée pour communiquer sur ses activités, sur la vie du département; pour transmettre aux promotions suivantes la documentation académique accumulée au fil des années (anciens sujets, supports de parrainage).

---

## Table des matières

- [Aperçu du projet](#-aperçu-du-projet)
- [Fonctionnalités](#-fonctionnalités)
- [Architecture du projet](#-architecture-du-projet)
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Lancement](#-lancement)
- [Structure des modules](#-structure-des-modules)
- [Base de données](#-base-de-données)
- [Équipe](#-équipe)
- [Encadrement](#-encadrement)
- [Licence](#-licence)

---

##  Aperçu du projet

GTEL SPACE est né des besoins :
    • Offrir un point d'information unique et à jour sur l'actualité du département de Télécommunications et de la filière GTEL.
    • Permettre au Président et à la Cellule Communication de publier facilement des annonces, actualités et photos, sans compétence technique particulière.
    • Présenter la filière de façon structurée à travers le détail de chaque Unité d'Enseignement (UE), avec autant que possible une présentation de l'enseignant responsable.
    • Constituer une bibliothèque de parrainage centralisant les anciens sujets et documents utiles, classés du niveau L3 au niveau L5, librement téléchargeables.
    • Valoriser l'histoire et l'identité du club à travers une section dédiée à ses origines.

**Contexte académique :**
- Établissement : École Nationale Supérieure Polytechnique (ENSP) de Yaoundé
- Filière : Génie des Télécommunications (GTEL)
- Année académique : 2025–2026

---

##  Fonctionnalités

| # | Module | Description | Statut |
|---|--------|-------------|--------|
| 1 | **Authentification & Rôles** | Connexion sécurisée, gestion des utilisateurs et permissions par rôle (president, visiteur, administrateur, cell_com) | Prévu |
| 2 | **Galeries et photos** | publication et gestion des photos |  Prévu |
| 3 | **Filiere et UEs** | Catalogue des produits et plats proposés, avec catégories, prix et disponibilité |  Prévu |
| 4 | **Bibliotheque de parrainnage** | Prise de commande, suivi en temps réel, génération de factures et reçus |  Prévu |
| 5 | **Origine du club Gtel** | Suivi des activites du club Gtel et de ses Origines | Prévu |
| 6 | **Administration /Back office** | Gestion du site | Prévu |
| 7 | **Annonces et Actualites** | Publication et gestion des annonces et des aatualites| Prévu |
---

## Architecture du projet

```
GTEL_SPACE/
│
├── GTEL_SPACE_1/
│   ├── config/              # Configuration principale Django
│   │   ├── settings.py               # Paramètres globaux
│   │   ├── urls.py                   # Routage principal
│   │   ├── wsgi.py                   # Interface WSGI
│   │   └── asgi.py                   # Interface ASGI
│   │
│   ├── authentification/             # Module 1 — Auth & Rôles
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   ├── admin.py
│   │   └── templates/authentification/
│   │
│   ├── Galeries/                     # Module 2 — Recettes
│   ├── UEs/                     # Module 3 — Produits
│   ├── Commandes/                    # Module 4 — Commandes & Facturation
│   ├── Parrainage/                   # Module 5 — Inventaire & Alertes Stock
│   ├── Origine/                           # Module 6 — Ressources Humaines & Paie
│   ├── Administration/                    # Module 7 — Dashboard & Rapports
│   ├── Base_SPACE.sql           # Base de données du restaurant
│   ├── static/                       # Fichiers statiques (CSS, JS, images), prevu
│   ├── templates/                    # Templates HTML globaux 
│   └── manage.py
│
├── env/                              # Environnement virtuel (non versionné)
├── .env.example                      # Exemple de configuration
├── requirements.txt                  # Dépendances Python
└── README.md
```

---

##  Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- **Python** 3.11 ou supérieur
- **pip** (gestionnaire de paquets Python)
- **MySQL Server** 8.0 ou supérieur
- **Git**

Vérifier les versions en utilisant les commandes :

```bash
python3 --version
mysql --version
git --version
```

---

## Installation

### 1. Cloner le dépôt

```bash
git clone https://github.com/Vmessah-Ida/GTEL_SPACE.git
cd GTEL_SPACE
```

### 2. Créer et activer un environnement virtuel

```bash
# Créer l'environnement virtuel
python3 -m venv gtel_env

# Activer (Linux / macOS)
source gtel_env/bin/activate

# Activer (Windows)
gtel_env\Scripts\activate
```

### 3. Installer les dépendances

```bash
pip install -r requirements.txt
```

### 4. Installer les dépendances individuellement (si nécessaire)

```bash
pip install django
pip install mysqlclient
pip install python-decouple
pip install Pillow
```

---

##  Configuration

### 1. Créer le fichier `.env`

Copiez le fichier d'exemple et remplissez vos valeurs :

```bash
cp .env.example .env
```

### 2. Contenu du fichier `.env`

```env
# Django
SECRET_KEY=votre_clé_secrète_django_ici
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1

# Base de données MySQL
DB_NAME= Base_GTEL
DB_USER=root
DB_PASSWORD=votre_mot_de_passe
DB_HOST=localhost
DB_PORT=3306
```

### 3. Créer la base de données MySQL

```sql
-- Se connecter à MySQL
mysql -u root -p

-- Créer la base de données
CREATE DATABASE Base_GTEL CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Vérifier
SHOW DATABASES;
EXIT;
```

---

##  Lancement

### 1. Appliquer les migrations

```bash
python3 manage.py makemigrations
python3 manage.py migrate
```

### 2. Créer un superutilisateur

```bash
python3 manage.py createsuperuser
```

### 3. Lancer le serveur de développement

```bash
python3 manage.py runserver
```

L'application est accessible à l'adresse : **http://127.0.0.1:8000/**  
L'interface d'administration : **http://127.0.0.1:8000/admin/**

---

##  Structure des modules

###  Module 1 — Authentification & Acceuil-Annonces

Point d'entrée sécurisé de toute l'application.

● Fil d'actualités du département et de la filière (articles courts, dates, images).
● Mise en avant des annonces importantes (événements, dates de forums, appels
à candidature, etc.) en tête de page.
● Formulaire de publication réservé aux contributeurs : titre, texte, image(s), date,
catégorie.
● Archives des actualités consultables par date ou par catégorie.

###  Module 2 — Galerie

● Albums organisés par événement ou par date.
● Upload multiple d'images par les contributeurs.
● Affichage type galerie avec vue agrandie (lightbox).

###  Module 3 — UEs

Catalogue complet des UEs et biographies des professeurs.

● Liste des UE de la filière, filtrable par niveau (L3, L4, L5) et par semestre.
● Fiche détaillée par UE : code, intitulé, volume horaire, crédits, semestre,
objectifs/contenu résumé.
● Présentation de l'enseignant responsable lorsque l'information est disponible :
nom, grade, éventuellement une courte biographie ou photo.
● Ce module nécessitera une collecte de données auprès de la scolarité ou du
département, l'information n'étant pas toujours centralisée.

###  Module 4 — Biblioheque de parrainnage 

● Espace de dépôt et de téléchargement de documents : anciens sujets
d'examens, TD, corrigés, supports de cours transmis par les promotions
précédentes.
● Classement par niveau (L3 / L4 / L5), puis par UE ou par matière.
● Upload réservé aux contributeurs ; téléchargement libre pour tout visiteur.
● Fonction de recherche par mot-clé (nom de matière, année, type de document).
● Point à valider : format des fichiers acceptés (PDF de préférence) et taille
maximale par fichier.

###  Module 5 — Origines

● Page dédiée à l'historique de création du club, ses fondateurs, ses temps forts.
● Présentation éventuelle des anciens bureaux / promotions marquantes.
● Contenu essentiellement rédactionnel, à fournir par le club.

###  Module 6 — Administration

● Interface de gestion des comptes (création de comptes Cellule Com, gestion des
rôles).
● Modération des contenus publiés par la Cellule Communication avant mise en
  ligne (optionnel, à valider).
● Statistiques simples de consultation (pages les plus vues, téléchargements).


---

##  Base de données

**SGBD :** MySQL 8.0  
**Encodage :** UTF-8 MB4 (support des caractères spéciaux et emojis)

```

### Commandes utiles

```bash
# Voir les migrations disponibles
python3 manage.py showmigrations

# Réinitialiser une migration spécifique
python3 manage.py migrate nom_app zero

# Sauvegarder la base de données
mysqldump -u root -p kmer_food_db > backup_$(date +%Y%m%d).sql
```



##  Équipe

| Nom | Matricule | Rôle |
|-----|-----------|------|


---

##  Encadrement

**Superviseur :** 
**Institution :** École Nationale Supérieure Polytechnique (ENSP) de Yaoundé  
**Département :** Génie des Télécommunications — Promotion 2028

---

##  Licence

Ce projet est développé dans un cadre académique à l'ENSP Yaoundé.  
Tous droits réservés © 2026 — Équipe KMER FOOD.

---
<p align="center">
  Fait à Yaoundé, Cameroun 
</p>
