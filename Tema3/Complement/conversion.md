# 🔢 Convertir a hexadecimal

Para poder entender como pasar a base hexadecimal, debemosentender como usamos y entendemos cómo se usa sistema decimal.
EL sistema decimal recordamos que consta de la composición de 10 cifras {0 ,1 , 2, 3, 4, 5, 6, 7, 8, 9}.

... , Centenas + Decenas + Unidades

Cuando empezamos desde ls unidades y completamos todas la cifras, se reinicia volviendo al 0 y se añade la siguiente cifra en la posición superior de las decenas.

$$
n \cdot 10^{n} + ... + n \cdot 10^{5} + n \cdot 10^{4} + n \cdot 10^{3} + n \cdot 10^{2} + n \cdot 10^{1} + n \cdot 10^{0}
$$

* En unidades 10 elevado a 0 es siempre 1. Por lo que si tenemos 3 x 10 ^0 = 3 x 1 = 3 unidades.
  
$$
1 \cdot 10^{3} + 8 \cdot 10^{2} + 4 \cdot 10^{1} + 3 \cdot 10^{0}
$$

$$
1000 + 800 + 40 + 3 = 1843
$$

* Cuando completamos tas las cifras en cada bloque (unidad, decenas y centenas, se le añade uno al bloque superior) y se reinicia a cero.

```
009 -> 010
```

---

## 🔢 Hexadecimal

Pasa lo mismo que con decial pero hasta 16 en vez de 10.
```
Decimal:     0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15
Hexadecimal: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9,  a,  b,  c,  d,  e,  f
```


$$
n \cdot 16^{n} + ... + n \cdot 16^{5} + n \cdot 16^{4} + n \cdot 16^{3} + n \cdot 16^{2} + n \cdot 16^{1} + n \cdot 16^{0}
$$

*Ejemplo: Pasar 11c a decimal*


```
1 x 16^2 + 1 x 16^1 + c x 16^0
256 + 16 + c
256 + 16 + 12 = 284
```

---

Para pasar de decimal (base 10) a hexadecimal (base 16) se usa siempre el mismo proceso: dividir entre 16 y quedarse con los restos.

*Ejemplo: Pasar 345 a hexadecimal*

```
345 ÷ 16 = 21  resto 9
21 ÷ 16 = 1    resto 5
1 ÷ 16 = 0     resto 1

Resultado: 159
```
*Ejemplo: Pasar 986 a hexadecimal*
```
986 ÷ 16 = 61   resto 10 → A
61 ÷ 16 = 3     resto 13 → D
3 ÷ 16 = 0      resto 3
```
