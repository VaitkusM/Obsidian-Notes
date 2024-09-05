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
- A Laplace egyenlet fizikailag valamilyen diffúziós folyamat végén előálló egyensúlyi (pl. hőmérséklet) eloszlást reprezentál.
- Ez egy parciális differenciálegyenlet, aminek megoldására nem ismert analitikus képlet.
- Az elterjedten használt numerikus módszerek (véges differencia, végeselem, stb.) a tartomány valamilyen diszkretizációját és valamilyen nagy méretű lineáris egyenletrendszer megoldását igénylik. 
- Számos előnye van ezzel szemben a Monte Carlo módszereknek, amik nem igénylik a tartomány diszkretizációját és tetszőleges pontban képesek mind az interpoláció eredményét, mind a deriváltjait kiértékelni, ráadásul maximálisan párhuzamosítható módon.
- Egy Monte Carlo alapú harmonikus egyenlet megoldónak számos alkalmazása lehet a grafikában és a geometriai modellezésben:
	1. **Vektorgrafika**: a görbék mentén előírt értékek színeket reprezentálnak (pl. RGB formátumban) és a célunk ezekkel a színekkel kitölteni a görbék közötti régiókat. Ez a "[diffusion curve](https://maverick.inria.fr/Publications/2008/OBWBTS08/diffusion_curves.pdf)" technika, amit számos vektorgrafikus rajzoló program támogat.
	2. **Minimálfelületek**: vegyünk egy 3D térben fekvő hurkot (pl. drótból) és merítsük szappanos vízbe. A hurokra egy szappanhártya feszül, amiről fizikai megfontolásokkal belátható, hogy a hurokra feszülő felületek közül a lehető legkisebb a felszíne (ún. [minimálfelület](https://www.google.com/search?q=minimal+surface)). Ha a felületet matematikailag egy 2D tartomány 3D térbe képezésével definiáljuk, akkor az $(x,y,z)$ koordinátafüggvényekről beáltható, hogy kielégítik a 2D Laplace egyenletet!
	3. **N-oldalú felületek:** A geometriai modellezésben széles körben használtak a Bézier és B-spline ("NURBS") paraméteres  felületek, amelyek hátránya viszont, hogy egy téglalap leképezéseként vannak definiálva, így csak "4-oldalú" felületdarabokat tudunk velük megadni. Általánosabb formák megadásához vannak bevett módszerek, mint pl. a "trimmelés", vagy szétbontás több 4-oldalú felületre, ezek azonban számos hátránnyal bírnak a gyakorlatban (amit most ne részletezzünk). Ezen okból felmerül az igény ún. N-oldalú felületek megadására, melyek nem egy téglalap, hanem valami általánosabb 2D tartomány leképezését valósítják meg. Számos N-oldalú felület fajtát publikáltak, a többség azonban egy kaptafára épül: az N-oldalú paraméter tartományt leképezzük a téglalapra több különböző módon, és az így definiálható 4-oldalú felületeket valahogy kombináljuk (pl. ügyesen súlyozva átlagoljuk). Bármilyen N-oldalú felület definíció legfontosabb eleme tehát a tartomány leképezése egy téglalapra (valójában a $[0,1]^2$ egységnégyzetre), amit úgy is hívunk , hogy lokális paraméterezés. A vízszintes paraméter ($s$, mint side) az N-oldalú tartomány egyik határgörbéjének két végpontja között 0 és 1 között lineárisan változik, a szomszédos két görbén pedig konstans 0 és 1 értéket vesz fel (a határ többi részén szintén lineárisan megy át 0 és 1 között). A függőleges paraméter ($d$, mint distance) konstans 0 az egyik oldalon, 0 és 1 között lineárisan változik a két szomszédos oldalon és konstans 1 a többi ("távoli" oldalon". Ez így minden oldalra 2 db interpolációs feladat, amire a legmegbízhatóbb megoldást a harmonikus interpoláció biztosítja. A számított $s-d$ paramétereket aztán fel lehet használni számos különböző N-oldalú felületek kiértékelésére. 


	!(./local_param.png)


