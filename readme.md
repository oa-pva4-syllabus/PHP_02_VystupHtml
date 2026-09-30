# PVA4 — PHP 02: Výstup v PHP a kombinace s HTML

Obsahem repozitáře je druhý blok cvičení předmětu PVA4 pro tematický oddíl
výuky programovacího jazyka PHP. Navazuje na `PHP_01_PromenneVyrazy` —
proměnné a konstanty už znáte, tady se učíte kombinovat PHP výstup se
statickým HTML, se kterým jste pracovali loni.

Cvičení je zabalené jako drobná fiktivní aplikace **Maturita** — portál, kde
žáci procházejí historická maturitní témata, navrhují vlastní téma a sledují
konzultace s vedoucím práce. Zatím s ní jen "hrajete roli backendu": žádné
opravdové db, žádné formuláře — jen proměnné, konstanty a výstup PHP do
připravené HTML kostry v stylu [TailAdmin](https://tailadmin.com).

## Obsah

| Soubor | Téma |
| --- | --- |
| `cover.html` → `index.php` | Přejmenování na PHP, PHP výstup v `<head>`, v nadpisu a v metrikových kartách dashboardu |
| `aboutme.php` | Kopie `index.php` — stránka Profil s návrhem tématu a stavem konzultace, propojení stránek, konstanta |
| `index.php`, úkoly 13–18 | Pole a vícerozměrné pole do tabulky, vkládání proměnných do řetězce (`{$pole['klic']}`), funkce `mb_*`, `int` vs. `float`, parametr z adresy s `??` a `htmlspecialchars()`, `var_dump()` v ladicím panelu |
| `aboutme.php`, úkoly 19–21 | Přetypování a PHP v atributu `style`, heredoc s asociativním polem, bonus: šablona zprávy přes `str_replace()` |

Zadání jednotlivých úkolů najdete přímo v souboru jako komentáře
`<!-- --- ÚKOL N --- -->` na místě, kam se řešení píše. Postupujte v pořadí,
každý úkol staví na předchozím.

Úkoly 13–21 navazují na přednášku *Konstrukt 2: Datové typy, proměnné,
operátory*. Podmínky a cykly zatím neznáte, takže je ani nepoužívejte —
všechno jde vyřešit proměnnými, poli, operátory a funkcemi z přednášky.
Úkoly označené **[+ odpověď v komentáři]** chtějí kromě kódu i krátkou
odpověď přímo do HTML komentáře u zadání.

## Vzhled stránky

Šablona používá vzhled [TailAdmin](https://tailadmin.com) — kartu se
zaoblenými rohy, dvě metrikové karty s ikonou (vzor `partials/metric-group`),
barvu `brand` a font Outfit. Styly táhne Tailwind CSS přes Play CDN
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

> **Parametr v adrese (úkol 17):** hledaný text píšete ručně na konec
> adresy za otazník, např. `http://localhost:8000/index.php?hledat=auto`.
> Mezeru v adrese zapíšete jako `%20`.

## Konvence, které se od vás čekají

Stejné jako u `PHP_01_PromenneVyrazy`:

- **Názvy proměnných** anglicky, `camelCase`, bez diakritiky — `$authorName`,
  ne `$jmeno`.
- **Konstanty** VELKÝMI písmeny s podtržítky: `APP_VERSION`.
- **Uzavírací značku `?>` na konci souboru nepište.**
- Řešení pište **přímo pod komentář příslušného úkolu**, ne na konec souboru.

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
