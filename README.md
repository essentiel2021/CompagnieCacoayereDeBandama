# Compagnie Cacaoyère De Bandama (CCB) - Système d'Information & ERP Cacao

Bienvenue dans le dépôt du système d'information de la **Compagnie Cacaoyère De Bandama (CCB)**. Il s'agit d'une plateforme web complète de gestion des coopératives agricoles, de la traçabilité du cacao, du suivi de la durabilité et de la protection de l'enfance en Côte d'Ivoire.

---

## 🚀 Présentation & Modules Métier

Le système CCB centralise la gestion opérationnelle, logistique et sociale des coopératives cacaoyères à travers plusieurs modules interconnectés :

### 1. 🏭 Gestion des Coopératives & Infrastructures
- **Structure organisationnelle** : Coopératives, Sections, Magasins Centraux et Magasins de Section.
- **Gestion des rôles & accès** : Administrateurs, managers, délégués et agents de terrain.

### 2. 👨‍🌾 Producteurs & Ménages
- **Registre des producteurs** : Profils complets, photos, pièces d'identité, statuts de certification (Rainforest Alliance, Fairtrade, etc.).
- **Enquêtes ménages** : Sources d'énergie, d'eau potable, gestion des ordures, équipements scolaires et sanitaires.

### 3. 🗺️ Cartographie SIG & Agroforesterie
- **Cartographie des parcelles** : Import et visualisation de fichiers GPS / KML (`mappingparcelle.kml`).
- **Protection environnementale** : Détection de proximité des forêts classées et des zones tampons.
- **Agroforesterie** : Approvisionnement, distribution et suivi post-plantation des espèces d'arbres d'ombrage.
- **Suivi phytosanitaire** : Application de pesticides, suivi des maladies, ravageurs et insectes utiles.

### 4. 🚚 Logistique & Traçabilité Cacao
- **Achat & Collecte** : Suivi des pesées et livraisons des producteurs aux magasins.
- **Logistique & Expédition** : Gestion des scellés, connaissements, transporteurs, véhicules et remorques jusqu'à l'usine/port.

### 5. 🛡️ Système de Suivi du Travail des Enfants (SSRTE / CLMRS)
- **Monitoring & Remédiation** : Identification des enfants vulnérables et suivi des facteurs de risque.
- **Classification des travaux** : Distinction des travaux dangereux vs. travaux légers autorisés.
- **Actions sociales & Scolarisation** : Prise en charge des arrêts d'école et soutien communautaire.

### 6. 🎓 Formations & Inspections
- **Formations** : Planification des modules pour les producteurs et le staff (thèmes, sous-thèmes, feuilles d'émargement).
- **Inspections internes** : Questionnaires d'évaluation de la conformité aux normes de durabilité.

### 7. 💼 Module ERP & Ressources Humaines
- **Gestion du personnel** : Contrats, fiches de poste, dossiers administratifs.
- **Présences & Congés** : Suivi du temps de travail, quotas de congés, plannings d'équipes.
- **Gestion financière & Projets** : Tâches, devis, factures, dépenses et tickets de support.

---

## 🛠️ Stack Technique

- **Backend** : PHP 8.0+ / [Laravel 9.52](https://laravel.com/)
- **Base de Données** : MySQL
- **Frontend** : HTML5, Vanilla CSS, JavaScript, Blade, DataTables, Chart.js / Larapex Charts
- **Serveur Web Local** : XAMPP (Apache)

---

## 📁 Structure du Projet

```text
ccb/
├── core/                        # Application principale Laravel
│   ├── app/                     # Modèles, Contrôleurs, Middleware, Service Providers
│   ├── bootstrap/               # Fichiers d'initialisation de l'application
│   ├── config/                  # Configuration (base de données, auth, mail, etc.)
│   ├── database/                # Migrations, Seeders, Factories
│   ├── resources/               # Vues Blade, assets frontend
│   ├── routes/                  # Définitions des routes (web.php, api.php, etc.)
│   ├── storage/                 # Logs, fichiers générés, cache
│   ├── vendor/                  # Dépendances PHP (Composer)
│   ├── .env                     # Configuration d'environnement
│   ├── artisan                  # CLI Laravel
│   └── composer.json            # Gestionnaire de paquets PHP
├── assets/                      # Ressources statiques partagées (CSS, JS, images)
├── index.php                    # Fichier d'entrée principal (Redirige vers core/)
├── db_clean.sql                 # Script SQL d'initialisation de la base de données
└── README.md                    # Documentation principale du projet
```

---

## ⚙️ Installation & Déploiement Local (XAMPP)

### Prerequisites
- [XAMPP](https://www.apachefriends.org/) installé avec **PHP 8.0+** et **MySQL**.
- [Composer](https://getcomposer.org/) installé globalement.

### Étapes d'installation

1. **Cloner / Placer le projet dans HTDOCS** :
   Le dossier du projet doit être situé dans : `C:\xampp\htdocs\ccb\`

2. **Configuration de la Base de Données** :
   - Démarrer les services **Apache** et **MySQL** dans le panneau XAMPP.
   - Créer une base de données MySQL nommée `db_ccb`.
   - Importer le fichier `db_clean.sql` dans la base `db_ccb` via phpMyAdmin ou en ligne de commande :
     ```bash
     mysql -u root -p db_ccb < C:\xampp\htdocs\ccb\db_clean.sql
     ```

3. **Configuration de l'Environnement (`.env`)** :
   Le fichier `core/.env` doit être configuré avec les accès locaux :
   ```ini
   APP_NAME=CCB
   APP_ENV=local
   APP_KEY=base64:...
   APP_DEBUG=true
   APP_URL=http://localhost/ccb

   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=db_ccb
   DB_USERNAME=root
   DB_PASSWORD=
   ```

4. **Installation des dépendances & Génération des clés** :
   Dans le dossier `core/` :
   ```bash
   cd core
   composer install
   php artisan key:generate
   php artisan config:clear
   ```

5. **Accès à l'application** :
   Ouvrez votre navigateur et accédez à :
   👉 **`http://localhost/ccb`**

---

## 💡 Commandes Utiles

Toutes les commandes d'administration doivent être exécutées depuis le répertoire `core/` :

- **Vider le cache de configuration** :
  ```bash
  php artisan config:clear
  php artisan cache:clear
  ```
- **Régénérer l'autoloader Composer** :
  ```bash
  composer dump-autoload
  ```
- **Découvrir les paquets installés** :
  ```bash
  php artisan package:discover
  ```

---

## 📄 Licence

Ce projet est la propriété exclusive de la **Compagnie Cacaoyère De Bandama (CCB)**. Tous droits réservés.
