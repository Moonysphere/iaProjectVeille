

```text
                              .-----.
                            /7  .  (
                           /   .-.  \
                          /   /   \  \
                         / `  )   (   )
                        / `   )   ).  \
                      .'  _.   \_/  . |
     .--.           .' _.' )`.        |
    (    `---...._.'   `---.'_)    ..  \
     \            `----....___    `. \  |
      `.           _ ----- _   `._  )/  |
        `.       /"  \   /"  \`.  `._   |
          `.    ((O)` ) ((O)` ) `.   `._\
            `-- '`---'   `---' )  `.    `-.
               /                  ` \      `-.
             .'                      `.       `.
            /                     `  ` `.       `-.
     .--.   \ ===._____.======. `    `   `. .___.--`     .''''.
    ' .` `-. `.                )`. `   ` ` \          .' . '  8)
   (8  .  ` `-.`.               ( .  ` `  .`\      .'  '    ' /
    \  `. `    `-.               ) ` .   ` ` \  .'   ' .  '  /
     \ ` `.  ` . \`.    .--.     |  ` ) `   .``/   '  // .  /
      `.  ``. .   \ \   .-- `.  (  ` /_   ` . / ' .  '/   .'
        `. ` \  `  \ \  '-.   `-'  .'  `-.  `   .  .'/  .'
          \ `.`.  ` \ \    ) /`._.`       `.  ` .  .'  /
    LGB    |  `.`. . \ \  (.'               `.   .'  .'
        __/  .. \ \ ` ) \                     \.' .. \__
 .-._.-'     '"  ) .-'   `.                   (  '"     `-._.--.
(_________.-====' / .' /\_)`--..____()____..-- `====-. _________)
                 (.'(.'

                    HEY, I'M TIMI!
                 TECHNOLOGY WATCH AGENT
```

## 🐸 Timi — Agent de veille technologique

**Timi** est un agent d’intelligence artificielle spécialisé dans la **recherche d’informations** et la **veille technologique**.

Son objectif est de surveiller, collecter, vérifier et synthétiser des informations provenant de différentes sources afin de faire ressortir les éléments réellement importants.

Timi peut notamment :

* rechercher des informations techniques et technologiques ;
* suivre les évolutions d’un sujet dans le temps ;
* consulter des sources externes grâce à ses tools ;
* analyser des articles, des flux RSS et des documents ;
* identifier les nouveautés, tendances et changements importants ;
* supprimer les doublons entre plusieurs sources ;
* résumer des contenus longs ;
* classer les informations par thème et par niveau de pertinence ;
* conserver le contexte d’une conversation ;
* générer une synthèse de veille claire et structurée.

L’agent s’appuie sur une architecture locale composée de :

* **Gemma 4** comme modèle de langage ;
* **LM Studio** pour exécuter et exposer le modèle localement ;
* **LangChain / LangGraph** pour orchestrer l’agent et ses tools ;
* **Express** pour exposer l’agent sous forme d’API ;
* une **CLI** et une future interface React pour interagir avec Timi.

### Fonctionnement général

```text
Sources de veille
      ↓
Tools de recherche et de lecture
      ↓
Agent Timi
      ↓
Gemma 4 dans LM Studio
      ↓
Analyse, tri et synthèse
      ↓
CLI ou interface web
```

## 🧠 Choix du modèle Gemma 4

La lettre **B** indique le nombre de paramètres du modèle en milliards.

Exemples :

* `4B` représente environ 4 milliards de paramètres ;
* `12B` représente environ 12 milliards de paramètres ;
* `31B` représente environ 31 milliards de paramètres.

En règle générale, un modèle plus grand produit de meilleures analyses, mais demande davantage de mémoire et répond moins rapidement.

Gemma 4 existe notamment en versions **E2B**, **E4B**, **12B**, **26B-A4B MoE** et **31B**. Les modèles E2B et E4B sont optimisés pour les appareils légers, tandis que les modèles 12B, 26B et 31B ciblent davantage les ordinateurs portables puissants et les stations de travail.

### Configuration matérielle indicative

Les valeurs suivantes correspondent principalement à une utilisation locale dans LM Studio avec une version quantifiée en **Q4**. Elles incluent une marge pour LM Studio, le système d’exploitation et le cache de contexte.

| Modèle          |                      Paramètres |    Mémoire minimale indicative | Configuration recommandée                      | Usage conseillé                                         |
| --------------- | ------------------------------: | -----------------------------: | ---------------------------------------------- | ------------------------------------------------------- |
| Gemma 4 E2B     |                  2,3B effectifs | 4 Go de RAM ou mémoire unifiée | 8 Go de RAM                                    | Tests, appareils légers, classification simple          |
| Gemma 4 E4B     |                  4,5B effectifs |                    8 Go de RAM | 12 à 16 Go de RAM                              | Veille légère, résumés, extraction de données           |
| Gemma 4 12B     |                          11,95B |           16 Go de RAM ou VRAM | 24 Go de mémoire unifiée ou 16 Go de VRAM      | Agent local équilibré, tools, analyse et synthèse       |
| Gemma 4 26B-A4B | 26B au total, environ 4B actifs |           24 Go de RAM ou VRAM | 32 Go de mémoire unifiée ou 24 Go de VRAM      | Veille avancée, raisonnement et workflows agentiques    |
| Gemma 4 31B     |                           30,7B |      24 à 32 Go de RAM ou VRAM | 48 à 64 Go de mémoire unifiée ou 32 Go de VRAM | Analyse complexe, meilleure qualité, station de travail |

> Ces configurations sont des estimations pour des modèles quantifiés. Une version non quantifiée peut demander plusieurs fois plus de mémoire.

Google indique que Gemma 4 12B est conçu pour fonctionner localement avec environ **16 Go de RAM, de VRAM ou de mémoire unifiée**.

Les poids non quantifiés occupent environ **24 Go pour le modèle 12B** et environ **62,6 Go pour le modèle 31B**.

Google propose également des versions Gemma 4 optimisées par **Quantization-Aware Training**, notamment au format Q4, afin de réduire fortement les besoins en mémoire. La version E2B optimisée peut descendre autour de 1 Go dans certaines configurations mobiles spécialisées.



## Agent CLI & Server

Un CLI et serveur JavaScript/TypeScript pour tester et interagir avec des agents IA.

## 📦 Installation

```bash
# Installer les dépendances
npm install

# Copier et configurer les variables d'environnement
cp .env.example .env
```

## 🚀 Démarrage rapide

### 1. Démarrer le serveur

```bash
# Démarrer le serveur en mode production
npm run server

# Ou en mode développement avec rechargement automatique
npm run dev
```

Le serveur sera accessible sur `http://localhost:8080`

### 2. Utiliser le CLI

```bash
# Vérifier la connectivité et lister les agents
npm run cli check

# Démarrer une session de chat
npm run cli chat

# Utiliser un agent spécifique
npm run cli chat --agent sallyO

# Mode invoke au lieu de streaming
npm run cli chat --invoke

# Mode debug
npm run cli chat --debug
```

## 🔧 Configuration

### Variables d'environnement

Créez un fichier `.env` avec les variables suivantes :

```env
# Configuration API
API_URL=http://localhost:8080
PORT=8080

# Authentification (optionnelle)
BEARER_TOKEN=votre-token-ici
REQUIRE_AUTH=false

# Clés API pour les agents réels
OPENAI_API_KEY=sk-...
TAVILY_API_KEY=tvly-...
```

### Configuration des agents

Modifiez le fichier `agents_config.json` pour configurer vos agents :

```json
{
  "api_url": "http://localhost:8080",
  "agents": [
    {
      "id": "sallyO",
      "name": "SallyO",
      "description": "Un agent IA spécialisé dans les opportunités CRM"
    }
  ]
}
```

## 📡 Endpoints API

### Vérification de santé
```http
GET /health
```

### Liste des agents
```http
GET /agents
Authorization: Bearer your-token
```

### Invocation directe
```http
POST /:agentId/invoke
Authorization: Bearer your-token
Content-Type: application/json

{
  "message": "Votre message",
  "thread_id": "optional-thread-id"
}
```

### Streaming SSE
```http
POST /:agentId/stream
Authorization: Bearer your-token
Content-Type: application/json

{
  "message": "Votre message",
  "thread_id": "optional-thread-id"
}
```

### Arrêter la génération
```http
POST /:agentId/stop
Authorization: Bearer your-token
Content-Type: application/json

{
  "thread_id": "thread-id-to-stop"
}
```

### Gestion des conversations
```http
GET /conversations
GET /conversations/:threadId
Authorization: Bearer your-token
```

## 💬 Utilisation du CLI

### Commandes spéciales pendant le chat

- `!clear` - Réinitialiser la conversation
- `!debug` - Basculer le mode debug
- `exit` - Quitter le chat

### Options de ligne de commande

```bash
# Commande check
npm run cli check [options]
  --api-url <url>        URL de l'API
  --bearer-token <token> Token d'authentification
  -d, --debug           Mode debug

# Commande chat
npm run cli chat [options]
  -a, --agent <id>       ID de l'agent
  -i, --invoke          Mode invoke (pas de streaming)
  --api-url <url>        URL de l'API
  --bearer-token <token> Token d'authentification
  -d, --debug           Mode debug
  --no-context          Désactiver le contexte
```

## 🔄 Streaming et événements SSE

Le serveur supporte les Server-Sent Events avec les types d'événements suivants :

- `stream_start` - Début du streaming
- `stream_token` - Token de réponse
- `stream_end` - Fin du streaming
- `tool_execution_start` - Début d'utilisation d'outil
- `tool_execution_complete` - Fin d'utilisation d'outil
- `tool_execution_error` - Erreur d'outil
- `error` - Erreur générale

## 🛠️ Développement

### Structure du projet

```
agent-example/
├── Agents/Agent/Agent.mts  # Agent LangChain
├── CLI/cli.mts            # CLI pour tester les agents
├── serveur/server.mts     # Serveur Express.js
├── CLI/agents_config.json # Configuration des agents
├── package.json           # Dépendances et scripts
└── README.md              # Documentation
```

### Scripts disponibles

```bash
npm run cli      # Lancer le CLI
npm run server   # Démarrer le serveur
npm run dev      # Mode développement avec rechargement
```

### Intégration avec de vrais agents

Pour remplacer le `MockAgent` par de vrais agents :

1. Modifiez la classe `MockAgent` dans `server.mts`
2. Intégrez avec LangChain, OpenAI, ou votre framework préféré
3. Adaptez les méthodes `generateResponse` et `invokeResponse`

## 🔐 Sécurité

- L'authentification par token Bearer est optionnelle (configurable)
- Les tokens sont stockés en mémoire côté serveur
- Les conversations sont en mémoire (remplacer par une DB en production)
- CORS configuré pour accepter toutes les origines (à restreindre en production)

## 📝 Exemples d'utilisation

### Test rapide

```bash
# Terminal 1 - Démarrer le serveur
npm run server

# Terminal 2 - Tester la connectivité
npm run cli check

# Terminal 3 - Commencer à chatter
npm run cli chat
```

### Avec authentification

```bash
# Avec token dans .env
BEARER_TOKEN=mon-super-token npm run server

# Utiliser le même token dans le CLI
npm run cli chat --bearer-token mon-super-token
```

### Mode debug

```bash
# Voir tous les détails des requêtes
npm run cli chat --debug
```

## 🚨 Limitations actuelles

- Agents simulés (MockAgent)
- Stockage en mémoire uniquement
- Pas de persistance des conversations
- Authentification basique
- Pas de rate limiting

## 🎯 Prochaines étapes

- [ ] Intégration avec de vrais agents LangChain
- [ ] Base de données pour la persistance
- [ ] Authentification robuste
- [ ] Rate limiting
- [ ] Interface web
- [ ] Docker
- [ ] Tests automatisés

## 📄 Licence

MIT

---

🚀 **Prêt à discuter avec vos agents IA !** 