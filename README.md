# 🧠 Jarvis – AI Personal Assistant with n8n

Jarvis est un assistant personnel intelligent construit avec **n8n** et un **modèle de langage**, capable de comprendre des requêtes en langage naturel et d’orchestrer automatiquement des outils du quotidien comme **Gmail**, **Google Calendar** ou **Google Tasks**.

Le projet met l’accent sur la **prise de décision par l’IA**, tout en conservant un **contrôle strict de l’exécution via n8n**.

---

## 🎯 Objectif du projet

L’objectif est de démontrer comment une IA peut être utilisée comme **agent décisionnel**, et non comme un simple chatbot.

Jarvis :

- comprend l’intention de l’utilisateur en langage naturel  
- choisit l’action appropriée  
- structure les paramètres nécessaires  
- déclenche uniquement les outils réellement disponibles dans le workflow  

👉 **L’IA ne réalise jamais directement les actions** : elle se contente de décrire précisément ce que **n8n doit exécuter**.

---

## 🏗️ Architecture générale

Le workflow est organisé autour de plusieurs blocs :

### Telegram Trigger
Point d’entrée utilisateur (messages en langage naturel).

### Jarvis (Agent IA)
Analyse la demande, détecte l’intention et génère une instruction structurée en JSON.

### Modules métiers (MCP)

- Gmail (emails, résumés, brouillons)  
- Google Calendar (événements)  
- Google Tasks (tâches)  
- Autres services extensibles  

### Set Reply Message
Génère une réponse claire et lisible pour l’utilisateur.

### Retour Telegram
Envoie le résultat ou la confirmation de l’action.

---

## 🧠 Rôle de l’IA (Prompt System)

Le comportement de Jarvis est entièrement contrôlé par un **prompt système strict**.

### Contraintes principales

- sortie exclusivement en **JSON**
- format imposé et vérifiable
- liste fermée d’outils autorisés
- aucune invention de capacités
- même langue que l’utilisateur

### Format de sortie imposé

```json
{
  "intent": "email | calendar | tasks | notes | reminder | veille | rag | smalltalk",
  "action": "action précise à exécuter",
  "parameters": {},
  "answer_for_user": "Message destiné à l'utilisateur"
}
```

Cette approche garantit :

- la fiabilité des actions  
- l’absence d’hallucinations  
- une séparation claire entre compréhension et exécution  

---

## 🔧 Fonctionnalités principales

### 📧 Emails (Gmail)

- Résumer le dernier email reçu  
- Lire ou rechercher des emails  
- Créer des brouillons de réponse  
- Répondre à un email (si autorisé)  

### 📅 Agenda (Google Calendar)

- Créer des événements à partir de phrases naturelles  
- Gérer automatiquement dates et horaires  
- Vérifier la disponibilité  

### ✅ Tâches (Google Tasks)

- Créer une tâche  
- Marquer une tâche comme terminée  
- Lister les tâches  

### 🧠 Autres

- Gestion des erreurs compréhensible  
- Suggestions d’actions alternatives  
- Mémoire contextuelle (si activée)  

---

## 🚀 Exemples d’interactions

### Utilisateur
```text
Résume mon dernier mail reçu
```


### Jarvis
- détecte une intention **email**
- récupère le dernier email
- génère un résumé
- renvoie le résultat sur Telegram

---

## 🖥️ Exécution du projet

- Projet exécuté en local via n8n (self-hosted)
- Les identifiants Google sont conservés localement pour des raisons de sécurité
- Le workflow peut être exporté / importé facilement

---


## 📹 Démonstration

Une vidéo de démonstration accompagne ce projet et présente :

    - l’architecture n8n
    - le prompt système
    - plusieurs scénarios d’utilisation en temps réel

---


## 📌 Points clés du projet

- Orchestration IA contrôlée
- Prompt strict et structuré
- Séparation claire IA / exécution
- Langage naturel sans format imposé
- Architecture extensible

---

## 🧑‍💻 Auteurs

### Yoann Le Chevalier, Timothé Winkler et Mathis Truong
Projet réalisé dans le cadre d’un projet pédagogique, visant à démontrer l’utilisation avancée d’agents IA avec n8n.
