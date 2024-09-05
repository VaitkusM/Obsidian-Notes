- TDK cím javaslat: A Monte Carlo módszer alkalmazásai a geometriai modellezésben
- Tekintsünk egy $D$-vel jelölt 2D tartományt (u,v koordináta sík részhalmazát), aminek határát N db általános (pl. egyenes/Bézier/spline) görbe határolja ($C_1,\ldots, C_N$).
- Tegyük fel, hogy ismerjük valamilyen mennyiség értékeit az említett határgörbék mentén, amit a $C_i$ görbe $t$ paramétere függvényében $f_i(t)$-vel jelölünk.
- A célunk a görbéken előírt értékeket a lehető legegyenletesebb módon kiterjeszteni a tartomány belsejébe. 
- Egy függvény egyenletességét jól méri a deriváltak nagysága, különösen a második derivált, ami az ideálisnak gondolt lineáris függvény esetén 0. A második derivált legközelebbi megfelelője 2 és több dimenzióban az ún. Laplace operátor, amit $\Delta$ jelöl és aminek konkrét definíciójánál fontosabb a szemléletes jelentése, miszerint a függvény adott pont körüli környezetében mért átlagértéktől való eltérését méri. 
- Így jutunk az ún. Laplace egyenlethez, aminek megoldásait harmonikus függvényeknek, vagy (harmonikus interpolációnak) szoktuk hívni és a lineáris interpoláció egyfajta általánosításaként gondolhatunk rájuk:  

``` math
\begin{align}
\Delta F(u,v) &= 0 \\ 
F(u,v) &= f_i(t), \text{, ha } (u,v) = C_i(t) 
\end{align}
```
- Ez egy parciális differenciálegyenlet, aminek megoldására nem ismert analitikus képlet.
- Az elterjedten használt numerikus módszerek (véges differencia, végeselem, stb.) a tartomány valamilyen diszkretizációját és valamilyen nagy méretű lineáris egyenletrendszer megoldását igénylik. 
- Számos előnye van ezzel szemben a Monte Carlo módszereknek, amik nem igénylik a tartomány diszkretizációját és tetszőleges pontban képesek mind az interpoláció eredményét, mind a deriváltjait kiértékelni, ráadásul maximálisan párhuzamosítható módon.
- Egy Monte Carlo alapú harmonikus egyenlet megoldónak számos alkalmazása lehet a grafikában és a geometriai modellezésben:
	- 


