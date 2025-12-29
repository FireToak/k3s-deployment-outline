# 📝 Déploiement Kubernetes (K3s) - Outline Wiki

Ce dépôt contient les manifestes "Infrastructure as Code" pour déployer **Outline**, une solution de base de connaissances collaborative, sur un cluster **K3s**.

L'architecture met en œuvre une stack complète avec base de données, cache, et gestion d'identité centralisée.

## 🏗️ Architecture Technique

Le déploiement orchestre les composants suivants :

* **Application :** Outline (Wiki)
* **Base de données :** PostgreSQL 18 (Données structurées)
* **Cache :** Redis (Performance et gestion des tâches)
* **Ingress Controller :** Traefik (Gestion du trafic entrant via `IngressRoute`)
* **Sécurité / SSO :** Intégration OIDC avec **Authentik** (Identity Provider)

## 📂 Structure du dépôt

* `/outline` : Contient les manifestes Kubernetes (Deployment, Service, IngressRoute).
* `ingress.yaml` : Configuration du routage Traefik.
* `outline-secret.example.yaml` : Modèle pour la configuration des secrets.

## 🚀 Prérequis

* Un cluster Kubernetes fonctionnel (testé sur K3s).
* Un nom de domaine configuré pointant vers le cluster.
* Un provider OIDC (ex: Authentik, Keycloak) pour l'authentification.

## 🛠️ Installation

1.  **Cloner le dépôt :**
    ```bash
    git clone [https://github.com/FireToak/k3s-deployment-outline.git](https://github.com/FireToak/k3s-deployment-outline.git)
    cd k3s-deployment-outline
    ```

2.  **Configurer la sécurité :**
    Copiez le fichier d'exemple et insérez vos propres secrets (Clés OIDC, Mots de passe BDD).
    ```bash
    cp outline-secret.example.yaml outline-secret.yaml
    # Éditez le fichier outline-secret.yaml avec vos valeurs
    ```

3.  **Déployer la stack :**
    ```bash
    kubectl apply -f outline/ -n outline
    ```

4.  **Vérification :**
    ```bash
    kubectl get pods -n outline
    ```

## 👤 Auteur

**Louis MEDO** - Passionné d'administration système
*Projet réalisé dans le cadre de la mise en place d'une infrastructure On-Premise.*