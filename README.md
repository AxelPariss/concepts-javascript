# Call Stack

En JavaScript, la call Stack (="Pile d'appels") décrit l'imbrication des contextes pour un script JS.
**La call stack évolue tout au long de l'exuction du script.**

## La stack étape par étape
Un dessin vaut mieux qu'un long discours, on va suivre l'évolution de la stack pour le code suivant :
```js
function bar(x){
  return return x + 20;
}

console.log(bar(10)); // Affiche 30
```
### 1. État de la stack
| call stack |
-------
| `main()` |

> Quand un script ce lance, il est **obligatoirement** executé dans la stack appelée _'main()'_.

### 2. État de la stack
| call stack |
-------
| `console.log(bar(10))` |
| `main()` |

> Ici, comme `console.log(bar(10))` est executé dans la _'main()'_ stack (dans le contexte global), alors on `console.log(bar(10))` se retrouve **au dessus** de `main()`dans la stack (D'où son nom "stack" = "empilement")

### 3. État de la stack
| call stack |
-------
| `bar(10)` |
| `console.log(bar(10))` |
| `main()` |

> Même principe qu'à l'étape 2 : `bar(10)` est executé dans la "stack" du `console.log()`. Donc `bar(10)` se retrouve au dessus !

### 4. État de la stack
| call stack |
-------
| `console.log(bar(10))` |
| `main()` |

> Une fois que `bar(10)` est executé, la fonction renvoie le résultat, **on sort donc de la stack de `bar(10)`**. La stack actuelle est donc `console.log(bar(10))`

### 5. État de la stack
| call stack |
-------
| `main()` |

> Même principe qu'à l'étape 4 : `console.log(bar(10))` est executé, la fonction affiche le résultat retourné précédemment par la fonction `bar()`, **on sort donc de la stack de `console.log(bar(10))`**. La stack actuelle redevient `main()`

### 6. État de la stack
| call stack |
-------
| | 

> Le script a fini de s'executer en totalité, la stack `main()` disparait.