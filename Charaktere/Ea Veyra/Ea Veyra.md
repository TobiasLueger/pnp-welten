---
aliases:
  - Bob
tags:
  - Category/Spieler
Player: Tobias
Role: Spieler
level: 3
hp: 23
ac: 11
modifier: 1
pasperc: 11
Status: Active
PlayerKnownLanguages:
  - Gemeinsprache
  - Abyssal
  - Deep Speech
  - Infernal
faction_standing:
  Faction Name 1: 1
  Faction Name 3: 3
char_description: |-
  testtest
  zesz
  zezs
char_race: Tiefling
char_class: Hexenmeister
char_gender: Weiblich
char_status: Lebendig
char_age: 27
char_items:
  - "[[Kette (10 feet)]]"
  - "[[Würfelset]]"
  - "[[Leder]]"
  - "[[Leichte Armbrust]]"
  - "[[Armbrustbolzen (20)]]"
  - "[[Komponententasche]]"
  - "[[Rucksack]]"
  - "[[Buch]]"
  - "[[Tinte (25ml Flasche)]]"
  - "[[Feder für Tinte]]"
  - "[[Pergament (ein Blatt)]]"
  - "[[Kleidung, Gewöhnlich]]"
  - "[[Kleiner Beutel mit Sand]]"
  - "[[Brief eines verstorbenen Kollegen]]"
  - "[[Gürteltasche]]"
  - "[[Zweihändige Keule]]"
gm_notes: |-
  test
  rtest
  test
---
> [!NOTE|div-m] Player Name: `Ea Veyra`

> [!column|no-i no-t]
>> [!div-m|no-title]
>> ![[normal form removed.webp|417x626]]
>
>> [!div-m|no-title] Place Name
>>~~~ meta-bind
>>INPUT[select(
>>option(1, Allgemein),
>>option(2, Beschreibung),
>>option(3, Konfiguration),
>>option(4, GM Notes),
>>class(tabbed)
>>)]
>>~~~
>>> [!tabbed-box]
>>> >[!div-m|no-title]
>>> >![[#Allgemein|no-h clean]]
>>>
>>> > [!div-m|no-title]
>>> > ![[#Beschreibung|no-h clean]]
>>>
>>> > [!div-m|no-title]
>>> >![[#Konfiguration|no-h clean]]
>>>
>>> > [!div-m|no-title]
>>> > ![[#GM Notes|no-h clean]]
>>> 

> [!NOTE|no-title]
>~~~ meta-bind
>INPUT[select(
>option(1, Abilities+Skills),
>option(2, Traits),
>option(3, Zauber Buch),
>option(4, Inventory),
>option(5, Connections),
>option(6, Relationships),
>class(tabbed)
>)]
>~~~
>> [!tabbed-box]
>>>[!div-m|no-title]
>>> ![[#Skills|no-h1 clean]]
>>
>>>[!div-m|no-title]
>>> ![[#Traits|no-h1 clean]]
>>
>>>[!div-m|no-title]
>>> ![[#Zauber Buch|no-h1 clean]]
>>
>>>[!div-m|no-title]
>>> ![[#Inventory|no-h1 clean]]
>>
>>>[!div-m|no-title]
>> >![[#Connections|no-h1 clean]]
>>
>>>[!div-m|no-title]
>>> ![[#Relationships|no-h1 clean]]

---

# Allgemein

```dataviewjs
const lvl = dv.current().level;
const ac = dv.current().ac;
const mod = dv.current().modifier;

const initStr = (typeof mod === "number" && mod > 0) ? `+${mod}` : `${mod}`;


const mageArmor = (typeof ac === "number" && typeof mod === "number") ? ac + mod : ac;


const badges = [
  { label: "Level", value: lvl },
  { label: "Initiative", value: initStr },
  { label: "Rüstungsklasse", value: mageArmor },
];

let out = "```badges\nitems:\n";
for (let b of badges) {
  const v = typeof b.value === "number" ? b.value : `'${b.value}'`;
  out += `  - label: ${b.label}\n    value: ${v}\n`;
}
out += "```";

dv.paragraph(out);
```
```dataviewjs
const hp = dv.current().hp;


const dice = "d8";
const diceValue = 3;


let out = "```healthpoints\n";
out += `state_key: din_health\n`;
out += `health: ${hp}\n`;
out += `death_saves: true\n`;
out += `reset_on: long-rest\n`;
out += `hitdice:\n`;
out += `  dice: ${dice}\n`;
out += `  value: ${diceValue}\n`;

dv.paragraph(out);
```
```event-btns
items:
  - name: Short Rest
    value: short-rest
  - name: Long Rest
    value: long-rest
  - name: Level Up
    value: level-up 
```

# Beschreibung
```dataviewjs
const race = dv.current().char_race;
const cclass = dv.current().char_class;


let out = "";
out += `**Rasse:** ${race}\n`;
out += `**Klasse:** ${cclass}\n`;

dv.paragraph(out);
```
`INPUT[textArea:char_description]`

# Konfiguration

| Stat     | Value                                                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Status   | `INPUT[inlineSelect(option(Lebendig), option(Tod)):char_status]`                                                                       |
| Rasse     | `INPUT[inlineSelect(option(Mensch), option(Halbling), option(Halb-Elf), option(Zwerg), option(Drachenblütiger), option(Halb-Orks), option(Elf), option(Gnom), option(Tiefling)):char_race]`                                                                                                 |
| Klasse    | `INPUT[inlineSelect(option(Barbar), option(Barde), option(Druide), option(Hexenmeister), option(Kämpfer), option(Kleriker), option(Magier), option(Mönch), option(Paladin), option(Schurke), option(Waldläufer), option(Zauberer), option(Magieschmied)):char_class]` |
| Level    | `INPUT[number:level]`                                                                                                                |
| Geschlecht   | `INPUT[inlineSelect(option(Männlich), option(Weiblich), option(Andere)):char_gender]`                                                       |
| Alter      | `INPUT[number:char_age]` |
| HP       | `INPUT[number:hp]`                                                                                                        |
| AC       | `INPUT[number:ac]`                                                                                                                   |
| Modifier | `INPUT[number:modifier]`                                                                                                             |

# GM Notes

`INPUT[textArea:gm_notes]`

# Skills

```dataviewjs
const pasperc = dv.current().pasperc;

const badges = [
  { label: "Passive Wahrnemung", value: pasperc },
];

let out = "```badges\nitems:\n";
for (let b of badges) {
  const v = typeof b.value === "number" ? b.value : `'${b.value}'`;
  out += `  - label: ${b.label}\n    value: ${v}\n`;
}
out += "```";

dv.paragraph(out);
```

```ability
abilities:
 stärke: 10
 geschicklichkeit: 12
 konstitution: 13
 intelligenz: 14
 weisheit: 12
 charisma: 19

proficiencies: 
 - weisheit 
 - charisma 
```

<br>

```skills
proficiencies:
 - arkane kunde
 - geschichte
```


# Traits

Hier stehen due traits BSP:

### Super Traits
```consumable
label: ""
state_key: din_super_traits
uses: 3
```
Blah Blah Blah


# Zauber Buch

```dataviewjs
const badges = [
  { label: "Zauber Rettungswurf", value: 14 },
  { label: "Zauber Angriffsbonus", value: "+6" },
];

let out = "```badges\nitems:\n";
for (let b of badges) {
  const v = typeof b.value === "number" ? b.value : `'${b.value}'`;
  out += `  - label: ${b.label}\n    value: ${v}\n`;
}
out += "```";

dv.paragraph(out);
```

```consumable
items:
  - label: "Hexenmeister Zauberplätze"
    state_key: warlock_slots
    uses: 2
    reset_on:
      - event: short-rest  # Complete reset on short rest
      - event: long-rest   # Complete reset on long rest
```

Zaubertricks:  
[[Kalte Hand]]
[[Schauriger Strahl]]
[[Thaumaturgie]]

Zauber Grad 1:  
[[Verwünschen]] 
[[Arme von Hadar]]
[[Dissonantes Flüstern]]
[[Vertrauten finden]]
[[Höllischer Tadel]]

Zauber Grad 2:  
[[Gedanken wahrnehmen]]


# Inventory

Items:
 - [[Kette (10 feet)]]
 - [[Seil]]


# Connections

hier stehen Connections

# Relationships

hier stehen Beziehungen