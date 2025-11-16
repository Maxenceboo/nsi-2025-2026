# Documentation Python – PILES (STACK)

## 1. Définition

Une **pile** est une structure de données linéaire avec une seule extrémité d’accès.

Principe :
**LIFO** = *Last In, First Out* (dernier entré, premier sorti).

Exemples d'utilisation (théorique) :

* historique de navigation
* appels de fonctions
* annulation (undo)

En Python, il n’y a pas de type `stack` natif.
On utilise généralement une **liste**.

---

## 2. Représentation avec une liste

Convention classique :

* la **fin de la liste** correspond au **sommet** de la pile.

Exemple :

```python
pile = []           # pile vide
pile.append(10)     # empiler
pile.append(20)
pile.append(30)
# pile = [10, 20, 30]  → 30 est au sommet
```

---

## 3. Opérations de base (version naïve)

Empiler (push) :

```python
pile.append(x)
```

Dépiler (pop) :

```python
x = pile.pop()
```

Tester si vide :

```python
len(pile) == 0
# ou
not pile
```

Regarder le sommet sans dépiler :

```python
sommet = pile[-1]
```

---

## 4. Type abstrait Pile (implémentation simple)

Implémentation avec fonctions :

```python
def pile_vide():
    return []

def est_vide(p):
    return len(p) == 0

def empiler(p, x):
    p.append(x)

def depiler(p):
    return p.pop()

def sommet(p):
    return p[-1]
```

Remarque : `depiler` et `sommet` lèvent une exception si la pile est vide.

---

## 5. Erreurs possibles

Si on dépile alors que la pile est vide :

```python
pile = []
pile.pop()
# IndexError: pop from empty list
```

Si on accède au sommet d’une pile vide :

```python
pile = []
pile[-1]
# IndexError: list index out of range
```

Bonne pratique : vérifier `est_vide(p)` avant.

---

## 6. Exemple d’utilisation simple

```python
pile = pile_vide()
empiler(pile, 1)
empiler(pile, 2)
empiler(pile, 3)

print(depiler(pile))  # 3
print(depiler(pile))  # 2
print(depiler(pile))  # 1
```

---

## 7. Application classique : conversion en binaire

Principe :

* on divise le nombre par 2,
* on empile les restes,
* on dépile pour reconstruire l’écriture binaire dans le bon sens.

Pseudo-code :

```python
def en_binaire(n):
    p = pile_vide()
    while n > 0:
        empiler(p, n % 2)
        n = n // 2
    resultat = ""
    while not est_vide(p):
        resultat = resultat + str(depiler(p))
    return resultat
```

---

## 8. Application classique : vérification de parenthésage

On lit une chaîne caractère par caractère.

Règles :

* si on voit `'('` → empiler
* si on voit `')'` → dépiler une `'('` si possible
* à la fin → pile doit être vide

Pseudo-code :

```python
def bien_parenthesee(chaine):
    p = pile_vide()
    for c in chaine:
        if c == '(':
            empiler(p, c)
        elif c == ')':
            if est_vide(p):
                return False
            depiler(p)
    return est_vide(p)
```

---

## 9. Complexité (pile implémentée par liste Python)

Empiler :

```python
pile.append(x)
```

→ temps moyen `O(1)`

Dépiler :

```python
pile.pop()
```

→ temps `O(1)`

Tester vide, sommet, etc.
→ `O(1)`

---

## 10. Résumé rapide

* pile = structure **LIFO**
* en Python : on utilise une **list**
* sommet = fin de la liste
* opérations principales :

    * `append(x)` → empiler
    * `pop()` → dépiler
* utiliser une fonction `est_vide` pour éviter les erreurs
* applications : conversions, analyse syntaxique, historiques, etc.
