# PVA4 — PHP 02: Výstup v PHP a kombinace s HTML

Obsahem repozitáře je druhý blok cvičení předmětu PVA4 pro tematický oddíl
výuky programovacího jazyka PHP. Navazuje na `PHP_01_PromenneVyrazy` —
proměnné a konstanty už znáte, tady se učíte kombinovat PHP výstup se
statickým HTML, se kterým jste pracovali loni.

Cvičení je zabalené jako drobná fiktivní aplikace **Maturita** — portál, kde
žáci procházejí historická maturitní témata, navrhují vlastní téma a sledují
konzultace s vedoucím práce. Zatím s ní jen "hrajete roli backendu": žádné
opravdové db, žádné formuláře — jen proměnné, konstanty a výstup PHP do
připravené HTML kostry.

## Jak postupovat

Na začátku máte jediný soubor `index.php`, na konci odevzdáváte dva:
`index.php` (Přehled) a `aboutme.php` (Profil).

Zadání každého úkolu najdete přímo v souboru jako komentář
`<!-- --- ÚKOL N · soubor --- -->` na místě, kam se řešení píše. Úkoly jsou
očíslované **v pořadí, ve kterém je děláte**, a každý staví na předchozím.
Práce má dvě fáze:

- **Fáze A — úkoly 1–13 v `index.php`.** Procházíte soubor odshora dolů
  a čísla jdou v souboru po sobě. Úkoly označené *FÁZE B* zatím přeskočte.
- **Fáze B — úkoly 14–20.** Úkol 14 najdete úplně dole v souboru, vytvoříte
  v něm kopii `aboutme.php`. Úkoly 15–20 pak začínají znovu nahoře
  v souboru — hledejte je podle čísla.

### Pořadí úkolů

| Úkol | Soubor | Kde v souboru | Co děláte |
| --- | --- | --- | --- |
| 1 | `index.php` | úplně nahoře | PHP blok s prvními proměnnými |
| 2 | `index.php` | `<head>` | `<title>` a meta description přes `echo`/`print` |
| 3 | `index.php` | `<head>` | Meta author z proměnné |
| 4 | `index.php` | navigace | Text odkazu „Profil - jméno“ spojováním řetězců |
| 5 | `index.php` | nadpis H1 | `Hello, world!` |
| 6 | `index.php` | metrikové karty | Čísla z proměnných |
| 7 | `index.php` | Historická témata | Vícerozměrné asociativní pole vypsané do tabulky |
| 8 | `index.php` | Historická témata | Hodnoty z pole v řetězci přes `{$pole['klic']}` |
| 9 | `index.php` | Historická témata | Funkce `mb_strlen`, `mb_substr`, `mb_strtoupper` a text s diakritikou |
| 10 | `index.php` | Historická témata | Průměr — `int` vs. `float`, `round()` |
| 11 | `index.php` | Hledání | Parametr z adresy, `??`, `trim()`, `htmlspecialchars()`, `str_contains()` |
| 12 | `index.php` | Ladicí panel | `var_dump()` všech datových typů v `<pre>` |
| 13 | `index.php` | patička | Konstanta `APP_VERSION` |
| 14 | → `aboutme.php` | úplně dole | Kopie `index.php` a smazání sekcí, které na stránku nepatří |
| 15 | oba soubory | navigace | Propojení stránek odkazy |
| 16 | `aboutme.php` | nadpis H1 | Nadpis „Profil - jméno“ |
| 17 | `aboutme.php` | sekce jen pro aboutme.php | Návrh tématu a stav konzultace na jednom řádku |
| 18 | `aboutme.php` | sekce jen pro aboutme.php | Konstanta, přetypování na `(int)`, PHP v atributu `style` |
| 19 | `aboutme.php` | sekce jen pro aboutme.php | Heredoc s asociativním polem, `??` pro chybějící klíč |
| 20 | `aboutme.php` | sekce jen pro aboutme.php | **Bonus:** šablona zprávy přes `str_replace()` a `<br>` |

Úkoly 7–12 a 18–20 navazují na přednášku *Konstrukt 2: Datové typy,
proměnné, operátory*. Podmínky a cykly zatím neznáte, takže je ani
nepoužívejte — všechno jde vyřešit proměnnými, poli, operátory a funkcemi
z přednášky. Úkoly označené **[+ odpověď v komentáři]** chtějí kromě kódu
i krátkou odpověď přímo do HTML komentáře u zadání.

> **Sekce jen pro jednu stránku:** úkoly 7–12 leží v bloku
> `SEKCE JEN PRO index.php` a úkoly 17–20 v bloku
> `FÁZE B · SEKCE JEN PRO aboutme.php`. V úkolu 14 každou z nich smažete
> ze stránky, kam nepatří.

## Vzhled stránky

Stránka má karty se zaoblenými rohy, dvě metrikové karty s ikonou, barvu
`brand` a font Outfit. Styly táhne Tailwind CSS přes Play CDN
(`<script src="https://cdn.tailwindcss.com">`), takže nic nebuildujete ani
neinstalujete — funguje to stejně jako u předchozích cvičení s Bootstrapem
přes CDN.

## Jak spustit stránku

Tohle cvičení se celé kontroluje **v prohlížeči**, žádný z úkolů nevypisuje
nic, co byste rozumně četli v konzoli.

**Přes FlyEnv:** nastavte tuto složku jako document root webu a otevřete
`http://localhost/index.php` (port si ověřte v nastavení FlyEnv, může se
lišit).

**Bez jakéhokoli nastavování** funguje i vestavěný server PHP — ve složce
s cvičením spusťte:

```sh
php -S localhost:8000
```

…a v prohlížeči otevřete `http://localhost:8000/index.php`.

> **Tip:** u úkolů v `<head>` a v meta tazích se dívejte na **zdrojový kód
> stránky** (`Ctrl+U`) — vizuálně se tam nic nezmění, jde jen o to, odkud
> text pochází (statický HTML vs. `echo`/`print`).

> **Parametr v adrese (úkol 11):** hledaný text píšete ručně na konec
> adresy za otazník, např. `http://localhost:8000/index.php?hledat=auto`.
> Mezeru v adrese zapíšete jako `%20`.

## Konvence, které se od vás čekají

Stejné jako u `PHP_01_PromenneVyrazy`:

- **Názvy proměnných** anglicky, `camelCase`, bez diakritiky — `$authorName`,
  ne `$jmeno`.
- **Konstanty** VELKÝMI písmeny s podtržítky: `APP_VERSION`.
- **Uzavírací značku `?>` na konci čistě PHP souboru nepište.** Tady je to
  jinak: PHP blok na začátku souboru `?>` uzavřít **musíte**, protože za ním
  pokračuje HTML.
- Řešení pište **přímo pod komentář příslušného úkolu**, ne na konec souboru.
  Výjimkou jsou deklarace proměnných, polí a konstant — ty patří vždy do PHP
  bloku na úplném začátku souboru.

## Jak poznáte, že to máte správně

Ke každému úkolu, u kterého se dá kontrolovat výstup, je u komentáře
sekce **`Očekávaný výstup:`** — porovnejte ji s tím, co vidíte ve zdrojovém
kódu stránky. Udělejte to vždy, ještě než odevzdáte.

## Odevzdání a automatická kontrola

Práci odevzdáváte do svého repozitáře přes **Classroom 50**:

```sh
git add index.php aboutme.php
git commit -m "Cviceni 02 - vypracovano"
git push
```

Po pushnutí proběhne **automatická kontrola** (stejně jako u dalších cvičení
v Classroom 50) a výsledek najdete ve Feedback PR ve vašem repozitáři —
u každého požadavku uvidíte, jestli prošel, a pokud ne, nápovědu, co doplnit.
Automatická kontrola je pomocná zpětná vazba, ne jediná — porovnání
s **Očekávaným výstupem** dělejte vždy sami jako první krok.
