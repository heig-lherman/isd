# ISD - SA2022 - TP1

Fichier de réponses

Professeur: Carlos Peña
Assistant: Thibault Schowing

Étudiant: [redacted]

---

# Partie 1

---

## Exercice 1

(5 points)

1. Ecrivez un script qui génère une liste contenant un million de valeurs entières aléatoires entre 1 et 10 (y compris) et qui calcule le pourcentage de valeurs paires dans cette liste.

```py
# Importation du module random.
from random import randrange

# Générer une liste de valeurs aléatoire
N = 1_000_000
MIN = 1
MAX = 10

random_range = [randrange(MIN, MAX + 1) for i in range(N)]

# Générer une liste / compter les valeurs paires et calculer le pourcentage de ces valeurs.
even_count = sum(1 - n % 2 for n in random_range)
percentage = even_count / N

# Afficher le résultat
print(f"percentage of even numbers: {percentage * 100}%")
```

**Points obtenus: /5**
**Remarques:**

## Exercice 2

(10 points)

2.1) Décrivez avec vos mots et l'aide de la documentation les trois methodes décrites ci-dessus, leur différences et les fonctions utilisées.

Réponse:

#### Méthode 1

Une liste est formée de deux intervalles :

- Le premier regroupe les nombres entre 1 et 10, où l'espace entre deux nombres est de 2. Ainsi, seul les nombres impairs sont inscrits.
- Le deuxième regroupe les nombres entre 12 et 21, où l'espace entre deux nombres est de 2. Ainsi, seul les nombres pairs sont inscrits.

L'addition des deux intervalles constitue une liste des nombres impairs inférieurs ou égaux à 10 et les nombres pairs supérieurs à 10, mais inférieurs à 21.

En partant de cette liste, tous les chiffres sont ensuite élevés au carré pour formuler la liste finale.

#### Méthode 2

Un intervalle est formé depuis tous les nombres entre 1 et 20.

De cet intervalle on récupère seulement:

- Les nombres dont le modulo à 2 n'est pas 0 (nombres impairs), si le nombre en question est inférieur ou égal à 10
- Les nombres dont le modulo à 2 est 0 (nombres pairs), si le nombre en question est supérieur à 10

Pour tous les nombres récupérés on les élève au carré pour les avoirs dans la liste finale.

#### Méthode 3

La solution 3 génère d'abord la liste des carrés des nombres entre 1 et 10 (inclus) avec un intervalle depuis 1 de 2 entre chaque nombre.

Ensuite une autre liste et générée avec les carrés des nombres entre 12 et 20 (inclus) avec un intervalle depuis 12 de 2 entre chaque nombre.

Les deux listes sont concaténées pour donner la liste demandée.

2.2) A partir de la liste "objets" données ci-dessous, créez une liste contenant uniquement les mots de la première liste qui contiennent la lettre "z" ou "Z".

```py
filtered_objects = [x for x in objets if 'z' in x.lower()]
```

**Points obtenus: /5**
**Remarques:**

---

# Partie 2

---

(5 points)

1. Pourquoi utiliser NumPy ?

Réponse:

> Car ça nous permet d'utiliser une implémentation de tableaux de données rapide et efficace, qui peut nous permettre de modéliser tout type de matrice.

2. Comment s'appelle (n.b. "de quel type est") l'objet "array" dans NumPy et que signifie son nom ?

Réponse:

> `numpy.ndarray` - n-dimensional array

3. Pourquoi utiliser NumPy est-il plus rapide qu'utiliser les listes ?

Réponse:

> Car NumPy, contrairement aux listes, stocke les données en mémoire sous forme de chaine continue ce qui permet un accès rapide.

4. A quelle question le code "# Question 4" ci-dessous répond-il ?

Réponse:

> Question 2

5. Affichez la somme des deux derniers éléments du tableau

```py
arr = np.array([1, 2, 3, 4, 5])
arr_sum = arr[-2:].sum()
print(arr_sum)
```

**Points obtenus: /5**
**Remarques:**

---

# Partie 3

---

(5 points)

1. Pourquoi utiliser Pandas ?

Réponse:

> C'est une librairie qui permet de facilement lire un set de données et ajoute plusieurs façons de les interpréter, filtrer, nettoyer et manipuler.

2. Que peut faire pandas (d'après le tuto w3schools) ?

Réponse:

> Permet de répondre à des questions comme :
>
> - Existe-t-il une correlation entre deux colonnes?
> - Quelle est la valeur moyenne d'une colonne?
> - Quelle est la valeur maximale d'une colonne?
> - Quelle est la valeur minimale d'une colonne?
>
> Il est aussi possible de supprimer des lignes selon plusieurs critères.

3. Que fait l'exemple "Question 3" ci-dessous ?

Réponse:

> Il constitue un set de données depuis des marques de voitures et les nombres de conducteurs de la marque en question qui sont décédés au volant.

4. Compléter la cellule "Question 4" pour afficher les lignes demandées. Utiliser l'attribut _loc_ comme décrit dans le tutoriel. Que remarquez vous concernant l'utilisation de simples crochets ([...]) ou doubles crochets ([[x,y]]) pour extraire _une_ colonne du dataframe ? En utilisant la fonction type(), donnez le type de données retournées avec les simples crochets ([...]) ou doubles crochets ([[x,y]]).

Réponse:

> En utilisant les simples crochets, pandas va en générer une `pandas.Series`.
> Avec les doubles crochets, comme il est possible de sélectionner plusieurs colonnes, le type reste `pandas.DataFrame` qui est une sous-matrice du set de base.

5. Complétez le code comme demandé dans la cellule "Question 5 - exercice". Extrait du tutoriel Pandas de w3school.

```py
# 1) Enlevez les données manquantes (NaN = Not a Number) et créez un nouveau dataframe appelé df_clean
#    (n.b ne changez pas le dataframe original, n'utilisez pas *inplace=True*)
#    n'hésitez pas à utiliser "print(df_clean)" pour voir les changements, mais déplacez-le / commentez-le
#    pour ne pas encombrer l'affichage de votre cellule !
df_clean = df.dropna()

# 2) La ligne 26 contient une date au mauvais format. Pour cela nous allons convertir la colonne "Date".
#    Attention a bien faire cette opération sur df_clean et non sur df (modifiez par rapport au tutoriel).
#    En cas de Warnings, vous pouvez l'ignorer.
df_clean['Date'] = pd.to_datetime(df_clean['Date'])

# 3) La valeur à la ligne 7 vous semble suspecte. Vous pouvez choisir de la remplacer par une valeur qui a plus de sense (45)
#    ou vous pouvez simplement supprimer la ligne. Basez-vous toujours sur le tutoriel pour réaliser cette tâche.
for x in df_clean.index:
    if df_clean.loc[x, 'Duration'] > 120:
        df_clean.drop(x, inplace=True)
```

**Points obtenus: /5**
**Remarques:**

---

## Partie 4

(2 points)

1. Pourquoi utiliser Matplotlib ?

Réponse:

> Permet de générer des graphes à partir de données.

2. Allez regarder la gallerie des exemples de Matplotlib et regardez rapidement les 5 premières sections (jusqu'à la section "Pie and polar charts compris"). Choisissez 2 types de graphiques (Ou prenez les plus importants: Barchart, Boxplot et Scatterplot) et écrivez une courte description pour chaqu'un d'eux.

Réponse:

> **Bar charts**: (Diagrammes à barres) Représente des variables avec des barres rectangulaires dont la hauteur est proportionnelle à la valeur qu'elle représente.$
>
> **Box plots**: (Boîtes à moustaches) Représente des une plage de données par variables avec une boîte qui commence au premier quartile jusqu'au troisième quartile.
>
> **Scatter plots**: (Nuages de points) Représente des variables avec des points dont les coordonnées sont proportionnelles aux valeurs qu'ils représentent.

**Points obtenus: /5**
**Remarques:**
