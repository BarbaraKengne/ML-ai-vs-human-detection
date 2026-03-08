# Détection de textes générés par IA

Projet personnel — Licence 3 Informatique, Aix-Marseille Université.

Avec GPT-4, Claude, Gemini qui génèrent des textes de plus en plus convaincants, j'ai voulu explorer si des modèles classiques de ML pouvaient encore les distinguer d'un texte humain.

---

## Ce que fait ce projet

À partir d'un dataset de 1 000 textes (537 humains, 463 IA — dont GPT-4, Claude, Gemini), j'ai testé deux approches :

**Approche 1 — Features stylistiques numériques**
Utiliser des métriques pré-calculées : perplexité, burstiness, diversité lexicale, cohérence sémantique...

**Approche 2 — TF-IDF sur le texte brut**
Laisser le modèle apprendre directement depuis les mots utilisés.

Et j'ai analysé les mots "trahisseurs" : quels termes sont le plus associés aux textes IA vs humains ?

## Résultats

**Approche numérique :**

| Modèle | Accuracy | F1-Score |
|--------|----------|----------|
| Régression Logistique | 51% | 26% |
| Random Forest | 55.5% | 45% |
| SVM Linéaire | 51% | 26% |

**Approche TF-IDF :**

| Modèle | Accuracy | F1-Score |
|--------|----------|----------|
| Naive Bayes | 52.5% | 34% |
| Régression Logistique | 51.5% | 43% |
| SVM Linéaire | 53% | 48% |

**Observation clé :** les scores modestes (~50%) ne sont pas un échec — ils reflètent la difficulté réelle du problème. Les LLMs modernes produisent des textes stylistiquement très proches des textes humains, surtout sur des textes courts. Ce résultat est lui-même informatif.

---

## Fichiers

- `ai_vs_human_barbara.ipynb` — notebook complet
- `AuthentiText_X_2026_AI_vs_Human_Detection_1K.csv` — dataset

---

## Lancer le projet

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook ai_vs_human_barbara.ipynb
```

---

## Ce que j'ai trouvé intéressant

Les trois modèles IA (GPT-4, Claude, Gemini) ont des profils stylistiques légèrement différents entre eux. Ça ouvre une piste : est-ce qu'on pourrait classifier non pas juste "IA ou humain" mais "quel modèle IA ?" — c'est ce que j'aimerais explorer ensuite avec BERT.

## Pistes d'amélioration

- Classification multi-classe : Human / GPT-4 / Claude / Gemini
- Tester avec des embeddings BERT sur des textes plus longs
- Collecter des textes plus longs pour améliorer la robustesse

---

## Auteure

**Barbara KENGNE**
Licence 3 Informatique — Aix-Marseille Université
[LinkedIn](https://www.linkedin.com/in/barbara-nguimfack-kengne-343094303) | [GitHub](https://github.com/BarbaraKengne) | [Kaggle](https://kaggle.com/barbarakengne)
