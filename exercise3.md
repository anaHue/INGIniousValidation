# Minimum

## Enoncé
Supposez que les variables a, b et c contiennent un nombre naturel.

Ecrire un fragment de code qui assigne à la variable minima le plus petit de ces nombres.

## Exemple de tests
```
a, b, c = 1, 2, 3 -> minima=1
a, b, c = 1, 0, 3 -> minima=0
a, b, c = 1, 2, -3 -> minima=-3
```

## Réponse attendue

```python
if a < b and a < c:
    minima = a
elif b < a and b < c:
    minima = b
else:
    minima = c
```