# OPENCLASSROOMS - Parcours Data Scientist - Projet n°7
# Implémentez un modèle de scoring - 80 h

------------------------------
## Documentation de l'API
------------------------------

### Préambule

Afin d'exposer au personnel de Prêt à dépenser le modèle de scoring client développé, une API et une interface ont été créés.

La documentation suivante explique le fonctionnement de l'application.

### Structure des dossiers

| Chemin                                         | Type         | Description                                                                 |
|-----------------------------------------------|--------------|-----------------------------------------------------------------------------|
| `.github/`                                     | Dossier      | Configuration GitHub                                                       |
| └── `workflows/`                               | Dossier      | Contient les workflows GitHub Actions                                      |
|     └── `deploy.yml`                           | Fichier      | Déploiement automatique via GitHub Actions                                 |
| `api/`                                         | Dossier      | Code source de l’API                                                       |
| ├── `model/`                                   | Dossier      | Modèle ML et fichiers d'environnement                                      |
| │   ├── `MLmodel`                              | Fichier      | Fichier MLflow décrivant le modèle                                         |
| │   ├── `conda.yml`                            | Fichier      | Environnement Conda pour exécuter le modèle                                |
| │   ├── `model.pkl`                            | Fichier      | Modèle entraîné sérialisé au format pickle                                 |
| │   ├── `python_env.yaml`                      | Fichier      | Environnement Python requis pour MLflow                                    |
| │   ├── `requirements.txt`                     | Fichier      | Dépendances du modèle                                                      |
| ├── `Dockerfile`                               | Fichier      | Dockerfile pour l’image de l’API                                           |
| ├── `api.py`                                   | Fichier      | Script principal de l’API                                                  |
| └── `requirements.txt`                         | Fichier      | Dépendances nécessaires pour faire tourner l’API                           |
| `cleaned_data/`                                | Dossier      | Données pré-traitées                                                       |
| └── `test_data_cleaned.csv`                    | Fichier      | Jeu de test nettoyé                                                        |
| `dashboard/`                                   | Dossier      | Dashboard Streamlit                                                        |
| ├── `Dockerfile`                               | Fichier      | Dockerfile pour le dashboard                                               |
| ├── `dashboard.py`                             | Fichier      | Application Streamlit                                                      |
| └── `requirements.txt`                         | Fichier      | Dépendances nécessaires au dashboard                                       |
| `tests/`                                       | Dossier      | Tests unitaires                                                             |
| └── `test_api.py`                              | Fichier      | Fichier de test pour l’API                                                 |
| `docker-compose.yml`                           | Fichier      | Orchestration des conteneurs (API + dashboard)                             |
| `requirements.txt`                             | Fichier      | Fichier racine de dépendances                                              |

### Interrogation de l'API

L'API attend les requêtes qui lui sont envoyées sur le port 5000. 

Afin d'obtenir les informations de scoring relatives à un client, il est nécessaire d'envoyer un requête GET de la forme suivante :
* /api/v1/customer?id=10001

  