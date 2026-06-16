# 🍹 Mocktail Studio

Community-gedreven platform voor alcoholvrije drankjes.

---

## 📖 Inhoudsopgave

- [Over het project](#over-het-project)
- [Functionaliteiten](#functionaliteiten)
- [Huisstijl](#huisstijl)
- [Toekomstige uitbreidingen](#toekomstige-uitbreidingen)

---

## Over het project

**Mocktail Studio** is een webapplicatie voor liefhebbers van alcoholvrije drankjes. Gebruikers kunnen zelf mocktailrecepten indienen, opgebouwd uit een vaste lijst van beschikbare ingrediënten. Elk recept krijgt een smaakprofiel mee dat door de indiener wordt opgegeven. Andere gebruikers kunnen recepten ontdekken, filteren, opslaan en beoordelen.

Het platform is volledig Nederlandstalig en gericht op een breed publiek: van beginners tot thuisbartenders.

---

## Functionaliteiten

### 🧾 Recepten indienen
Gebruikers stellen hun recept samen via een vaste ingrediëntenlijst. Ze zeggen welke hoeveelheid ze van elk ingrediënt nodig hebben. Als er een specifieke volgorde/bereidingswijze nodig is, kunnen ze die ook opgeven. Bij het indienen geven ze ook het smaakprofiel op (bijv. zoet, zuur, fruitig). Omdat gebruikers zelf recepten insturen, ontstaat automatisch een gevarieerd aanbod van alcoholvrije alternatieven voor klassieke cocktails.

### ⭐ Beoordelen
Andere gebruikers kunnen een recept beoordelen met een sterrenscore en een korte geschreven review. Ze kunnen ook stemmen op het smaakprofiel.

### 🔍 Filteren en zoeken
| Filter | Omschrijving |
|---|---|
| **Ingrediënten** | Filter op wat je in huis hebt |
| **Smaak** | Kies uit zoet, zuur, bitter, fruitig, kruidig of fris |
| **Zoekfunctie** | Zoek op naam, ingrediënt of smaak |

### 🏆 Mocktail van de Week
Op de homepage wordt wekelijks een uitgelicht recept getoond:
- Kandidaten: gepubliceerde recepten met minimaal 1 review en rating >= 3.5.
- Score combineert kwaliteit, review-trust, favorites en een verkenningsboost voor nieuwere / minder vaak beoordeelde recepten.
- Resultaat wordt per week vastgelegd in `weekly_features`.

### 📊 Moeilijkheidsgraad
Er zijn 3 moeilheidslevels:
- 🟢 **Makkelijk**: gewoon mixen en klaar
- 🟡 **Gemiddeld**: een beetje techniek vereist
- 🔴 **Barista-level**: voor de echte liefhebbers

- De submitter geeft initieel label.
- Dat telt voor 3 stemmen
- Elke community-vote telt als 1.
- Het label met hoogste score wordt `effective_difficulty`.

### 🎖️ Badges en achievements
Actieve gebruikers verdienen badges op basis van hun bijdragen:
- Eerste recept ingediend
- 10 beoordelingen gegeven
- Recept van de Week gewonnen
- En nog veel meer...

- Elke belangrijke actie schrijft een event naar `domain_events`.
- Badge processor leest events en kent badges toe zonder business logic hard in de request flow te veren.

### Smaakprofiel
- Submitter kiest smaakprofiel (zoet/zuur/bitter/fruitig/kruidig/fris).
- Gebruikers kunnen ook stemmen op het smaakprofiel.
- Submitter-tags tellen dubbel (`source=submitter`, factor 2.0).
- Community-votes tellen enkel (`factor 1.0`).
- Per recept berekenen we percentages per smaak.
- Smaken met >= 18% verschijnen als dominante tags.

### Shake to Surprise
Geeft een random recept volgens deze regels:
- Sluit recepten uit die echt slecht presteren: `avg_rating < 2.5` wanneer er minstens 3 reviews zijn.

### ❤️ Favorieten
Gebruikers kunnen recepten opslaan in hun persoonlijke favorietenlijst voor later gebruik.

### 🔗 Sociaal delen
Elk recept heeft een deelbare link zodat gebruikers hun creaties kunnen verspreiden via sociale media of messaging-apps.

---

## Huisstijl

Mocktail Studio heeft een speelse maar verfijnde uitstraling, geïnspireerd op de sfeer van een hippe alcoholvrije bar.

### Kleurenpalet

| Kleur | Gebruik | Hex |
|---|---|---|
| 🟠 Koraal/perzik | Primaire kleur, knoppen | `#FF6B6B` |
| 🟡 Amber/goud | Accenten, highlights | `#FFB347` |
| 🟢 Mintgroen | Frisse accenten, tags | `#A8E6CF` |
| ⚪ Off-white | Achtergrond | `#FAFAF7` |

### Typografie

- **Koppen:** Poppins of Nunito; rond, vriendelijk en modern
- **Bodytekst:** Clean sans-serif: maximale leesbaarheid

### Visuele elementen

- Illustratieve icoontjes per ingrediënt
- Glastype als visuele identiteit van elk recept
- Dashboard dat aanvoelt als een kleurrijk keukenblad

---

## Toekomstige uitbreidingen

De onderstaande functies zijn bewust buiten de eerste versie gehouden wegens implementatiecomplexiteit. Ze staan wel op de roadmap.

| # | Uitbreiding | Omschrijving |
|---|---|---|
| 1 | 🥗 **Voedingswaarde** | Calorieën en macronutriënten per recept tonen |
| 2 | 🤖 **AI-receptsuggesties** | Op basis van jouw beschikbare ingrediënten automatisch recepten voorstellen |
| 3 | 📷 **Foto uploaden** | Gebruikers kunnen een foto van hun versie van het recept toevoegen |
| 4 | 🖨️ **Printbare receptkaart** | Export van een recept als mooi opgemaakte PDF |
| 5 | 🌍 **Meertaligheid** | Uitbreiding naar Frans en Engels naast het Nederlandse basisplatform |

---

## 🚀 Status

> 🛠️ In ontwikkeling: eerste versie gemaakt (nog niet openbaar)

---

## Run lokaal (om te testen)
```bash
cd backend
python -m venv .venv
source venv/bin/activate  # (recommended)
pip install -r requirements.txt
uvicorn app.main:app --reload
```

Open daarna `http://127.0.0.1:8000`.

---

**Mocktail Studio** | *Bouw je eigen drankkaart, zonder alcohol.*