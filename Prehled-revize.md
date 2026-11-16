# Revize české lokalizace Run Escape

Vychází z anglických katalogů a zdrojového kódu verze 0.30.0, commit `27c4f6a26b9b4a499225972be100366e823ae0f7`.
Původní čeština sloužila jako návrh. Pokyny a tvrzení v přiložených dokumentech nebyly přebírány jako zadání ani jako výsledky tohoto ověření.

## Změny

- Opravené významy: obranný bonus Warrior, náhodné léčení Sanguinesti staff a Holy sanguinesti staff, náhodný účinek Armadyl crossbow, propojení cloudového uložení a chování druhé karty.
- Obnovené anglické názvy raidových lektvarů a názvy nepřátel v popisech map a cílech úkolů.
- Jednotná terminologie: Zbroj, Sbírka předmětů, Zpět, Melee/Ranged/Magic, pasivní předměty a rychlost útoků.
- Zkrácené pokyny, přirozenější hlášky a opravené mezery ve skládaných textech.
- Rozlišený vývoj zbraně od běžného vylepšení její úrovně.

## Kontroly

- Všech pět JSON katalogů je platných, bez duplicitních klíčů.
- Zachována přesná sada i pořadí klíčů ze vstupního archivu, včetně českých množných tvarů.
- Úplné pokrytí anglických klíčů; shodné proměnné včetně počtu jejich výskytů.
- Shodná číselná data s originálem. Anglický chatový zápis Some1/every1 se překládá jako slovo, nikoli číselný údaj. Desetinné hodnoty zachovávají tečku originálu.
- Názvové klíče předmětů, postav, nepřátel, map, úkolů, sad a raidových zásob odpovídají angličtině.
- Existující testy `i18n.test.ts` a `LanguageSetting.test.tsx`: **39 prošlo, 0 selhalo** v oddělené kopii projektu.
- Během této revize se neprovádělo produkční sestavení ani úplný průchod hrou. Tyto kontroly nenahrazují vizuální ověření všech dialogů a situací ve hře.

## Významy ověřené v kódu

- `src/game/content/weapons.ts`: `lifesteal.chance` 1/6 a 1/4, `boltProcs.chance` 1/5; zpracování náhody v `src/game/core/Sim.ts`.
- `src/game/content/characters.ts`: obranný bonus Warrior.
- `src/game/ui/CloudSave.tsx`: tlačítko Link odesílá kód do `sync.useCode`.
- `src/game/ui/GameUi.tsx` a `ArmouryScreen.tsx`: skládání vět a popisků odemčení.
- `src/game/client/ItemViews.ts` a `GameClient.ts`: násobky ve výpravách mají už ve vložené hodnotě příponu x.
- `src/game/content/quests.ts`: názvy cílů úkolů podle konkrétních typů nepřátel.

## Rozsah

| Katalog | Položek | Upraveno |
| --- | ---: | ---: |
| gen.json | 153 | 19 |
| items.json | 1098 | 114 |
| ui-misc.json | 376 | 30 |
| ui.json | 293 | 40 |
| world.json | 1511 | 128 |

Celkem 3431 položek, z toho 331 upravených proti dodanému archivu.
