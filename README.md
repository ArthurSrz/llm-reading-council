# Le conseil des machines pensantes

![llmcouncil](header.jpg)

*Délibérations de la commission permanente des intelligences artificielles*

---

## Exposé des motifs

Considérant que la République, une et indivisible, ne saurait confier ses interrogations les plus pressantes à un unique oracle numérique — fût-il américain, californien, ou issu des laboratoires de la rue de Grenelle —, le présent dispositif institue un **conseil délibératif** composé de plusieurs machines pensantes.

Car, comme l'énonçait si justement Pierre Mendès France : *« Gouverner, c'est choisir. »* Et pour bien choisir, encore faut-il entendre plusieurs avis, les soumettre à l'examen contradictoire, et désigner un président du Conseil pour en tirer la synthèse.

Cette application web, sobre comme un costume de la rue de Rivoli, utilise le protocole OpenRouter pour convoquer simultanément des LLM open-source et **surtout gratuits (!)**, leur demander de s'évaluer mutuellement (à bulletins secrets, naturellement), avant qu'un président de séance ne proclame la réponse définitive.

## Ordre du jour des délibérations

Lorsque le citoyen soumet une question au Conseil, la procédure suivante est observée :

### Article premier — Première lecture

La question de l'administré est transmise à l'ensemble des conseillers numériques. Chacun rédige sa réponse, indépendamment et sans concertation préalable. Les interventions sont consignées dans des onglets distincts, consultables par le requérant tel un procès-verbal de séance.

### Article 2 — Commission d'examen à huis clos

Chaque conseiller reçoit les réponses de ses pairs, mais — innovation décisive ! — les identités sont anonymisées. Point de favoritisme, point de *combinazione* : les réponses sont désignées « Réponse A », « Réponse B », etc., comme les bulletins dans l'urne.

Chaque machine évalue et classe ses collègues selon des critères de justesse et de perspicacité. Car, ainsi que le rappelait Edgar Faure avec son ironie coutumière : *« L'immobilisme est en marche, et rien ne l'arrêtera »* — sauf, peut-être, dans ce cas, un bon système de notation.

### Article 3 — Motion de synthèse

Le président du Conseil, fort de l'ensemble des délibérations, rédige la réponse finale. Il compile, il synthétise, il tranche. Comme au Palais-Bourbon, il faut bien que quelqu'un conclue — même si, en IVe République, le gouvernement serait déjà tombé avant la fin de la phrase.

---

## Avertissement : code de circonstance

Le présent dispositif fut élaboré un samedi, dans l'urgence caractéristique de tout gouvernement de la IVe République. À l'instar du cabinet Pleven II (durée de vie : sept mois, trois semaines et deux jours), ce code n'est pas conçu pour l'éternité.

Il fut « vibe-codé », comme on formait jadis les coalitions : rapidement, sans trop y croire, dans l'espoir que l'édifice tienne jusqu'au prochain remaniement ministériel.

L'auteur, tel Guy Mollet recevant les tomates d'Alger en février 1956, décline toute responsabilité quant aux projectiles virtuels. Le code est fourni « en l'état », comme les promesses électorales. Les bibliothèques sont désormais caduques ; demandez à votre propre machine pensante de modifier ce qui vous déplaît.

---

## Installation du dispositif

### 1. Constitution des dépendances

Le projet utilise [uv](https://docs.astral.sh/uv/) pour l'intendance pythonesque.

**Chancellerie (backend) :**
```bash
uv sync
```

**Préfecture (frontend) :**
```bash
cd frontend
npm install
cd ..
```

### 2. Accréditation auprès du bureau central

Créer un fichier `.env` à la racine du projet :

```bash
OPENROUTER_API_KEY=sk-or-v1-...
```

Obtenir ses lettres de créance sur [openrouter.ai](https://openrouter.ai/). Prévoir les crédits nécessaires, ou souscrire au réapprovisionnement automatique.

### 3. Nomination des conseillers

Éditer `backend/config.py` pour composer votre Conseil :

```python
COUNCIL_MODELS = [
    "openai/gpt-oss-120b:free",
    "openai/gpt-oss-20b:free",
    "mistralai/mistral-small-3.1-24b-instruct:free",
    "google/gemma-3-27b-it:free",
]

CHAIRMAN_MODEL = "openai/gpt-oss-120b:free"
```

---

## Convocation de l'assemblée

**Option 1 : décret d'ouverture automatique**
```bash
./start.sh
```

**Option 2 : convocation manuelle**

Terminal 1 (chancellerie) :
```bash
uv run python -m backend.main
```

Terminal 2 (préfecture) :
```bash
cd frontend
npm run dev
```

Puis ouvrir http://localhost:5173 dans votre navigateur.

---

## Architecture technique

- **Chancellerie :** FastAPI (Python 3.10+), httpx asynchrone, API OpenRouter
- **Préfecture :** React + Vite, react-markdown pour le rendu
- **Archives :** fichiers JSON dans `data/conversations/`
- **Intendance :** uv pour Python, npm pour JavaScript
