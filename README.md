
# JavaScript-baserad webbshop

Detta är ett litet webbshops-system skapat med JavaScript. Den har endast grundläggande funktioner, och är endast tänkt att användas i studiesyfte.

Du får fritt använda denna JavaScript-kod för detta projekt, och modifiera den efter behag (under förutsättning att gjorda ändringar noteras överst i filen) - men **använd inte denna utanför denna uppgift.**

### Video-demonstration

https://www.youtube.com/watch?v=U2_x_3dOSI0

## Installation

Ladda ner filen webshop.js och inkludera denna till dina webbsidor, lämpligen innan stängande body-tagg.

I din HTML-kod kan du sedan, genom att infoga element med specifika ID eller klasser infoga funktionalitet.

Följande finns att tillgå:

### Knapp för att lägga vara i varukorg

Det finns en funktion, **addToBasket**, som används för att lägga en vara i varukorgen genom att lägga ett onclick-anrop från en knapp, eller annat element.  
Denna funktion tar följande parametrar:

*   **el** - elementet varifrån anropet kommer. Skicka alltid med **this** till denna
*   **id** - (Sträng) Artikelnummer/ID för varan, ex. 001 (måste vara unikt)
*   **name** - (Sträng) Varunamn
*   **cost** - (Heltal) varans pris
*   **image** - (Sträng) sökväg och filnamn till produktens bild
*   **notify** - (Valfri)(Boolean) - om meddelande-rutan ska skrivas ut. Standard = false

Ett exempel på hur en knapp kan se ut:


```html
<button onclick="addToBasket(this, '16-1101','Högtalare (vit)', 245, 'images/speaker_white_small.jpg')">Köp</button>
```

När en vara lagts i varukorgen läggs en klass till till det element varifrån funktionen anropades, **clicked**, så vill du dölja eller på annat sätt indikera att detta gjors går detta att göra med CSS, ex: .clicked { display: none; }

### #basket

Stor variant av varukorg. Lägg till en unordered list, ul. Exempel:

```html
<ul id="basket"></ul>
```

Utskriften till detta element bli då på denna form (med två varor, för att visa):
```html
<ul id="basket">
    <li>
        <span class="item-text">Vara #1, </span>
        <span class="item-count">1 st </span>
        <span class="item-cost">100:-</span>
    </li>
    <li>
        <span class="item-text">Vara #2, </span>
        <span class="item-count">1 st </span>
        <span class="item-cost">200:-</span>
    </li>
    <li class="sum">Summa: 600:-</li>
</ul>
```
Notera klasserna **item-text**, **item-count**, **item-cost** och **sum** som skapas för att göra det enklare att infoga CSS.

### #small-basket

En mindre variant av varukorgen, som visar endast antal och totalsumma i text-form. Går att lägga på vilket element som helt, både block- och inline-element.  
Ett exempel:

```html
<span id="small-basket"></span></pre>
```
Ger motsvarande utskrift:

```html
<span id="small-basket">2st, 600:-</span>
```

### #checkout

Id **checkout** sätts på ett **tbody**-element inuti en tabell, för att skriva ut varulistan i tabellformat. Denna tabell skrivs ut med 5 stycken celler (td) per rad, i ordningen bild, artikelnummer/id, varunamn, antal och pris.  
Ett exempel:

```html
<table>
    <thead>
        <tr>
            <td>Bild</td>
            <td>Artikelnr</td>
            <td>Varunamn</td>
            <td>Antal</td>
            <td>Pris</td>
        </tr>
    </thead>
    <tbody id="checkout"></tbody>
</table>
```
Ger utskrift i följande format:

<table>
        <thead>
            <tr>
                <td>Bild</td>
                <td>Artikelnr</td>
                <td>Varunamn</td>
                <td>Antal</td>
                <td>Pris</td>
            </tr>
        </thead>
        <tbody id="checkout">
            <tr>
                <td>
                    <img src="images/image.png" alt="Produktbild för Vara #1">
                </td>
                <td>16-1101</td>
                <td>Vara #1</td>
                <td>1 st.</td>
                <td>100:-</td>
            </tr>
            <tr>
                <td>
                    <img src="images/image.png" alt="Produktbild för Vara #2">
                </td>
                <td>16-1102</td>
                <td>Vara #2</td>
                <td>1 st.</td>
                <td>200:-</td>
            </tr>
            <tr>
                <td colspan="5" class="checkout-sum">Summa: 300:-</td>
            </tr>
        </tbody>
    </table>

### Knappar för att slutföra köp

Det finns två stycken funktioner för att slutföra eller avbryta köp:

*   **checkOutBasket()** - skickar (virtuell) beställning.
*   **emptyBasket()** - rensar varukorgen.

Exempel på dessa två knappar:

```html
<button onclick="checkoutBasket()">Slutför köp</button>
<button onclick="emptyBasket()">Töm varukorgen</button>
```

### Extra funktionalitet

Det finns några ytterligare små funktioner som kan användas efter behov.

Extra klasser:

*   **.checkout-inline** - om varor finns i varukorgen sätts alla element med denna klass till display: inline; (dölj med CSS, vid behov)
*   **.checkout-button** - om varor finns i varukorgen sätts alla element med denna klass till display: block; - annars display: none;
*   **.items-in-basket** - skriver ut antal varor i text
*   **.total-sum** - skriver ut totalsumman i text

#### Notifiering vid vara lagd till varukorg

Om true skickats med som parameter till att lägga vara i varukorgen, och ett element med id **notify** finns, skapas följande:

```html
<p>Varan <b>Vara #3</b> lagd i varukorgen</p>
```
Den lägger även på en klass vid utskrift, **visible** som tas bort efter tre sekunder. Denna klass kan då användas för att tillfälligt skriva ut ett meddelande till användaren för att tydliggöra att en vara lagts i varukorgen. Ett CSS-exempel: .visible { display: block; } på ett annars dolt element.


### Test av branch
Detta är en test-branch