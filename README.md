# Connection-laravel-angular


Pour commencer un projet avec Laravel pour le backend et Angular pour le frontend, voici les étapes générales que vous pouvez suivre :

### 1. **Installer Laravel**
   - Assurez-vous que PHP, Composer et MySQL (ou une autre base de données) sont installés sur votre machine.
   - Créez un nouveau projet Laravel :
     ```bash
     composer create-project --prefer-dist laravel/laravel nom-du-projet
     ```
   - Configurez votre base de données dans le fichier `.env` de Laravel.

### 2. **Configurer le Frontend avec Angular**
   - Installez Angular CLI si ce n'est pas déjà fait :
     ```bash
     npm install -g @angular/cli
     ```
   - Créez une nouvelle application Angular :
     ```bash
     ng new nom-du-projet-frontend
     ```
   - Une fois votre projet créé, démarrez-le avec :
     ```bash
     ng serve
     ```
   - Cela démarre un serveur de développement et vous permet de visualiser votre application sur `http://localhost:4200`.

### 3. **Connexion entre Laravel et Angular**
   - **API Restful avec Laravel** :
     - Créez des routes API dans Laravel en utilisant des contrôleurs qui renvoient des réponses JSON.
     - Exemples de routes dans `routes/api.php` :
       ```php
       Route::get('/users', [UserController::class, 'index']);
       Route::post('/users', [UserController::class, 'store']);
       ```
     - Utilisez `Laravel Sanctum` ou `JWT` si vous avez besoin d'authentification pour votre API.
   
   - **Consommer l'API Laravel dans Angular** :
     - Utilisez le service `HttpClient` d'Angular pour envoyer des requêtes HTTP à votre API Laravel.
     - Créez un service Angular pour gérer les appels API, par exemple :
       ```typescript
       import { HttpClient } from '@angular/common/http';
       import { Injectable } from '@angular/core';

       @Injectable({
         providedIn: 'root'
       })
       export class ApiService {
         private apiUrl = 'http://votre-backend-url/api';

         constructor(private http: HttpClient) {}

         getUsers() {
           return this.http.get(`${this.apiUrl}/users`);
         }

         createUser(data: any) {
           return this.http.post(`${this.apiUrl}/users`, data);
         }
       }
       ```

### 4. **Configurer le CORS**
   - Dans Laravel, configurez le CORS (Cross-Origin Resource Sharing) pour permettre aux requêtes venant d'Angular d'accéder à l'API.
   - Vous pouvez utiliser le package `barryvdh/laravel-cors` pour simplifier cette configuration.

### 5. **Déploiement**
   - **Backend Laravel** : Déployez votre application Laravel sur un serveur avec Apache ou Nginx, en s'assurant que la base de données est configurée.
   - **Frontend Angular** : Compilez votre application Angular en production avec `ng build --prod`, puis servez les fichiers compilés avec un serveur comme Apache, Nginx, ou même dans un bucket S3 si c'est une application statique.

Si vous avez besoin de plus de détails sur une étape spécifique ou de l'aide pour une partie du projet, n'hésitez pas à demander !
