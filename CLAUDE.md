# PM kalkulátor – Claude Code útmutató

Egyfájlos, backend nélküli alapanyag-kalkulátor (`index.html` + `allapot.json` + `logo.png`),
**nyilvános** GitHub Pages-en fut a `main` ágról.

## Szabályok
- Magyarul, tömören. Engedély nélkül ne implementálj; élesre (main) csak Otto jóváhagyásával.
- **Ide üzletadat, adatbázis-séma, jelszó vagy token nem kerülhet** – a repó és az oldal nyilvános.
- A receptszerkesztő jelszavas kapuja (`#jelszó-modal`, `ADMIN_HASH`) marad; csak kényelmi zár, nem valódi védelem.

## Kapcsolódó
- Az üzletenkénti készletfogyás (Tény / Ajánlás / Összevetés) és a régi üzlet-szimulátor utódja
  a privát **`Keszletfogyas`** repóban készül; a terv és a döntések annak `docs/` mappájában vannak.
- A törölt üzlet-szimulátor utolsó állapota: tag `szimulator-elotte-2026-09-30` (b7863e5).

## Vendorolt skillek

A `.claude/skills/` alatt két külső skill-könyvtár van bemásolva, hogy minden Claude Code
sessionben – webes, desktop és CLI – install nélkül betöltődjön:

- [Superpowers](https://github.com/obra/superpowers) (MIT) – 14 skill: brainstorming, TDD,
  szisztematikus hibakeresés, terv-írás és -végrehajtás, kódreview.
- [agent-browser](https://github.com/vercel-labs/agent-browser) (Apache-2.0) – böngésző-automatizálás.
  A skill csak belépési pont, a CLI-t külön kell futtatni: `npx agent-browser <command>`
  (globális `npm i -g agent-browser` nem éli túl a felhős session konténerét).

Frissítés: `.claude/update-skills.sh`. A vendorolt verziók (upstream commitok) a
`.claude/vendor/manifest.tsv` fájlban vannak.

Az alábbi `using-superpowers` skill szabályai minden sessionre érvényesek.

@.claude/skills/using-superpowers/SKILL.md
