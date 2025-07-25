# Différence de compteur

## Enoncé
La méthode `diff_count(lst)` retourne le nombre d'éléments différents contenus dans la liste lst.

Fournissez le corps de cette méthode.

## Exemple de tests
```
diff_count([3, 5, 3]) -> 2
diff_count([0, 0, 0, 0, 0]) -> 1
diff_count([]) -> 0
```

## Réponse attendue

```python
unique = []
for i in lst:
	if i not in unique:
		unique.append(i)
return len(unique)
```