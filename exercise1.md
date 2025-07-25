# Equations du second degré

## Enoncé
Les équations du second degré sont des équations de la forme suivante:

$ax^2+bx+c=0$

avec a≠0

Pour déterminer si l'équation dispose d'une solution, on calcule le nombre $ρ=b^2−4ac$.

Implementer le corps de la fonction `calculate_rho(a, b, c)` pour qu'elle retourne la valeur de $ρ$ dans une variable nommée `roh`.

## Exemple de tests
```
calculate_roh(1, 2, 2) -> -4
calculate_roh(1, 2, 1) -> 0
calculate_roh(1, -5, 4) -> 9
```

## Réponse attendue

```python
roh = b**b - 4*a*c
```