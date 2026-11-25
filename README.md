# /end: uzávěrka session pro Claude Code

Skill, který na konci každé session zapíše, co je hotové, co zůstává otevřené a co se rozhodlo. Druhý den nezačínáte od nuly a nic nezůstane jen v chatu.

## Co dělá

1. Projde session a roztřídí ji do čtyř košů: rozdělaná práce, rozhodnutí, znalosti a pravidla, stav věcí mimo git.
2. Každý bod zapíše do souboru v repu (`UKOLY.md`, `decisions.md`, `CLAUDE.md`).
3. Vypíše krátké shrnutí: co zapsal, co je ke commitu, co zůstalo otevřené.
4. Když je kontext velký, doporučí novou session a dá vám větu, kterou do ní vložit.

Nic necommituje a nic neposílá ven. Když není co zapsat, řekne to jednou větou a skončí, takže ho můžete pouštět po každé práci.

## Instalace

Vložte do Claude Code tenhle prompt:

```
Nainstaluj mi skill /end z https://github.com/mitakoch/claude-code-end-skill: stáhni end/SKILL.md do ~/.claude/skills/end/SKILL.md. Pak se podívej, jaké soubory na úkoly, rozhodnutí a pravidla tenhle projekt už má, a navrhni mi úpravu tabulky „Kam co patří“.
```

Nebo ručně:

```
mkdir -p ~/.claude/skills/end
curl -fsSL https://raw.githubusercontent.com/mitakoch/claude-code-end-skill/main/end/SKILL.md -o ~/.claude/skills/end/SKILL.md
```

## Použití

Na konci práce napište `/end` (nebo „končíme“).

## Přizpůsobení

Jádro je tabulka „Kam co patří“ v [end/SKILL.md](end/SKILL.md). Přepište ji podle toho, kde máte úkoly, rozhodnutí a pravidla. Čím přesnější cesty, tím lépe to funguje.

Autor: Michael Koch, [fortal.cz](https://fortal.cz). Licence MIT.
