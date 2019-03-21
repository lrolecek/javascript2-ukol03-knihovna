# Úkol 03 - Knihovna

Tvým úkolem je dokončit program pro správu domácí knihovničky, který jsme začali ve 3. lekci. Návod na zpracování a zadání úlohy najdeš níže.

Úkol je **povinný**, tj. je nutné ho vypracovat pro udělení závěrečného certifikátu.

Termín odevzdání: **úterý 2. 4. 2019**

Úkol není zkouška. Pokud něco nevíš, **zeptej se**, rádi ti odpovíme a poradíme. Chceme, abys úkol uměla vypracovat. Netestujeme, zda to umíš sama od sebe.

## Instalace

Postupuj stejně, jako v případě startovního projektu, který používáme na hodinách.

1. Udělej si **fork** tohoto projektu na GitHubu.
2. Tentokrát nemusíš repozitář přejmenovávat, jako to děláme se startovním projektem. Až budeš mít repozitář s úkolem na svém účtu, klikni na zelené tlačítko **Clone or Download** a vyber **Open in Desktop**.
3. V aplikaci GitHub Desktop vyber složku na svém disku, kam si ukládáš příklady z hodin (pravděpodobně už bude vybraná z minula) a potvrď.
4. Až budeš mít projekt stažený k sobě na disk, otevři ho ve Visual Studio Code.
5. Otevři terminál a zadej `npm install`
6. Pracuj na úkolu...
7. Kód spustíš pomocí `npm run serve`

## Odevzdání úkolu

1. Až budeš mít úkol hotový, udělej v GitHub Desktop **commit** (tj. u tebe na disku se ve verzovacím systému Git vytvoří nový bod v historii projektu).
2. Až proběhne commit, vyber volbu **Push to Origin**, abys hotové změny poslala i do internetu na svůj GitHub účet.
3. Ve skupině na Facebooku máš odkaz na formulář, kam se úkol odevzdává. Napíš tam svoje jméno, email, a adresu na tvůj GitHub repozitář s úkolem.

## Zadání

Program je víceméně ve stavu, v jakém jsme ho napsali ve 3. lekci, pouze jsou v něm drobné změny.

Třída kniha (*book.js*) je upravena tak, že každá kniha nyní obsahuje i vlastnost pro obrázek s přebalem knihy, který je nutné předat jako čtvrtý parametr do konstruktoru.

V hlavním programu máš předvyplněných 16 knih, které se přidávají do knihovny. Jejich obálky najdeš ve složce *images*.

Úkol má **povinnou část**, kterou musí vypracovat všichni, aby jim byl úkol uznán. **Bonusová část** je pro ty, co chtějí dělat něco navíc a chtějí si s projektem hrát.

### Povinná část úkolu

1. **Do třídy *Library* přidej metodu pro dočtení aktuálně čtené knihy**

   Metodu nazvi `finishCurrentBook()` a měla by dělat následující:
   - u aktuálně čtené knihy zavolá metodu `read()` (tu už máme hotovou), která označí knihu jako přečtenou
   - přesune aktuální knihu z vlastnosti `currentBook` do vlastnosti `lastBook`
   - do `currentBook` dáme hodnotu null - dočetli jsme, takže teď nic nečteme
   - aktualizuje počet nepřečtených knih, aby odpovídal aktuálnímu stavu
   - dáváme pozor na chybové stavy - tj. všechny výše zmíněné body zabalíme do podmínky, která se provede pouze pokud v aktuálně čtené knize nějaká kniha je (tj. není tam hodnota `null`)

2. **Do třídy *Library* přidej metodu pro výpis všech nepřečtených knih**

   Metodu nazvi `listUnreadBooks()` a měla by dělat následující:
   - vyfiltruje ze seznamu všech knih (vlastnost `booklist`) jenom ty knihy, které jsou nepřečtené
   - výsledek se uloží do lokální proměnné jako nové pole
   - toto nové pole (seznam nepřečtených knih) vypíše do konzole (nebo do HTML, viz. bonus)

   Nejlepší a nejelegantnější varianta je, že použiješ na pole knih metodu `.filter()` a jako parametr do ní napíšeš krátkou arrow funkci, která vrátí `true` pro nepřečtené knihy. Výstupem bude nové pole obsahující pouze nepřečtené knihy.

   Dokumentaci k `array.filter()` najdeš na [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) nebo na [Javascript.info](https://javascript.info/array-methods) (cca uprostřed stránky).

   Můžeš se podívat i na [video o metodě filter z podzimního kurzu JavaScript 1](https://www.youtube.com/watch?v=kGCQJdikZCo&list=PLTCx5oiCrIJ4t6lZhFqH3SHI74QI_HjDn&index=8&t=2232s).

### Bonusová část úkolu (dobrovolná, pro šprtky)

Tato část je pro ty, kdo si chtějí s úkolem dál hrát. Není nutná pro uznání úkolu jako splněného.

3. **Ke knize do třídy *Book* dopiš metodu, která bude vracet HTML kód pro zobrazení knihy**

   Metodu nazvi `renderHTML()` a měla by vrátit text s vygenerovaným HTML kódem pro danou knihu. Tento kód pak můžeš později (viz. další krok), použít k tomu, abys místo výpisu do konzole zobrazila hezký seznam knih přímo na stránce.

   Vzor kódu, který bude metoda vracet, vypadá následovně (do kódu na příslušná místa samozřejmě doplníš vlastnosti aktuální knihy (název, autora, atd.)):

```html
<div class="book">
  <div class="book__image">
    <img src="images/book.jpg" alt="Obálka Název knihy">
  </div>
  <div class="book__info">
    <h3 class="book__title">Název knihy</h3>
    <p class="book__meta">Jméno Autora, 1975</p>
  </div>

  <!-- je-li kniha přečtená, vygeneruj sem i toto: -->
  <div class="book__badge book__badge--read">Přečteno</div>

  <!-- jedná-li se o aktuálně čtenou knihu, vygeneruj sem toto: -->
  <div class="book__badge book__badge--current">Právě čtu</div>

</div>
```

4. **Ve třídě *Library* změň metody pro výpis knih (všech i nepřečtených) tak, aby se místo vypisování do konzole generovalo HTML do stránky**

   Změň metody `listAllBooks()` a `listUnreadBooks()` tak, aby nepoužívaly `console.table(...)`, ale volaly pro každou knihu metodu `renderHTML()`, kterou jsi do třídy `Book` dopsala v prvním kroku bonusového úkolu.

   Protože oba výpisy (všech knih a nepřečtených knih) fungují na stejném principu - budou vypisovat obsah nějakého pole knih do stránky. Protože nechceme zbytečně opakovat kód, vytvoř si v třídě *Library* další metodu, která bude jako parametr přijímat pole a jako výsledek vrátí vygenerované HTML celého seznamu.

   Pole knih můžeš procházet postupně a pro každou knihu generovat HTML kód, ten si uložit do nějakého řetězce, který nakonec vložíš do stránky.

   Pokud chceš být opravdu cool, nemusíš knihy postupně procházet v cyklu, ale zkus nastudovat a použít metodu pole `.reduce()`. Dokumentaci najdeš na [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) nebo se nás zeptej na Facebooku :)

   HTML kód seznamu knih vlož do připraveného divu, který má `id="booklist"` (viz. *index.html*).

   V startovním kódu úkolu už je připravené CSS, takže by seznam knih na stránce měl vypadat docela hezky.

5. **Přidej do stránky tlačítka pro dočtení aktuální knihy a započetí čtení příští knihy**

   Do HTML v *index.html* přidej tlačítka **Dokončit aktuální knihu** a **Začít číst další knihu**.

   Na tlačítka přidej *event listener* pro událost *click* a v ovladači pro danou událost volej příslušné metody naší knihovny.

   Nezapomeň při každé změně i znovu vygenerovat HTML do stránky, aby se změny na stránce vizuálně projevily.

   Pokud máš vše správně, měla bys vidět, jak se knihy v knihovně při klikání na tlačítka postupně označují jako přečtené.