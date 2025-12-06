> {{meta}}

{{#if img}}
![{{name}}]({{img}})
{{/if}}

{{#if shortDescription}}
{{shortDescription}}
{{/if}}

{{#if description}}
{{description}}
{{/if}}


---

## Werteblock

**Herausforderungsgrad:** {{challenge}} / **XP:** {{xp}}
**Rüstungsklasse:** {{ac}}  
**Trefferpunkte:** {{hp}}
{{#if speedRun}}
**Geschwindigkeit**: {{speedRun}} m
{{/if}}
{{#if speedSwim}}
**Schwimmgeschwindigkeit:** {{speedSwim}} m
{{/if}}
{{#if speedFly}}
**Fluggeschwindigkeit:** {{speedFly}} m
{{/if}}
{{#if speedClimb}}
**Klettergeschwindigkeit:** {{speedClimb}} m
{{/if}}
{{#if speedBurrow}}
**Grabegeschwindigkeit:** {{speedBurrow}} m
{{/if}}


---

| STR                  | DEX                  | CON                  | INT                  | WIS                  | CHA                  |
| -------------------- | -------------------- | -------------------- | -------------------- | -------------------- | -------------------- |
| {{str}} ({{strMod}}) | {{dex}} ({{dexMod}}) | {{con}} ({{conMod}}) | {{int}} ({{intMod}}) | {{wis}} ({{wisMod}}) | {{cha}} ({{chaMod}}) |

---

{{#if savingThrows}}
**Rettungswürfe**:{{#each savingThrows}} {{@key}}: +{{this}},{{/each}}
{{/if}}

{{#if skills}}
**Fertigkeiten:**{{#each skills}} {{@key}}: +{{this}},{{/each}}
{{/if}}

{{#if senses}}
**Sinne:**{{#each senses}} {{this}},{{/each}}
{{/if}}

{{#if languages}}
**Sprachen:**{{#each languages}} {{this}},{{/each}}
{{/if}}

{{#if damageImmunities}}
**Schadensimmunitäten:**{{#each damageImmunities}} {{this}},{{/each}}
{{/if}}

{{#if conditionImmunities}}
**Zustandsimmunitäten:**  
{{#each conditionImmunities}} {{this}},{{/each}}
{{/if}}

---

## Eigenschaften

{{#if traits}}
{{#each traits}}
{{#if this.name}}
**{{this.name}}**
{{this.text}}

{{else}}
{{this}}

{{/if}}
{{/each}}
{{else}}
*(Keine besonderen Merkmale eingetragen.)*
{{/if}}

---

## Aktionen

{{#if actions}}
{{#each actions}}
{{#if this.name}}
**{{this.name}}**
{{this.text}}

{{else}}
{{this}}

{{/if}}
{{/each}}
{{else}}
*(Keine Aktionen eingetragen.)*
{{/if}}

{{#if legendaryActions}}

---

## Legendenaktionen

{{#each legendaryActions}}
{{#if this.name}}
**{{this.name}}**
{{this.text}}

{{else}}
{{this}}

{{/if}}
{{/each}}

{{/if}}


