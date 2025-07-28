# Fusion de listes

## Enoncé
On souhaite écrire le corps de la fonction `fusion` qui prend en paramètres deux listes d'entiers `first_list, second_list` triées par ordre croissant et les fusionne en une seule liste triée.

## Exemple de tests
```
>>> fusion([1, 6, 10], [0, 7, 8, 9])
[0, 1, 6, 7, 8, 9, 10]

>>> fusion([1, 6, 10], [])
[1, 6, 10]

>>> fusion([], [0, 7, 8, 9])
[0, 7, 8, 9]
```

## Réponse attendue

```python
res = []
cpt = 0
cpt2 = 0

while len(first_list) > cpt and len(second_list) > cpt2:
	if first_list[cpt] <= second_list[cpt2]:
		res.append(first_list[cpt])
		cpt += 1
	else:
		res.append(second_list[cpt2])
		cpt2 += 1

if len(first_list) > cpt:
	for i in range(cpt, len(first_list)):
		res.append(first_list[i])
            
if len(second_list) > cpt2:
	for i in range(cpt2, len(second_list)):
		res.append(second_list[i])
            
return res
```