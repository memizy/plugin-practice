Zde je návrh `README.md` pro tvůj nový **Practice Plugin**. Je stylizovaný tak, aby ladil s ostatními pluginy v ekosystému Memizy a hned na začátku nabízí tlačítka pro rychlé vyzkoušení s testovací sadou.

***

```markdown
<div align="center">

# 🏋️ Practice Plugin
**Classic Spaced Repetition Drill Plugin for the Memizy Ecosystem**

![Version](https://img.shields.io/badge/Version-0.1.0-blue?style=for-the-badge)
![Supported Items](https://img.shields.io/badge/Supports-8_Types-blueviolet?style=for-the-badge)
![Features](https://img.shields.io/badge/Features-Leitner%20%7C%20Weighted%20Random-success?style=for-the-badge)

<br>

Oficiální tréninkový plugin pro intenzivní dril studijních sad pomocí **Leitnerova systému**. Zaměřuje se na inteligentní procvičování položek, které ještě neumíte, zatímco ty známé odsouvá na později.

<br>

[![Practice with Test Suite](https://img.shields.io/badge/🏋️_Practice-With_Test_Suite-2ea44f?style=for-the-badge)](https://memizy.github.io/plugin-practice/?set=https://cdn.jsdelivr.net/gh/memizy/set-test-suite@main/data.oqse.json)
[![Open Empty Sandbox](https://img.shields.io/badge/⚙️_Open-Empty_Sandbox-6e7681?style=for-the-badge)](https://memizy.github.io/plugin-practice/)

</div>

---

## 📖 O pluginu

**Practice Plugin** je navržen pro maximálně efektivní učení. Na rozdíl od pouhého procházení poznámek vás tento plugin aktivně zkouší ze všech typů OQSE položek a dynamicky upravuje frekvenci jejich zobrazování na základě vašich výsledků.

### ✨ Hlavní funkce
* **Vážený náhodný výběr:** Plugin vybírá otázky chytře. Čím méně položku znáte (nižší bucket), tím častěji se objevuje:
    * 🔴 **Bucket 0 & 1:** Maximální priorita (Váha 1.0)
    * 🟠 **Bucket 2:** Časté opakování (Váha 0.7)
    * 🟡 **Bucket 3:** Upevňování (Váha 0.4)
    * 🟢 **Bucket 4:** Udržování (Váha 0.1)
* **Prevence opakování:** Algoritmus zajišťuje, že nedostanete stejnou otázku dvakrát hned po sobě (pokud má sada více než jednu položku).
* **Interaktivní vyhodnocení:** Podpora pro všech 8 základních OQSE typů včetně seřazování, propojování párů a vícečetného výběru.
* **Vizuální přehled:** V záhlaví neustále vidíte, kolik karet máte v jednotlivých úrovních znalostí.

## 🛠 Technické specifikace (OQSEM Manifest)

Plugin deklaruje plnou kompatibilitu s formátem OQSE v0.1 a podporuje vykreslování Markdownu, HTML a matematických vzorců v LaTeXu.

```json
{
  "id": "[https://memizy.github.io/plugin-practice/](https://memizy.github.io/plugin-practice/)",
  "appName": "Practice Mode",
  "version": "0.1.0",
  "studyMode": "drill",
  "capabilities": {
    "actions": ["render"],
    "types": [
      "flashcard", "mcq-single", "mcq-multi", "true-false", 
      "match-pairs", "sort-items", "short-answer", "note"
    ],
    "features": ["markdown", "math", "html"]
  }
}
```

## 🚀 Jak používat

### V rámci ekosystému Memizy (Hostitel)
Plugin je plně integrován s `@memizy/plugin-sdk`. Stačí otevřít libovolnou studijní sadu v aplikaci Memizy a zvolit režim **Practice**. O ukládání do cloudu a synchronizaci progresu se postará hostitelská aplikace.

### Samostatný režim (Standalone)
Díky vestavěnému Standalone UI v SDK můžete plugin používat i samostatně. Stačí v prohlížeči otevřít URL a přetáhnout do okna svůj soubor `.oqse.json`. Progres se v tomto případě ukládá do lokálního úložiště prohlížeče.

---

## 💻 Pro vývojáře

Tento plugin je ukázkou čisté implementace v **Vanilla JavaScriptu** bez nutnosti sestavování (build step).

* **SDK Integrace:** Využívá `sdk.store.answer()` pro nativní výpočet Leitnerových intervalů přímo v SDK.
* **Bezpečnost:** Veškerý uživatelský obsah je před vykreslením sanitován pomocí **DOMPurify** po průchodu Markdown parserem.
* **Design:** Moderní UI postavené na CSS proměnných pro snadnou úpravu barevných schémat a plnou responzivitu.

---
*Vytvořeno jako součást otevřeného ekosystému Memizy.*
```