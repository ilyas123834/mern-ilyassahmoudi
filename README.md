# CRM MERN

Application de gestion de clients (CRM) construite avec la stack MERN :
**MongoDB Atlas, Express, React, Node.js**.

TP 2 : Projet fil rouge, module CRM / Développement web full-stack (Professeur Othman Mekouar).

Auteur : Sahmoudi Ilyas, ESISA (Fès)

## Fonctionnalités

- Ajouter un client (nom, email, entreprise)
- Afficher tous les clients dans un tableau
- Changer le statut d'un client : prospect, client ou inactif
- Supprimer un client
- Rechercher par nom ou email
- Données conservées dans MongoDB Atlas

## Architecture

```
crm-mern/
├── backend/     API REST (Node.js, Express, Mongoose)
│   ├── config/db.js         connexion à MongoDB
│   ├── models/Client.js     modèle et règles de validation
│   ├── routes/clients.js    routes CRUD
│   ├── server.js            point d'entrée
│   └── .env.example         variables nécessaires
└── frontend/    Interface (React, Create React App)
    ├── public/index.html
    └── src/
        ├── components/      Header, ClientForm, ClientList
        ├── services/clientService.js   appels à l'API
        ├── App.js
        └── .env.example
```

React ne parle jamais directement à MongoDB : le navigateur appelle l'API, et seule l'API accède à la base.

## API

| Méthode | Adresse              | Action              | Succès |
|---------|----------------------|---------------------|--------|
| GET     | /api/clients         | Lire tous les clients | 200  |
| GET     | /api/clients/:id     | Lire un client      | 200    |
| POST    | /api/clients         | Créer un client     | 201    |
| PATCH   | /api/clients/:id     | Modifier un client  | 200    |
| DELETE  | /api/clients/:id     | Supprimer un client | 200    |

Codes d'erreur : 400 (données invalides), 404 (client introuvable), 409 (email déjà utilisé), 500 (erreur serveur).

## Installation

Prérequis : Node.js (LTS), Git, un cluster MongoDB Atlas.

```bash
git clone https://github.com/ilyas123834/crm-mern.git
cd crm-mern
```

### Backend

```bash
cd backend
npm install
cp .env.example .env     # puis remplir les valeurs
npm run dev
```

L'API démarre sur http://localhost:4000.

### Frontend

```bash
cd frontend
npm install
cp .env.example .env
npm start
```

L'application s'ouvre sur http://localhost:3000.

## Variables d'environnement

| Variable           | Où       | En local                           | Sur Vercel                              |
|--------------------|----------|------------------------------------|-----------------------------------------|
| MONGODB_URI        | Backend  | URI Atlas (avec `/crm`)            | URI Atlas                               |
| FRONTEND_URL       | Backend  | http://localhost:3000              | Adresse du frontend Vercel              |
| PORT               | Backend  | 4000                               | À ne pas définir                        |
| REACT_APP_API_URL  | Frontend | http://localhost:4000/api/clients  | Adresse du backend Vercel + /api/clients |

Les fichiers `.env` ne sont jamais publiés sur GitHub (voir `.gitignore`).

## Déploiement

Deux projets Vercel créés à partir du même dépôt GitHub :

1. `crm-backend` (Root Directory : `backend`, variable `MONGODB_URI`)
2. `crm-frontend` (Root Directory : `frontend`, variable `REACT_APP_API_URL`)
3. Retour sur le backend : ajouter `FRONTEND_URL`, puis redéployer.

## Liens

- Dépôt GitHub : _à compléter_
- Frontend Vercel : _à compléter_
- API Vercel : _à compléter_
