# **Documentation Python – LISTES**

*(version moche, brute, qui pique un peu les yeux)*

---

## **1. Définition**

En Python, une liste est un objet **list**.
Elle permet de stocker plusieurs valeurs dans un seul conteneur.

Syntaxe :

```
[n1, n2, n3, ...]
```

Exemple :

```
l = [1, 5, 8, 2]
```

Les éléments peuvent être de types différents.

```
l = [1, "abc", True, 3.14]
```

---

## **2. Accès aux éléments**

L’accès se fait via des indices.
L’indice commence à **0**.

```
l[0]  # premier élément
l[1]  # deuxième élément
```

Indices négatifs :

```
l[-1]  # dernier élément
l[-2]  # avant-dernier élément
```

Erreur si l’indice dépasse la taille :

```
IndexError: list index out of range
```

---

## **3. Modifier un élément**

```
l[2] = 99
```

---

## **4. Longueur de la liste**

```
len(l)
```

---

## **5. Ajouter / supprimer**

Ajouter en fin :

```
l.append(x)
```

Supprimer le dernier élément :

```
l.pop()
```

Supprimer un élément précis :

```
l.remove(x)
```

Insérer à un indice :

```
l.insert(i, x)
```

---

## **6. Parcourir une liste**

Boucle simple :

```
for e in l:
    print(e)
```

Boucle avec indices :

```
for i in range(len(l)):
    print(i, l[i])
```

---

## **7. Rechercher un élément**

Savoir si un élément existe :

```
x in l
```

Trouver l’indice :

```
l.index(x)
```

Erreur si x n’est pas là :

```
ValueError: x is not in list
```

---

## **8. Trier une liste**

Trier croissant :

```
l.sort()
```

Trier décroissant :

```
l.sort(reverse=True)
```

Trier sans modifier :

```
sorted(l)
```

---

## **9. Copier une liste**

Attention : l’opérateur `=` ne copie pas.

```
l2 = l    # mauvaise copie (même objet)
```

Copie propre :

```
l2 = l.copy()
```

ou

```
l2 = l[:]
```

---

## **10. Méthodes principales**

```
append(x)   → ajoute x en fin
pop()       → enlève le dernier
pop(i)      → enlève l’élément indice i
remove(x)   → enlève la 1ère occurrence de x
insert(i,x) → insère x à l’indice i
count(x)    → nb d’occurrences
index(x)    → indice de x
sort()      → trie (modifie)
reverse()   → inverse l’ordre
```

---

## **11. Opérations utiles**

Concaténation :

```
l1 + l2
```

Répétition :

```
l * 3
```

Slicing (tranches) :

```
l[2:5]
l[:3]
l[3:]
l[::2]
```

---

## **12. Valeurs spéciales**

Liste vide :

```
[]
```

Tester vide :

```
len(l) == 0
```

ou

```
if not l:
    ...
```

---

## **13. Erreurs fréquentes**

* `IndexError` → indice trop grand
* `ValueError` → remove(x) ou index(x) si x absent
* Copier une liste avec `=`
* Oublier que `sort()` modifie la liste directement

---

## **14. Exemple complet**

```
l = [5, 3, 9, 1]

print(len(l))
l.append(7)
l.remove(3)
l.sort()
print(l[0])
```

---

## **15. Complexité (très bref)**

```
append      → O(1)
pop()       → O(1)
remove(x)   → O(n)
index(x)    → O(n)
in          → O(n)
sort()      → O(n log n)
```
