{{#if type}}
> *{{type}}*
{{/if}}

{{#if (eq level "cantrip")}}
Zaubertrick
{{else}}
**Stufe:** {{level}}
{{/if}}

{{{description}}}

{{#if higher_level}}
---

## ⬆️ Auf höheren Stufen

{{{higher_level}}}
{{/if}}

---

## 🔮 Zauberinformationen

**Wirkzeit:** {{casting_time}}
**Reichweite:** {{range}}
**Wirkungsdauer:** {{duration}}
{{#if classes}}
**Klassen:**  
{{#each classes}}
- {{this}}
{{/each}}
{{/if}}

{{#if components}}
{{#if components.raw}}
**Komponenten (Rohformat):** {{components.raw}}
{{/if}}
{{#if components.materials_needed}}
**Benötigte Materialien:** {{components.materials_needed}}
{{/if}}
{{/if}}
{{#if ritual}}
**Ritual:** Ja
{{else}}
**Ritual:** Nein
{{/if}}






