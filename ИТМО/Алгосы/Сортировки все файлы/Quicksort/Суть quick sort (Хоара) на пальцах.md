1. Берем support element == элементу в середине массива
2. Индекс i идет слева от support element, индекс j идет справа от support element. Идем до тех пор, пока не найдем arr{ i } > support element и arr{ j } < support element
4. Если arr{ i } > arr{ j }, то свапаем элементы, затем i++, j--

![[Pasted image 20220930222404.png]]