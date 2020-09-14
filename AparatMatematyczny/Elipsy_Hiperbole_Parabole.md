# Elipsy, Hiperbole, Parabole

Witaj w kolejnym matematycznym artykule na Inżynierskim Primerze. Dziś w menu temat, który wprawdzie **potęgą** nie dorównuje rachunkowi różniczkowemu, jest jednak przydatnym narzędziem do wizualizacji. Pozwoli Ci on nie tylko na łatwiejsze wyobrażenie wykresów niektórych funkcji, lecz także na *zmatematyzowanie* pewnych wykresów lub figur, czyli wyrażenie ich za pomocą równania; nie wspominając już o wrażeniu jakie zrobisz na studentkach/studentach z roku (tak na prawdę tylko na ćwiczeniowcu) swoją ponadprogramową płynnością w matematycznym żargonie!

Chcesz być najpopularniejszym (najbardziej znienawidzonym) freshmanem na wydziale? Chcesz, aby wszyscy podziwiali (kogo próbujesz oszukać) Twoją matematyczną wiedzę (more like random trivia tbh)? Czy chcesz uniknąć publicznego upokorzenia przez nauczyciela algebry? Jesteś w dobrym miejscu! Z tej strony ja, Twój @admin *RibsonZ*, a to "Elipsy, Hiperbole, Parabole"!

## Krzywe Stożkowe

Zestawienie krzywych w tym artykule nie jest przypadkowe. Są one wszystkie krzywymi stożkowymi. Krzywa stożkowa jest to zbiór punktów przecięcia płaszczyzny i powierzchni stożkowej. Poniższe grafiki ilustrują to pojęcie.  [[4]](#[5])[[5]](#[6])
![krzywe stożkowe](Elipsy_Hiperbole_Parabole_files/krzywe_stozkowe.svg)

![Conic sections with plane](Elipsy_Hiperbole_Parabole_files/Conic_sections_with_plane.svg)

## Szybki Recap

Zanim przejdziemy do nowych, ekscytujących rzeczy, wykorzystam Twój chwilowy dopaminowy boost koncentracji do przypomnienia pewnych podstaw. 

### Parabola

The oldest wykres in the book. Pierwsza kochanka. 
<p align="center"> <img alt="$$ y = x^2 $$" src="https://render.githubusercontent.com/render/math?math=y%20%3D%20x%5E2"/> </p>


```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(-5,5,50)
y = x**2

plt.plot(x,y)
plt.grid()
plt.show()
```


![png](Elipsy_Hiperbole_Parabole_files/output_10_0.png)


Parabola to ogólniej wykres funkcji kwadratowej <img alt="$ y=ax^2+b $" src="https://render.githubusercontent.com/render/math?math=y%3Dax%5E2%2Bb"/>. Choć jest ona dość powszechna, być może wciąż jestem w stanie Cię zaskoczyć. Otóż wszystkie parabole, podobnie jak kwadraty i koła, są podobne!

Podobieństwo dwóch figur zachodzi wtedy, gdy jedną z nich można otrzymać przez skalowanie (zmianę rozmiaru), translację (zmianę położenia), rotację (zmianę orientacji) lub odbicie drugiej. W przypadku kwadratów jest to dość oczywiste, parabole wymagają jednak chwili refleksji, przynajmniej dla mnie. Mylącym jest fakt, iż przeważnie widzimy tylko wycinek paraboli, podczas gdy w rzeczywistości jest ona nieskończona.

Jeśli zaś chodzi o czapki urodzinowe, parabola powstaje w wyniku przecięcia powierzchni stożkowej płaszczyzną, która tworzy z osią stożka taki sam kąt, jak tworząca stożka.

### Okrąg

Klasyczna figura. Jeden z największych wynalazków ludzkości.
<p align="center"> <img alt="$$x^2+y^2=r^2$$" src="https://render.githubusercontent.com/render/math?math=x%5E2%2By%5E2%3Dr%5E2"/> </p>


```python
from matplotlib.patches import Circle

circle = Circle((0,0), radius = 1, fill = False)
fig, ax = plt.subplots(figsize=(6,6))
ax.add_artist(circle)

ax.set_xlim((-2,2))
ax.set_ylim((-2,2))
plt.grid()

plt.show()
```


![png](Elipsy_Hiperbole_Parabole_files/output_14_0.png)


Równanie okręgu jest właściwie twierdzeniem Pitagorasa. W przestrzeni Euklidesowej odległość między dwoma punktami <img alt="$A=(x_A,y_A), B=(x_B,y_B)$" src="https://render.githubusercontent.com/render/math?math=A%3D%28x_A%2Cy_A%29%2C%20B%3D%28x_B%2Cy_B%29"/> to długość przeciwprostokątnej trójkąta prostokątnego skonstruowanego z odcinków równoległych do osi układu współrzędnych, rozciągniętych między odpowiadającymi współrzędnymi punktów. Słowem:

<p align="center"> <img alt="$$r=\sqrt{(x_B-x_A)^2+(y_B-y_A)^2}$$" src="https://render.githubusercontent.com/render/math?math=r%3D%5Csqrt%7B%28x_B-x_A%29%5E2%2B%28y_B-y_A%29%5E2%7D"/> </p>

Czyli po podniesieniu do kwadratu mamy:

<p align="center"> <img alt="$$r^2=(x_B-x_A)^2+(y_B-y_A)^2$$" src="https://render.githubusercontent.com/render/math?math=r%5E2%3D%28x_B-x_A%29%5E2%2B%28y_B-y_A%29%5E2"/> </p>


Przypiszmy <img alt="$x=x_B, y=y_B$" src="https://render.githubusercontent.com/render/math?math=x%3Dx_B%2C%20y%3Dy_B"/> oraz <img alt="$x_S=x_A, y_S=y_A$" src="https://render.githubusercontent.com/render/math?math=x_S%3Dx_A%2C%20y_S%3Dy_A"/>. Wtedy ostatnie równanie przyjmuje postać:

<p align="center"> <img alt="$$(x-x_S)^2+(y-y_S)^2=r^2$$" src="https://render.githubusercontent.com/render/math?math=%28x-x_S%29%5E2%2B%28y-y_S%29%5E2%3Dr%5E2"/> </p>

Zbiór punktów <img alt="$(x,y)$" src="https://render.githubusercontent.com/render/math?math=%28x%2Cy%29"/> spełniających to równanie to zbiór punktów równoodległych od punktu <img alt="$(x_S,y_S)$" src="https://render.githubusercontent.com/render/math?math=%28x_S%2Cy_S%29"/>, czyli okrąg o środku w tym punkcie oraz promieniu <img alt="$r$" src="https://render.githubusercontent.com/render/math?math=r"/>. Aby uzyskać równanie powyżej wykresu, wystarczy przyjąć za <img alt="$(x_S,y_S)$" src="https://render.githubusercontent.com/render/math?math=%28x_S%2Cy_S%29"/> punkt <img alt="$(0,0)$" src="https://render.githubusercontent.com/render/math?math=%280%2C0%29"/>.

Nawiązując ponownie do czapek, okrąg powstaje w wyniku przecięcia powierzchni stożkowej płaszczyzną prostopadłą do osi stożka.

## Hiperbola

Słowo pochodzi z greki: "ὑπερβολή" - "hyperbolḗ": „przerzucenie; przesada”. Fundamentem hiperboli są dwa wybrane punkty przestrzeni, zwane ogniskami. Hiperbolą nazywamy zbiór punktów płaszczyzny o równym module różnicy odległości od ognisk.

Jako krzywa stożkowa powstaje ona z przecięcia powierzchni stożkowej płaszczyzną nachyloną do osi pod kątem mniejszym niż tworząca. W wyniku tego przecina tę powierzchnię dwukrotnie, tworząc osobne ramiona.

A jak ona wygląda? O tak:


```python
x = np.linspace(1e-1, 5, 50)
y = 1/x

plt.plot(-x,-y, color='blue')
plt.plot(x,y, color='blue')
plt.grid()
plt.show()
```


![png](Elipsy_Hiperbole_Parabole_files/output_18_0.png)


To hiperbola znana nam od lat jako wykres funkcji 

<p align="center"> <img alt="$$y=\frac{1}{x}$$" src="https://render.githubusercontent.com/render/math?math=y%3D%5Cfrac%7B1%7D%7Bx%7D"/> </p>

Ale istnieje również inne równanie hiperboli, mianowicie:

<p align="center"> <img alt="$$\frac{x^2}{a^2}-\frac{y^2}{b^2}=1$$" src="https://render.githubusercontent.com/render/math?math=%5Cfrac%7Bx%5E2%7D%7Ba%5E2%7D-%5Cfrac%7By%5E2%7D%7Bb%5E2%7D%3D1"/> </p>

Zajmiemy się jego wyprowadzeniem.


```python
# hiperbola o ogniskach (5,0) i (-5,0) oraz wierzchołkach (3,0) i (-3,0)
x = np.linspace(3, 8, 30)
y = np.sqrt((16/9)*(x**2)-16)
plt.figure(figsize=(6,6))
plt.grid()
plt.plot(-x,-y, color='red')
plt.plot(-x,y, color='red')
plt.plot(x,-y, color='red')
plt.plot(x,y, color='red')
plt.scatter([-5,5],[0,0], color='green')
plt.scatter([-3,3],[0,0], color='blue')
plt.scatter([0,0],[-4,4], color='violet')
plt.show()
```


![png](Elipsy_Hiperbole_Parabole_files/output_22_0.png)


W pierwszej kolejności zdefiniujmy jednak kilka kluczowych elementów hiperboli. Już poprzednio wspominaliśmy o ogniskach, które leżą u podstaw definicji naszej krzywej. Powtórzmy jednak dla ścisłości:
1. Ogniska - takie punkty płaszczyzny, że moduł różnicy odległości tych punktów od punktów hiperboli jest stały. Odległość między ogniskami określimy jako <img alt="$2c$" src="https://render.githubusercontent.com/render/math?math=2c"/>. (kolor zielony)
2. Wierzchołki - punkty należące do hiperboli, leżące na osi wyznaczonej przez jej ogniska; to także dwa leżące najbliżej siebie punkty pochodzące z przeciwnych ramion. Odległość między nimi zdefiniujmy jako <img alt="$2a$" src="https://render.githubusercontent.com/render/math?math=2a"/>. (kolor niebieski)
3. Wierzchołki urojone - punkty leżące na osi urojonej (symetralnej odcinka między ogniskami), leżące w odległości <img alt="$b$" src="https://render.githubusercontent.com/render/math?math=b"/> od punktu przecięcia osi, gdzie <img alt="$b^2=c^2-a^2$" src="https://render.githubusercontent.com/render/math?math=b%5E2%3Dc%5E2-a%5E2"/>. (kolor fioletowy)

Dobre wytłumaczenie elementów hiperboli można znaleźć na poniższej stronie internetowej. Zawiera ona również wyprowadzenie równania. Jest jednak anglojęzyczna.
https://courses.lumenlearning.com/collegealgebra2017/chapter/introduction-the-hyperbola/

Powiedzmy jeszcze parę słów o naszej hiperboli. Jej osie pokrywają się z osiami kartezjańskiego układu współrzędnych, jej ogniska leżą w punktach <img alt="$(\pm c,0)$" src="https://render.githubusercontent.com/render/math?math=%28%5Cpm%20c%2C0%29"/>, jej wierzchołki zaś w punktach <img alt="$(\pm a,0)$" src="https://render.githubusercontent.com/render/math?math=%28%5Cpm%20a%2C0%29"/>. W rezultacie jej wierzchołki urojone znajdą się w punktach <img alt="$(0, \pm b)$" src="https://render.githubusercontent.com/render/math?math=%280%2C%20%5Cpm%20b%29"/>

**No to jazda.**

Definicja: moduł różnicy odległości od wierzchołków jest stały. Jaka to wartość? Taka sama dla wszystkich punktów, w tym wierzchołków. A jaka jest dla np. prawego wierzchołka?

<p align="center"> <img alt="$$|(c-a)-(a+c)|=2a$$" src="https://render.githubusercontent.com/render/math?math=%7C%28c-a%29-%28a%2Bc%29%7C%3D2a"/> </p>

Zapisujemy tę definicję:

<p align="center"> <img alt="$$|\sqrt{(x-c)^2+(y-0)^2}-\sqrt{(x-(-c))^2+(y-0)^2}|=2a$$" src="https://render.githubusercontent.com/render/math?math=%7C%5Csqrt%7B%28x-c%29%5E2%2B%28y-0%29%5E2%7D-%5Csqrt%7B%28x-%28-c%29%29%5E2%2B%28y-0%29%5E2%7D%7C%3D2a"/> </p>

Kwadrat obustronnie:

<p align="center"> <img alt="$$(x-c)^2+y^2+(x+c)^2+y^2-2\sqrt{(x-c)^2+y^2}\sqrt{(x+c)^2+y^2}=4a^2$$" src="https://render.githubusercontent.com/render/math?math=%28x-c%29%5E2%2By%5E2%2B%28x%2Bc%29%5E2%2By%5E2-2%5Csqrt%7B%28x-c%29%5E2%2By%5E2%7D%5Csqrt%7B%28x%2Bc%29%5E2%2By%5E2%7D%3D4a%5E2"/> </p>

Izoluję pierwiastek po jednej stronie równania, rozwijam kwadraty:

<p align="center"> <img alt="$$2x^2+2y^2-4a^2+2c^2=2\sqrt{((x-c)^2+y^2)((x+c)^2+y^2)}$$" src="https://render.githubusercontent.com/render/math?math=2x%5E2%2B2y%5E2-4a%5E2%2B2c%5E2%3D2%5Csqrt%7B%28%28x-c%29%5E2%2By%5E2%29%28%28x%2Bc%29%5E2%2By%5E2%29%7D"/> </p>

Dzielę przez 2:

<p align="center"> <img alt="$$x^2+y^2-2a^2+c^2=\sqrt{((x-c)^2+y^2)((x+c)^2+y^2)}$$" src="https://render.githubusercontent.com/render/math?math=x%5E2%2By%5E2-2a%5E2%2Bc%5E2%3D%5Csqrt%7B%28%28x-c%29%5E2%2By%5E2%29%28%28x%2Bc%29%5E2%2By%5E2%29%7D"/> </p>

Podnoszę do kwadratu:

<p align="center"> <img alt="$$x^4+y^4+4a^4+c^4+2x^2y^2-4a^2x^2+2c^2x^2-4a^2y^2+2c^2y^2-4a^2c^2=((x-c)^2+y^2)((x+c)^2+y^2)$$" src="https://render.githubusercontent.com/render/math?math=x%5E4%2By%5E4%2B4a%5E4%2Bc%5E4%2B2x%5E2y%5E2-4a%5E2x%5E2%2B2c%5E2x%5E2-4a%5E2y%5E2%2B2c%5E2y%5E2-4a%5E2c%5E2%3D%28%28x-c%29%5E2%2By%5E2%29%28%28x%2Bc%29%5E2%2By%5E2%29"/> </p>

Wymnażam prawą stronę:

<p align="center"> <img alt="$$x^4+y^4+4a^4+c^4+2x^2y^2-4a^2x^2+2c^2x^2-4a^2y^2+2c^2y^2-4a^2c^2=(x^2-c^2)^2+y^2(x+c)^2+y^2(x-c)^2+y^4$$" src="https://render.githubusercontent.com/render/math?math=x%5E4%2By%5E4%2B4a%5E4%2Bc%5E4%2B2x%5E2y%5E2-4a%5E2x%5E2%2B2c%5E2x%5E2-4a%5E2y%5E2%2B2c%5E2y%5E2-4a%5E2c%5E2%3D%28x%5E2-c%5E2%29%5E2%2By%5E2%28x%2Bc%29%5E2%2By%5E2%28x-c%29%5E2%2By%5E4"/> </p>

Rozwijam prawą stronę w celu skrócenia:

<p align="center"> <img alt="$$x^4+y^4+4a^4+c^4+2x^2y^2-4a^2x^2+2c^2x^2-4a^2y^2+2c^2y^2-4a^2c^2=x^4+c^4-2c^2x^2+2x^2y^2+2c^2y^2+y^4$$" src="https://render.githubusercontent.com/render/math?math=x%5E4%2By%5E4%2B4a%5E4%2Bc%5E4%2B2x%5E2y%5E2-4a%5E2x%5E2%2B2c%5E2x%5E2-4a%5E2y%5E2%2B2c%5E2y%5E2-4a%5E2c%5E2%3Dx%5E4%2Bc%5E4-2c%5E2x%5E2%2B2x%5E2y%5E2%2B2c%5E2y%5E2%2By%5E4"/> </p>

I skaracam:

<p align="center"> <img alt="$$4a^4-4a^2x^2+2c^2x^2-4a^2y^2-4a^2c^2=-2c^2x^2$$" src="https://render.githubusercontent.com/render/math?math=4a%5E4-4a%5E2x%5E2%2B2c%5E2x%5E2-4a%5E2y%5E2-4a%5E2c%5E2%3D-2c%5E2x%5E2"/> </p>

Izoluję <img alt="$x$" src="https://render.githubusercontent.com/render/math?math=x"/> i <img alt="$y$" src="https://render.githubusercontent.com/render/math?math=y"/>:

<p align="center"> <img alt="$$x^2(4c^2-4a^2)-y^2(4a^2)=4a^2c^2-4a^4$$" src="https://render.githubusercontent.com/render/math?math=x%5E2%284c%5E2-4a%5E2%29-y%5E2%284a%5E2%29%3D4a%5E2c%5E2-4a%5E4"/> </p>

Podstawiam <img alt="$c^2=a^2+b^2$" src="https://render.githubusercontent.com/render/math?math=c%5E2%3Da%5E2%2Bb%5E2"/>:

<p align="center"> <img alt="$$x^2(4a^2+4b^2-4a^2)-y^2(4a^2)=4a^4+4a^2b^2-4a^4$$" src="https://render.githubusercontent.com/render/math?math=x%5E2%284a%5E2%2B4b%5E2-4a%5E2%29-y%5E2%284a%5E2%29%3D4a%5E4%2B4a%5E2b%5E2-4a%5E4"/> </p>

<p align="center"> <img alt="$$x^2(4b^2)-y^2(4a^2)=4a^2b^2$$" src="https://render.githubusercontent.com/render/math?math=x%5E2%284b%5E2%29-y%5E2%284a%5E2%29%3D4a%5E2b%5E2"/> </p>

Dzielę obustronnie przez prawą stronę:

<p align="center"> <img alt="$$\frac{4b^2x^2}{4a^2b^2}-\frac{4a^2y^2}{4a^2b^2}=1$$" src="https://render.githubusercontent.com/render/math?math=%5Cfrac%7B4b%5E2x%5E2%7D%7B4a%5E2b%5E2%7D-%5Cfrac%7B4a%5E2y%5E2%7D%7B4a%5E2b%5E2%7D%3D1"/> </p>

<p align="center"> <img alt="$$\frac{x^2}{a^2}-\frac{y^2}{b^2}=1$$" src="https://render.githubusercontent.com/render/math?math=%5Cfrac%7Bx%5E2%7D%7Ba%5E2%7D-%5Cfrac%7By%5E2%7D%7Bb%5E2%7D%3D1"/> </p>

Eleganckie równanie eleganckiej krzywej.

## Elipsa

Gdy mowa o hiperboli, nie może zabraknąć także i elipsy. Jest ona rezultatem przecięcia powierzchni stożkowej oraz płaszczyzny nachylonej do osi stożka pod kątem większym niż kąt nachylenia tworzącej. Jej szczególnym przypadkiem jest okrąg.

Mikołaj Kopernik postulował, że planety poruszają się po okręgach. Johannes Kepler przyjrzał się orbitom nieco dokładniej i stwierdził, iż są one eliptyczne. Elipsa to zatem bardzo ważna krzywa.

Podobnie jak hiperbola, elipsa opiera się na dwóch punktach zwanych ogniskami. Jest ona zbiorem punktów, których **suma** odległości od ognisk jest równa pewnej stałej. Elipsa posiada (przynajmniej) dwie osie symetrii, (typowo) jedną dłuższą i jedną krótszą. Wzór elipsy o środku w punkcie <img alt="$(0,0)$" src="https://render.githubusercontent.com/render/math?math=%280%2C0%29"/>, o "poziomej" osi długości <img alt="$2a$" src="https://render.githubusercontent.com/render/math?math=2a"/> oraz o "pionowej" osi długości <img alt="$2b$" src="https://render.githubusercontent.com/render/math?math=2b"/> przyjmuje postać:

<p align="center"> <img alt="$$\frac{x^2}{a^2}+\frac{y^2}{b^2}=1$$" src="https://render.githubusercontent.com/render/math?math=%5Cfrac%7Bx%5E2%7D%7Ba%5E2%7D%2B%5Cfrac%7By%5E2%7D%7Bb%5E2%7D%3D1"/> </p>

Wzór jest bardzo podobny do wzoru hiperboli, choć krzywe wyglądają kompletnie inaczej. Niemniej mają bardzo podobne elementy konstrukcyjne, takie jak ogniska czy wierzchołki. Wyprowadziłbym i ten wzór, ale perspektywa ponownego rozpisywania tych działań w LaTeX'u budzi we mnie odrazę. Zlecam więc to zadanie Tobie, w charakterze ćwiczenia ( tylko wyprowadzenie, nie rozpisanie go w LaTeX'u; tego nie życzyłbym nawet największemu wrogowi). 

Tak oto elipsa prezentuje się w matplotlibie:


```python
# elipsa o wierzchołkach w punktach (-5,0), (5,0), (0,-4), (0,4)
x = np.linspace(-5, 5, 60)
y = np.sqrt(-(16/25)*(x**2)+16)
plt.figure(figsize=(6,6))
plt.grid()
# plt.plot(-x,-y, color='red')
# plt.plot(-x,y, color='red')
plt.plot(x,-y, color='red')
plt.plot(x,y, color='red')
plt.gca().set_aspect('equal', adjustable='box')
plt.show()
```


![png](Elipsy_Hiperbole_Parabole_files/output_31_0.png)


Jako further reading dla płynnych w angielskim ponownie polecam materiały Lumen Learning:
https://courses.lumenlearning.com/collegealgebra2017/chapter/introduction-the-ellipse/

## Podsumowanie

Elipsy są wszędzie. Hiperbole też się zdarzają. Znałeś ich kształt, teraz znasz także ich analityczne równania i sowizdrzalskie powiązania ze stożkiem. Mam nadzieję, że dzięki temu artykułowi, gdy w czasie swej inżynierskiej przygody napatoczysz się na którąś z powyżej omówionych krzywych, na Twojej twarzy pojawi się cwaniacki uśmieszek mówiący: *haha, znam to.*

## Bibliografia

<a id="[1]">[1] </a>[Wikipedia: Krzywa stożkowa](https://pl.wikipedia.org/wiki/Krzywa_sto%C5%BCkowa)

<a id="[2]">[2] </a>[Lumen Learning Introduction: The Hyperbola](https://courses.lumenlearning.com/collegealgebra2017/chapter/introduction-the-hyperbola/)

<a id="[3]">[3] </a>[Wikipedia: Hyperbola](https://en.wikipedia.org/wiki/Hyperbola)

<a id="[4]">[4] </a>[Ilustracja: Conic sections with plane,](https://de.wikipedia.org/wiki/Datei:Conic_sections_with_plane.svg)
under [Creative-Commons License](https://creativecommons.org/licenses/by/3.0/deed.de)

<a id="[5]">[5] </a>[Ilustracja: Krzywe Stożkowe](https://commons.wikimedia.org/wiki/File:Krzywe_sto%C5%BCkowe.svg)

<a id="[6]">[6] </a>[Lumen Learning Introduction: The Ellipse](https://courses.lumenlearning.com/collegealgebra2017/chapter/introduction-the-ellipse/)
