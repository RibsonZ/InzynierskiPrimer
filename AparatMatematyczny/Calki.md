# Całki 

Gdy przyjdziesz w październiku na swoje wymarzone studia inżynierskie, możesz mieć złudzenia, że program będzie logicznie rozłożony. **To normalne.** Może Ci się wydawać, że całki zostaną wprowadzone na analizie matematycznej, a następnie wykorzystane na pozostałych przedmiotach inżynierskich.

## "Reality is often disappointing."

*In a perfect uczelnia, men like **dziekan** would not exist. But this is not a perfect uczelnia*. W rzeczywistości prowadzący na pierwszych zajęciach spyta Was, czy umiecie całkować, pomimo że od lat odpowiedź jest zawsze przecząca. W programie jego przedmiotu rachunek całkowy to tzw. prerequisite, więc będziesz zmuszony nauczyć się go z eTrapeza, żeby nie oblać. A gdy całki raczą się pojawić na analizie pół roku później (przy dobrych wiatrach), to już będzie musztarda po obiedzie. **I'm sorry, little one.**

**Chyba że** zdecydujesz się przeczytać ten artykulik do końca i poznasz **jeden prosty sposób** na zrozumienie całki. Poniżej zawarłem **potężne intuicje**, które pozwoliły mi zaliczyć wszystkie przedmioty inżynierskie z pierwszego roku oraz tzw. anala :~D *z latającymi kolorami*.

## Całek uczy się w gimnazjum.

Choć możesz sobie nie zdawać z tego sprawy, proste całki są Ci znane z gimnazjalnych lekcji fizyki. Exhibit A:  
*Samochód jedzie po prostej drodze z prędkością <img alt="$v=80km/h$" src="https://render.githubusercontent.com/render/math?math=v%3D80km/h"/> przez czas <img alt="$t=1h$" src="https://render.githubusercontent.com/render/math?math=t%3D1h"/>.  
Jaką drogę przejedzie?*


```python
v = 80
t = 1
s = v * t
print(f"Samochód przejedzie drogę s = {s}km.")
```

    Samochód przejedzie drogę s = 80km.
    


Wykorzystaliśmy tu pewne uproszczenie. Założyliśmy stałą prędkość pojazdu, w którym to przypadku zachodzi równość:

<p align="center"> <img alt="$$ s = vt $$" src="https://render.githubusercontent.com/render/math?math=s%20%3D%20vt"/> </p>

To nic innego niż szczególny przypadek całki. Prędkość to pochodna drogi po czasie, a zatem droga jest całką prędkości po czasie (kinda). Jeśli prędkość jest stałą rzeczywistą, to jej całką będzie funkcja liniowa dobrze znanej postaci:

<p align="center"> <img alt="$$ y = ax + b $$" src="https://render.githubusercontent.com/render/math?math=y%20%3D%20ax%20%2B%20b"/> </p>

lub jak w tym przypadku:

<p align="center"> <img alt="$$ r = vt + r_0 $$" src="https://render.githubusercontent.com/render/math?math=r%20%3D%20vt%20%2B%20r_0"/> </p>

Ale zaraz, o co chodzi z <img alt="$r$" src="https://render.githubusercontent.com/render/math?math=r"/>? Przecież liczyliśmy <img alt="$s$" src="https://render.githubusercontent.com/render/math?math=s"/>. Wprowadziłem nowe oznaczenie <img alt="$r$" src="https://render.githubusercontent.com/render/math?math=r"/> dla *położenia* samochodu w układzie współrzędnych. Litera <img alt="$s$" src="https://render.githubusercontent.com/render/math?math=s"/> oznacza w tym przypadku *drogę*, czyli różnicę położeń <img alt="$r(t_0+1h) - r(t_0)$" src="https://render.githubusercontent.com/render/math?math=r%28t_0%2B1h%29%20-%20r%28t_0%29"/>.

Znając prędkość i różnicę czasu byliśmy w stanie określić drogę, ale co możemy powiedzieć o położeniu? Znamy jego zmienność, więc możemy określić różnicę między jego wartościami dla różnych chwil w czasie (argumentów), nie możemy natomiast powiedzieć wiele na temat jego bezwzględnej wartości w danej chwili <img alt="$t_0$" src="https://render.githubusercontent.com/render/math?math=t_0"/>. Do naszego zagadnienia pasuje nieskończenie wiele par położeń. Mogą to być kilometry 1 oraz 81, 64 i 144 lub 361 i 441. Tak długo jak różnica między nimi wynosi 80, pasują do *rodziny* rozwiązań. To *important idea* w całkach.


```python
for i in range(100):
    for j in range(i,100):
        if (j**2 - i**2 == 80):
            print(j**2, i**2)
# Yeah I wanted to make the numbers pretty.
```

    81 1
    144 64
    441 361
    

## Do całki przez pochodną.

Mając daną funkcję <img alt="$f(x)$" src="https://render.githubusercontent.com/render/math?math=f%28x%29"/>, przez operację *różniczkowania* otrzymujemy jej pochodną <img alt="$f'(x)$" src="https://render.githubusercontent.com/render/math?math=f%27%28x%29"/> lub <img alt="$\frac{df}{dx}(x)$" src="https://render.githubusercontent.com/render/math?math=%5Cfrac%7Bdf%7D%7Bdx%7D%28x%29"/>. Natomiast przez operację *całkowania* otrzymujemy jej funkcję pierwotną <img alt="$F(x)$" src="https://render.githubusercontent.com/render/math?math=F%28x%29"/>.

Zgodnie z definicją[[1]](#[1]):  

Funkcję <img alt="$F$" src="https://render.githubusercontent.com/render/math?math=F"/> nazywamy pierwotną funkcji <img alt="$f$" src="https://render.githubusercontent.com/render/math?math=f"/> na przedziale <img alt="$I$" src="https://render.githubusercontent.com/render/math?math=I"/>, jeżeli

<p align="center"> <img alt="$$\forall x \in I: F'(x)=f(x)$$" src="https://render.githubusercontent.com/render/math?math=%5Cforall%20x%20%5Cin%20I%3A%20F%27%28x%29%3Df%28x%29"/> </p>

Czyli dla każdego <img alt="$x$" src="https://render.githubusercontent.com/render/math?math=x"/> należącego do <img alt="$I$" src="https://render.githubusercontent.com/render/math?math=I"/> wartość pochodnej funkcji <img alt="$F$" src="https://render.githubusercontent.com/render/math?math=F"/> jest równa wartości funkcji <img alt="$f$" src="https://render.githubusercontent.com/render/math?math=f"/>.

A zatem w całkowaniu chodzi o znalezienie funkcji pierwotnych danej funkcji. **c00l beanz ;~D**, ale zanim zagłębimy się w całki, przypomnijmy sobie pochodne, bo w ten sposób możemy poznać **potężne intuicje**, które pozwolą na łatwe zrozumienie operacji całkowania i **zDeKlAsoWaNie pOzoStaŁyCh sTuDenTów nA ryNKu ParCy!!!!** 

<p align="center"> <img alt="$$f'(x_0)=\frac{df}{dx}(x_0)=\lim_{\Delta x\to 0}\frac{f(x_0+\Delta x)-f(x_0)}{\Delta x}$$" src="https://render.githubusercontent.com/render/math?math=f%27%28x_0%29%3D%5Cfrac%7Bdf%7D%7Bdx%7D%28x_0%29%3D%5Clim_%7B%5CDelta%20x%5Cto%200%7D%5Cfrac%7Bf%28x_0%2B%5CDelta%20x%29-f%28x_0%29%7D%7B%5CDelta%20x%7D"/> </p>

Powyżej znajduje się definicja pochodnej, czyli granica ilorazu różnicowego (to coś po prawej) w danym punkcie <img alt="$x_0$" src="https://render.githubusercontent.com/render/math?math=x_0"/>. Jest to stosunek przyrostu wartości funkcji do przyrostu wartości argumentu. Jeśli podzielimy przyrost funkcji przez przyrost argumentu otrzymamy stosunek - pochodną. A jeśli pomnożymy pochodną przez przyrost argumentu? ;-)

W liceum najczęściej używa się zapisu po lewej, z apostrofem. Na studiach w moim doświadczeniu wygodniejszy jest zapis środkowy, z <img alt="$df$" src="https://render.githubusercontent.com/render/math?math=df"/> i <img alt="$dx$" src="https://render.githubusercontent.com/render/math?math=dx"/>. Przez długi czas nie wiedziałem, co on właściwie oznacza. Co reprezentuje ta literka <img alt="$d$" src="https://render.githubusercontent.com/render/math?math=d"/>? Na analizie obiło mi się o uszy sformułowanie "operator", co wciąż było dla mnie dość enigmatyczne. Jednak gdy wreszcie doznałem olśnienia, zacząłem preferować tę postać, ponieważ wydaje mi się znacznie bardziej naturalna.

Stojąc samodzielnie <img alt="$dx$" src="https://render.githubusercontent.com/render/math?math=dx"/> jest różniczką, czyli nieskończenie małym (eng.infinitesimal /ˌɪnfɪnɪˈtɛsɪm(ə)l/) przyrostem, długością jednego punktu na osi liczbowej. I gdy używana jest jako operator czegokolwiek (różniczkowania czy też całkowania), warto jest zachować tę intuicję.

Granica ilorazu różnicowego to w końcu nic innego, niż iloraz granic różnic (przyrostów). Nasze <img alt="$f(x_0+\Delta x)-f(x_0)$" src="https://render.githubusercontent.com/render/math?math=f%28x_0%2B%5CDelta%20x%29-f%28x_0%29"/> w granicy to <img alt="$df$" src="https://render.githubusercontent.com/render/math?math=df"/>, a <img alt="$\Delta x$" src="https://render.githubusercontent.com/render/math?math=%5CDelta%20x"/> staje się <img alt="$dx$" src="https://render.githubusercontent.com/render/math?math=dx"/>. Osobno są "równe" zero, ale ich iloraz się zachowuje i odzwierciedla nachylenie stycznej do wykresu funkcji, czyli prędkość zmiany wartości funkcji w danym punkcie.

### Przykład 1: model uproszczony

Powróćmy do analogii samochodu poruszającego się z prędkością <img alt="$v(t)$" src="https://render.githubusercontent.com/render/math?math=v%28t%29"/> po jednowymiarowej drodze. Przyjmiemy pewien uproszczony przypadek, gdzie auto przyjmuje tylko dyskretne wartości prędkości, między którymi przechodzi natychmiastowo, z nieskończonym przyspieszeniem.

**Engineering Tip!**
1. Przy rozpatrywaniu różnych zagadnień warto używać najpierw uproszczonego modelu, aby uzyskać pewne intuicyjne zrozumienie problemu, a następnie stopniowo zwiększać jego złożoność przez bardziej wnikliwą analizę. Od ogółu do szczegółu. W pierwszym kroku powietrze nie istnieje, każdy płyn i gaz jest doskonały, a każda powierzchnia idealnie gładka.
2. Wartość dyskretna - wartość nieciągła, pojedyncza. Należąca do jakiegoś przeliczalnego (niekoniecznie policzalnego) zbioru, np. zbiór liczb całkowitych <img alt="$\mathbb{Z}$" src="https://render.githubusercontent.com/render/math?math=%5Cmathbb%7BZ%7D"/>


```python
import matplotlib.pyplot as plt
import numpy as np

x_0 = np.array([0, 1e-5, 1, 1+1e-5, 2, 2+1e-5, 3, 3+1e-5, 4, 4+1e-5, 5, 5+1e-5])
y_0 = np.array([0, 50, 50, 70, 70, 80, 80, 60, 60, 40, 40, 0])

fig, ax = plt.subplots()
ax.plot(x_0,y_0)

ax.set(xlabel='Czas [h]', ylabel='Prędkość [km/h]',
       title='Prędkość "idealnego" auta w funkcji czasu.')
ax.grid()

plt.show()
```


![png](Calki_files/output_21_0.png)


Nasze auto podróżuje z prędkością 50km/h przez pierwszą godzinę. Kolejną przebywa z prędkością 70km/h, 80 itd. Policzmy przebytą drogę, czyli różnicę między położeniem początkowym, a końcowym. To proste: jeśli auto przez godzinę jedzie z prędkością 50km/h, przejedzie 50km. Wystarczy posumować te odcinki czasowe i otrzymamy wynik.


```python
50 * (1 - 0) + 70 * (2 - 1) + 80 * (3 - 2) + 60 * (4 - 3) + 40 * (5 - 4)
```




    300



Otrzymany wynik to wynik całkowania funkcji prędkości po czasie. Choć operację tę rozumiemy dość intuicyujnie, kryje się w niej istota całkowania.

Dla każdego z tych godzinnych okresów prawdą jest, że:

<p align="center"> <img alt="$$v = \frac{\Delta r}{\Delta t}$$" src="https://render.githubusercontent.com/render/math?math=v%20%3D%20%5Cfrac%7B%5CDelta%20r%7D%7B%5CDelta%20t%7D"/> </p>
<p align="center"> <img alt="$$\Updownarrow$$" src="https://render.githubusercontent.com/render/math?math=%5CUpdownarrow"/> </p>
<p align="center"> <img alt="$$\Delta r = v \cdot \Delta t$$" src="https://render.githubusercontent.com/render/math?math=%5CDelta%20r%20%3D%20v%20%5Ccdot%20%5CDelta%20t"/> </p>

Czyli jeśli pomnożymy wartość pochodnej (<img alt="$v$" src="https://render.githubusercontent.com/render/math?math=v"/>) przez ten przyrost argumentu (<img alt="$\Delta t$" src="https://render.githubusercontent.com/render/math?math=%5CDelta%20t"/>), otrzymamy przyrost wartości funkcji pierwotnej (<img alt="$\Delta r$" src="https://render.githubusercontent.com/render/math?math=%5CDelta%20r"/>). Całka to suma wszystkich tych przyrostów wartości funkcji pierwotnej.

#### Engineering Tip!
3. Poniższy symbol <img alt="$\Sigma$" src="https://render.githubusercontent.com/render/math?math=%5CSigma"/> to wielka grecka litera sigma, oznaczająca sumę. Dolny indeks przy symbolu oznacza zmienną, po której będziemy iterować w kierunku limitu zawartego w indeksie górnym.

<p align="center"> <img alt="$$s=\sum_{i=1}^{5} \Delta r_i = \sum_{i=1}^{5} v_i \cdot \Delta t_i = v_1 \cdot \Delta t_1 + v_2 \cdot \Delta t_2 + v_3 \cdot \Delta t_3 + v_4 \cdot \Delta t_4 + v_5 \cdot \Delta t_5$$" src="https://render.githubusercontent.com/render/math?math=s%3D%5Csum_%7Bi%3D1%7D%5E%7B5%7D%20%5CDelta%20r_i%20%3D%20%5Csum_%7Bi%3D1%7D%5E%7B5%7D%20v_i%20%5Ccdot%20%5CDelta%20t_i%20%3D%20v_1%20%5Ccdot%20%5CDelta%20t_1%20%2B%20v_2%20%5Ccdot%20%5CDelta%20t_2%20%2B%20v_3%20%5Ccdot%20%5CDelta%20t_3%20%2B%20v_4%20%5Ccdot%20%5CDelta%20t_4%20%2B%20v_5%20%5Ccdot%20%5CDelta%20t_5"/> </p>

Jeszcze jedno: często mówi się o tym, że całka oznaczona równa jest polu pod wykresem funkcji. Właściwie czemu?  
Pole pod naszym wykresem możemy rozbić na 5 prostokątów. Wysokość każdego z nich to prędkość, a podstawa to różnica argumentów. Zatem chcąc zapisać wielkość tego pola, otrzymalibyśmy to samo równanie, co powyżej. *Easy peasy lemon squeezy.*

### Przykład 2: model rzeczywisty

Czas na bardziej realistyczny przykład. Tym razem nasz samochód będzie przyspieszał płynnie, ze skończonym przyspieszeniem i nieskończoną liczbą wartości prędkości. Na to wszyscy czekali, czas na big-boy całkę.


```python
x_1 = np.arange(0, 5, 0.01)
y_1 = 10*np.sin(np.pi*x_1) - 10*((x_1-2.5)**2) + 62.5
fig_1, ax_1 = plt.subplots()
ax_1.plot(x_1,y_1)
ax_1.set(xlabel='Czas [h]', ylabel='Prędkość [km/h]',
       title='Prędkość auta w funkcji czasu.')
ax_1.grid()
plt.show()
```


![png](Calki_files/output_28_0.png)


Przypomnijmy sobie pochodną. (Oznaczę równania gwiazdkami, popularna technika u wykładowców).

<p align="center"> <img alt="$$v=\frac{dr}{dt}(*) $$" src="https://render.githubusercontent.com/render/math?math=v%3D%5Cfrac%7Bdr%7D%7Bdt%7D%28%2A%29"/> </p>

Wzór ten wygląda bardzo podobnie do wzoru z przykładu 1, czyli:
<p align="center"> <img alt="$$v = \frac{\Delta r}{\Delta t} **) $$" src="https://render.githubusercontent.com/render/math?math=v%20%3D%20%5Cfrac%7B%5CDelta%20r%7D%7B%5CDelta%20t%7D%20%28%2A%2A%29"/> </p>

Bo wzór (\*\*) jest po prostu szczególnym przypadkiem wzoru (\*).

Przekształćmy (\*) tak samo, jak przekształciliśmy wcześniej (\*\*).
<p align="center"> <img alt="$${dr}=v\cdot dt$$" src="https://render.githubusercontent.com/render/math?math=%7Bdr%7D%3Dv%5Ccdot%20dt"/> </p>

A zatem różniczka <img alt="$dr$" src="https://render.githubusercontent.com/render/math?math=dr"/> (nieskończenie mały przyrost <img alt="$\Delta r$" src="https://render.githubusercontent.com/render/math?math=%5CDelta%20r"/>) jest równa iloczynowi wartości pochodnej <img alt="$v$" src="https://render.githubusercontent.com/render/math?math=v"/> i różniczki <img alt="$dt$" src="https://render.githubusercontent.com/render/math?math=dt"/> (nieskończenie małego przyrostu argumentu <img alt="$\Delta t$" src="https://render.githubusercontent.com/render/math?math=%5CDelta%20t"/>). Do sumowania dyskretnych wartości z przykładu 1 użyliśmy symbolu sumy, greckiej wielkiej litery sigma <img alt="$\Sigma$" src="https://render.githubusercontent.com/render/math?math=%5CSigma"/>. Do sumowania nieskończonej liczby nieskończenie małych przyrostów stosujemy symbol całki: <img alt="$\int$" src="https://render.githubusercontent.com/render/math?math=%5Cint"/>

> Wreszcie ten symbol. Behold its beauty: <img alt="$\int \int \int \int \int \int \int \int \int$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20%5Cint%20%5Cint%20%5Cint%20%5Cint%20%5Cint%20%5Cint%20%5Cint%20%5Cint"/>

Tym razem równanie drogi zapiszemy jako:

<p align="center"> <img alt="$$s=\int_{0}^{5}v(t) dt $$" src="https://render.githubusercontent.com/render/math?math=s%3D%5Cint_%7B0%7D%5E%7B5%7Dv%28t%29%20dt"/> </p>

Zapis ten można interpretować na następujące sposoby:
- Pole pod wykresem funkcji ograniczone prostymi t=0 i t=5 (gdzie pole poniżej osi Ox liczy się jako ujemne),
- Różnica wartości wybranej funkcji pierwotnej dla t=5 oraz t=0 (praktyczny sposób liczenia całek oznaczonych),  
- **Suma przyrostów (dowolnej) funkcji pierowtnej od dolnej granicy całkowania (u nas t=0) do górnej (t=5) (fundamentalne znaczenie całki oznaczonej).**

Nasza funkcja opowiada nam historię zmiany jej funkcji pierwotnych.

## Całka nieoznaczona

*Z "Analiza Matematyczna 1"* [[1]](#[1]):

Niech <img alt="$F$" src="https://render.githubusercontent.com/render/math?math=F"/> będzie pierwotną funkcji <img alt="$f$" src="https://render.githubusercontent.com/render/math?math=f"/> na przedziale <img alt="$I$" src="https://render.githubusercontent.com/render/math?math=I"/>. Całką nieoznaczoną funkcji <img alt="$f$" src="https://render.githubusercontent.com/render/math?math=f"/> na przedziale <img alt="$I$" src="https://render.githubusercontent.com/render/math?math=I"/> nazywamy zbiór funkcji

<p align="center"> <img alt="$$\{F(x)+C: C\in \mathbb{R}\}$$" src="https://render.githubusercontent.com/render/math?math=%5C%7BF%28x%29%2BC%3A%20C%5Cin%20%5Cmathbb%7BR%7D%5C%7D"/> </p>

Całkę nieoznaczoną funkcji <img alt="$f$" src="https://render.githubusercontent.com/render/math?math=f"/> oznaczamy przez <img alt="$\int f(x)dx$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20f%28x%29dx"/>.


Czyli całka nieoznaczona to zbiór funkcji pierwotnych danej funkcji. Najczęściej będziemy poszukiwać tej, której wyraz wolny <img alt="$C$" src="https://render.githubusercontent.com/render/math?math=C"/> jest równy 0, ponieważ na takich najłatwiej się operuje, a są one równie dobrymi funkcjami pierwotnymi jak te z niezerowymi wyrazami wolnymi.

Całki nieoznaczone są ściśle związane z oznaczonymi, pozwalają mianowicie na ich łatwe policzenie. W przykładzie 1 dokładnie znaliśmy wszystkie dyskretne prędkości, więc problem policzenia całki był trywialny. Mając jednak do czynienia z funkcją ciągłą i niestałą nie mamy możliwości sumowania pól prostokątów, ponieważ mają nieskończenie małą szerokość i jest ich nieskończenie wiele. Wiemy natomiast, że zmienność funkcji pierwotnej jest dyktowana przez naszą funkcję prędkości. Znając funkcję pierwotną, wystarczyłoby wziąć jej wartość w punkcie startowym (czasie <img alt="$t_0$" src="https://render.githubusercontent.com/render/math?math=t_0"/>) i odjąć ją od wartości w punkcie końcowym (czasie <img alt="$t_k$" src="https://render.githubusercontent.com/render/math?math=t_k"/>). Całkowita zmiana wartości funkcji pierwotnej między tymi argumentami jest przecież właśnie naszą poszukiwaną sumą nieskończoności nieskończenie małych zmian! A jak odnaleźć funkcję pierwotną?

Należy zadać fundamentalne pytanie:  
**Pochodną jakiej funkcji jest moja funkcja?**

### Przykład 3: całka nieoznaczona wielomianu

<img alt="$f(x)=x^3+2x$" src="https://render.githubusercontent.com/render/math?math=f%28x%29%3Dx%5E3%2B2x"/> 

<img alt="$\int f(x)dx = ?$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20f%28x%29dx%20%3D%20%3F"/>  

Pochodna sumy to suma pochodnych, więc ta sama zasada aplikuje się do całek. Rozpatrzymy oba składniki osobno.
Najpierw <img alt="$2x$" src="https://render.githubusercontent.com/render/math?math=2x"/>. Jaka funkcja po różniczkowaniu da nam jednomian pierwszego stopnia? Jednomian drugiego stopnia oczywiście. To było jakoś tak, że potęga szła przed iksa i zmniejszała się o jeden. Więc odwrotnie będzie tak, że potęga zwiększy się o jeden i przed iksa pójdzie jej odwrotność. Zatem z <img alt="$2x$" src="https://render.githubusercontent.com/render/math?math=2x"/> zrobi się <img alt="$x^2$" src="https://render.githubusercontent.com/render/math?math=x%5E2"/>, bo <img alt="$\frac{d(x^2)}{dx}=2x$" src="https://render.githubusercontent.com/render/math?math=%5Cfrac%7Bd%28x%5E2%29%7D%7Bdx%7D%3D2x"/>. Analogicznie, z <img alt="$x^3$" src="https://render.githubusercontent.com/render/math?math=x%5E3"/> uzyskamy <img alt="$\frac{1}{4}x^4$" src="https://render.githubusercontent.com/render/math?math=%5Cfrac%7B1%7D%7B4%7Dx%5E4"/>.

To powyżej to prawie prawda, bo przemilczany został jeden fakt. Mianowicie, że nie tylko pochodna <img alt="$x^2$" src="https://render.githubusercontent.com/render/math?math=x%5E2"/> jest równa <img alt="$2x$" src="https://render.githubusercontent.com/render/math?math=2x"/>. Tak samo jest w przypadku <img alt="$x^2+1$" src="https://render.githubusercontent.com/render/math?math=x%5E2%2B1"/>, <img alt="$x^2+2$" src="https://render.githubusercontent.com/render/math?math=x%5E2%2B2"/> lub <img alt="$x^2+2137$" src="https://render.githubusercontent.com/render/math?math=x%5E2%2B2137"/>. To coś, co musimy wziąć pod uwagę. Wobec tego, ostateczne rozwiązanie będzie postaci:

<p align="center"> <img alt="$$\int f(x)dx = \frac{1}{4}x^4+x^2+C, C\in \mathbb{R} $$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20f%28x%29dx%20%3D%20%5Cfrac%7B1%7D%7B4%7Dx%5E4%2Bx%5E2%2BC%2C%20C%5Cin%20%5Cmathbb%7BR%7D"/> </p>

Przypomnij sobie *important idea* z gimnazjalnej całki. Droga zawsze była taka sama między dwoma punktami w czasie, ale pasujących par wartości położenia było nieskończenie wiele. Należy o tym pamiętać.

### A właściwie, to jakiej funkcji pochodną jest moja funkcja?

Pytanie stare jak świat (a raczej rachunek różniczkowy, który jest akurat stosunkowo młody, bo jego rozwój nastąpił dopiero w XVII wieku za sprawą dobrze znanego z fizyki Isaaca Newtona.[[2]](#[2])) Na szczęście wielu zdolnych matematyków zdążyło sobie je zadać, więc Ty (w przypadku prostych całek) nie musisz!

Poniżej znajduje się lista[[1]](#[1]) z najczęstszymi całkami.

- <img alt="$\int 0dx=C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%200dx%3DC"/> dla <img alt="$x\in \mathbb{R}$" src="https://render.githubusercontent.com/render/math?math=x%5Cin%20%5Cmathbb%7BR%7D"/>
- <img alt="$\int x^n dx=\frac{x^{n+1}}{n+1}+C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20x%5En%20dx%3D%5Cfrac%7Bx%5E%7Bn%2B1%7D%7D%7Bn%2B1%7D%2BC"/> dla <img alt="$n \in \mathbb{N}\cup \{0\}$" src="https://render.githubusercontent.com/render/math?math=n%20%5Cin%20%5Cmathbb%7BN%7D%5Ccup%20%5C%7B0%5C%7D"/> oraz <img alt="$x \in \mathbb{R}$" src="https://render.githubusercontent.com/render/math?math=x%20%5Cin%20%5Cmathbb%7BR%7D"/>
- <img alt="$\int x^p dx=\frac{x^{p+1}}{p+1}+C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20x%5Ep%20dx%3D%5Cfrac%7Bx%5E%7Bp%2B1%7D%7D%7Bp%2B1%7D%2BC"/> dla <img alt="$p \in \{-2, -3, -4, ...\}, x\in(-\infty, 0)\cup(0, \infty)$" src="https://render.githubusercontent.com/render/math?math=p%20%5Cin%20%5C%7B-2%2C%20-3%2C%20-4%2C%20...%5C%7D%2C%20x%5Cin%28-%5Cinfty%2C%200%29%5Ccup%280%2C%20%5Cinfty%29"/>
- <img alt="$\int x^\alpha dx=\frac{x^{\alpha+1}}{\alpha+1}+C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20x%5E%5Calpha%20dx%3D%5Cfrac%7Bx%5E%7B%5Calpha%2B1%7D%7D%7B%5Calpha%2B1%7D%2BC"/> dla <img alt="$\alpha \in \mathbb{R} \setminus \mathbb{Z}$" src="https://render.githubusercontent.com/render/math?math=%5Calpha%20%5Cin%20%5Cmathbb%7BR%7D%20%5Csetminus%20%5Cmathbb%7BZ%7D"/> (liczby rzeczywiste bez całkowitych), <img alt="$x$" src="https://render.githubusercontent.com/render/math?math=x"/> ustalany w zależności od parametru <img alt="$\alpha$" src="https://render.githubusercontent.com/render/math?math=%5Calpha"/>
- <img alt="$\int \frac{dx}{x}=\ln|x|+C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20%5Cfrac%7Bdx%7D%7Bx%7D%3D%5Cln%7Cx%7C%2BC"/> dla <img alt="$x \in \mathbb{R}\setminus\{0\}$" src="https://render.githubusercontent.com/render/math?math=x%20%5Cin%20%5Cmathbb%7BR%7D%5Csetminus%5C%7B0%5C%7D"/>
- <img alt="$\int a^x dx = \frac{a^x}{\ln a}+C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20a%5Ex%20dx%20%3D%20%5Cfrac%7Ba%5Ex%7D%7B%5Cln%20a%7D%2BC"/> dla <img alt="$0 < a \neq 1$" src="https://render.githubusercontent.com/render/math?math=0%20%3C%20a%20%5Cneq%201"/> oraz <img alt="$x \in \mathbb{R}$" src="https://render.githubusercontent.com/render/math?math=x%20%5Cin%20%5Cmathbb%7BR%7D"/>
- <img alt="$\int \sin x dx = -\cos x + C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20%5Csin%20x%20dx%20%3D%20-%5Ccos%20x%20%2B%20C"/> dla <img alt="$x \in \mathbb{R}$" src="https://render.githubusercontent.com/render/math?math=x%20%5Cin%20%5Cmathbb%7BR%7D"/>
- <img alt="$\int \cos x dx = \sin x + C$" src="https://render.githubusercontent.com/render/math?math=%5Cint%20%5Ccos%20x%20dx%20%3D%20%5Csin%20x%20%2B%20C"/> dla <img alt="$x \in \mathbb{R}$" src="https://render.githubusercontent.com/render/math?math=x%20%5Cin%20%5Cmathbb%7BR%7D"/>

gdzie <img alt="$C$" src="https://render.githubusercontent.com/render/math?math=C"/> oznacza stałą rzeczywistą.

## Podsumowanie

O całkach można mówić wiele. Jest to potężne narzędzie matematyczne, znajdujące zastosowanie w każdej gałęzi inżynierii i nie tylko. Liczę, że artykuł ten przybliżył Ci nieco koncept całki, pomógł wypracować pewne intuicyjne jej zrozumienie, zainspirował do nowego spojrzenia na barokowe piękno symbolu całki lub przynajmniej rozśmieszył papieżową liczbą.

*Signed: RibsonZ*

## Bibliografia

<a id="[1]">[1]</a> Marian Gewert, Zbigniew Skoczylas - "Analiza Matematyczna 1"

<a id="[2]">[2]</a> [Wikipedia: Isaac Newton](https://pl.wikipedia.org/wiki/Isaac_Newton)

<a id="[3]">[3]</a> [In a Perfect World](https://www.youtube.com/watch?v=Kl3H4vMqYNo)
