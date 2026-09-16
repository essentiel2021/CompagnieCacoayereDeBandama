# CCB Core Application (Laravel 9.x)

Ce dossier contient l'application cœur de la **Compagnie Cacaoyère De Bandama (CCB)** développée sous le framework **Laravel 9.52**.

---

## 🛠️ Spécifications Techniques

- **Framework** : Laravel 9.52.16
- **Version PHP requise** : >= 8.0.2
- **Base de données** : MySQL 8.0+ / MariaDB
- **Autoloading** : PSR-4

---

## 📦 Packages & Extensions Clés

L'application utilise plusieurs extensions spécialisées pour la gestion cartographique, les exports, les graphiques et le reporting :

| Package | Usage |
| :--- | :--- |
| `arielmejiadev/larapex-charts` & `laraveldaily/laravel-charts` | Tableaux de bord & graphiques interactifs |
| `barryvdh/laravel-dompdf` & `mpdf/mpdf` | Génération de documents et rapports PDF |
| `maatwebsite/excel` & `phpoffice/phpspreadsheet` | Exportation et importation de fichiers Excel/CSV |
| `spatie/laravel-permission` | Gestion des rôles, permissions et habilitations |
| `spatie/browsershot` | Captures d'écran et rapports HTML dynamiques |
| `laravel/sanctum` | Authentification API sécurisée pour applications mobiles |
| `yajra/laravel-datatables-*` | Grilles de données interactives avec filtres avancés |
| `milon/barcode` & `simplesoftwareio/simple-qrcode` | Génération de codes-barres et QR codes pour la traçabilité des sacs/scellés |
| `intervention/image` | Traitement et optimisation des photos de profil / documents |

---

## 💻 Instructions de Maintenance CLI

Toutes les commandes d'administration et d'entretien s'exécutent dans ce dossier (`core/`) :

```bash
# Vérifier la version de Laravel
php artisan --version

# Découvrir et enregistrer les paquets Laravel
php artisan package:discover

# Vider les caches système et de configuration
php artisan config:clear
php artisan cache:clear
php artisan route:clear
php artisan view:clear

# Régénérer l'autoloader composer
composer dump-autoload
```

Pour la documentation globale et le guide de démarrage de l'application, veuillez consulter le [README principal](../README.md).
