---
name: end
description: Uzávěrka session v Claude Code. Projde session a každý bod zapíše na správné místo v repu, aby nic nezůstalo jen v chatu, a při velkém kontextu doporučí novou session. Spusť, když uživatel napíše /end, „končíme“, „uzavři session“ nebo „zapiš to“. Nic necommituje ani neposílá ven.
---

# /end: session končí zápisem všeho

Princip: co se v session zjistilo, rozhodlo nebo zůstalo rozdělané, musí po jejím zavření ležet v souboru, ze kterého na to naváže další session. Chat se zahazuje.

## 1. Projdi session
Vypiš si (pro sebe, ne do odpovědi) body ve čtyřech koších: rozdělaná práce a úkoly, rozhodnutí, znalosti a pravidla, stav věcí mimo git.

Nezapisuj: hotové a triviální věci, které se dají vyčíst z kódu nebo gitu, a to, co už během session v cílovém souboru stojí.

**Zkratka:** když po tomhle kroku nezbude žádný bod, nic nečti ani nezapisuj, odpověz jednou větou „Nic k zápisu“ (plus co je ke commitu, pokud něco je) a skonči.

Před zápisem si z cílového souboru přečti jen to, co potřebuješ k doplnění (u dlouhých souborů začátek nebo příslušnou sekci, ne celý soubor). Jen doplňuj, nic nepřepisuj ani nemaž. Data piš absolutně (RRRR-MM-DD), ne „zítra“ nebo „příští týden“.

## 2. Kam co patří

Tabulku si uprav podle svého projektu. Pokud projekt už podobné soubory má (TODO, backlog, ADR), použij je a nové nezakládej.

| Koš | Cíl |
|---|---|
| Rozdělaná práce, další krok | `UKOLY.md` v kořeni repa (větší úkol jako vlastní sekce, drobnost jako řádek) |
| Rozhodnutí | `decisions.md` v kořeni repa (formát níž); když chybí, založ ho s nadpisem `# Rozhodnutí` |
| Znalosti a pravidla (jak se tu něco dělá, kde co leží, zpětná vazba od uživatele) | `CLAUDE.md` projektu, jen když to platí i pro další session; krátce, jedna odrážka |
| Práce mimo git (dokumenty, podklady) | soubor `STAV.md` v té složce: co je hotové a další krok |
| Otevřené otázky, které se teď vyřešily | odškrtnout nebo doplnit odpověď přímo v souboru, kde otázka stojí |

Rozdělaná práce se zapisuje tak, aby na ni navázal někdo bez téhle session: co je hotové, další konkrétní krok, cesty k souborům.

Formát záznamu v `decisions.md` (nejnovější nahoře):

```
## RRRR-MM-DD: <rozhodnutí jednou větou>
- Proč: …
- Zamítnuto: … (a proč)
```

Rozpor s existujícím pravidlem nerozhoduj, obě znění vypiš do shrnutí.

## 3. Git a odesílání
Nic necommituj ani nepushuj bez pokynu. Nic neposílej ven (e-maily, zprávy, akce v cizích systémech).

## 4. Shrnutí a délka kontextu
Na konci krátce vypiš (prázdné body vynech):
- **Zapsáno:** soubor a jedna věta k němu
- **Ke commitu:** soubory podle repa (jen nabídnout)
- **Otevřené:** co zůstalo a kde je to zapsané

Když je kontext session velký (zhruba nad 250k tokenů), doporuč pokračovat v nové session a napiš jednu větu, kterou do ní vložit (cesta k úkolu nebo zápisu, na který se navazuje).
