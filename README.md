# **Gruppexamination 2: Scrum, Git & GitHub i team**

**Grupper och redovisningstider:** [Se gruppindelningen här](https://docs.google.com/spreadsheets/d/1NkVkGaHUfUBU8YMdWOR9mEdUa_dChSqBWT8s3sPZwwI/edit?gid=848476790#gid=848476790)

Ni ska i **grupp** genomföra en **sprint med Scrum** och samarbeta med **Git och GitHub**. Ni planerar arbetet, följer det på en gemensam tavla och levererar via Pull Requests.

Examinationen har två delar:
1. **Skriftligt:** ett gemensamt GitHub-repo + `README.md` + länk till er tavla
2. **Muntligt:** gruppen redovisar muntligt på fredagen. Betyget sätts **individuellt**.

### **Viktigt innan ni börjar — vad som ger betyg**

**Det är Scrum-arbetet och Git-samarbetet som bedöms — inte koden.**

Koden är med flit enkel: varje user story kopplas till en färdig funktion i `index.html` som returnerar en textsträng. Lägg tiden på planering, tavla, dailies, Pull Requests och review.

Samarbete sker **via Pull Requests på GitHub**, inte genom att merga rakt in i `main` i terminalen.

All Scrum-dokumentation skrivs i `README.md`. Tavlan skapas i **Google Kalkylark eller Google Docs** och länkas i er README.

---

### **Dagsplan för sprinten**

Följ dagsplanen. Gör **inte** all kod på måndagen. Varje person gör **en user story på tisdagen och en på onsdagen**, så att era dailies har något att stämma av.

| Dag | Det här gör ni |
|-----|----------------|
| **Måndag** | **Sprintplanering.** Välj Scrum Master, skapa repo och tavla, skriv user stories och sprintmål (steg 1). Ingen kod idag. |
| **Tisdag** | **Daily 1.** Varje person gör sin **första** user story genom hela flödet: Pågår → branch → PR → review → merge → Klart (steg 2). Granska varandras PR:er. |
| **Onsdag** | **Daily 2.** Varje person gör sin **andra** user story genom hela flödet. |
| **Torsdag** | **Daily 3.** Merga de sista PR:erna. Håll retrospektivet (steg 4). Skriv svaren på teorifrågorna och era personliga reflektioner i `README.md`. |
| **Fredag** | Fixa det sista och förbered redovisningen. **Muntlig redovisning** på er grupps tid (se länken högst upp). Inlämning senast **kl. 23:59**. |

---

### **Instruktioner steg för steg**

#### **1. Förarbete & Sprintplanering (Måndag)**

1. **Fördela roller:**
   - **Scrum Master (SM):** leder era dailies och planeringen, ser till att tavlan hålls uppdaterad.
   - **Utvecklare:** alla i gruppen (även Scrum Master kodar).

2. **Skapa en tavla** i Google Kalkylark eller Google Docs med följande fem kolumner:
   `Backlog` → `Att göra (sprint)` → `Pågår` → `Granskning` → `Klart`  
   Ett kort representerar en User Story. Format på kortet: `[ID] · [AK] · [Funktion] · [Ansvarig]` (t.ex. `US-3 · AK-4 · funktion04 · Linus`). Se till att länken är delad så att läraren kan läsa den, och klistra in länken i `README.md`.

3. **Skriv user stories – minst 2 egna per person:**
   - **Format:** *Som en [roll] vill jag [funktion] för att [syfte].*
   - **Två färdiga exempel** får ni lägga i er backlog och använda. De räknas **inte** in i kravet på egna stories:
     - `US-1 · AK-1 · funktion01 · [Ansvarig]`: *Som en student vill jag se öppettiderna för att veta när jag kan fika.*
     - `US-2 · AK-2 · funktion02 · [Ansvarig]`: *Som en hungrig besökare vill jag se dagens kaka för att veta om jag ska gå dit.*
   - Varje person skriver **minst 2 egna** user stories, och varje person ansvarar för **minst 2 stories** i sprinten.
   - Tilldela varje egen story ett acceptanskriterium ur tabellen nedan (`AK-3`–`AK-15`) och koppla den till ett ledigt funktionsblock (`funktion03`–`funktion15`). `AK-1`/`AK-2` och `funktion01`/`funktion02` är reserverade för exemplen. Rör inga andra funktioner.
   - Skriv ett tydligt **sprintmål** i `README.md` (en mening som beskriver vad kaféets sida ska visa när sprinten är klar).

#### **2. Git-flöde & Samarbete (Tisdag–Torsdag)**

1. **Repo & Baslinje:** En person skapar ett gemensamt **publikt GitHub-repo**, lägger till övriga som **Collaborators** och pushar startfilen `index.html` samt er `README.md` till `main`. Övriga klonar repot (`git clone`).
   - Hämta startfilen här: **[index.html](https://github.com/linuszocom/examination_grupp_scrum_git/blob/main/index.html)** och spara den som `index.html`.
   - Varje funktion returnerar `""` från start och syns inte på sidan förrän den får en text. Exempel för AK-4 i `funktion04`:

   Före:
   ```js
   function funktion04() {
     return "";
   }
   visa(funktion04());
   ```

   Efter:
   ```js
   function funktion04() {
     return "Kaffe: 25 kr";
   }
   visa(funktion04());
   ```
2. **Arbeta på branch:**
   - Flytta ditt kort på tavlan från `Att göra` till `Pågår`.
   - Se till att stå på `main` och hämta senaste koden: `git switch main` följt av `git pull`.
   - Skapa din branch: `git switch -c feature/us-nummer-namn` (t.ex. `feature/us-1-oppettider`).
   - Öppna `index.html` och ersätt `""` med din text på `return`-raden i din tilldelade funktion. Spara och testa i webbläsaren.
   - Committa och pusha: `git add index.html`, `git commit -m "US-1: Beskrivning"`, `git push -u origin feature/us-nummer-namn`.
3. **Pull Request & Code Review:**
   - Öppna en Pull Request på GitHub (`base: main` ← `compare: din-branch`).
   - PR-titeln ska börja med storyns ID (t.ex. `US-1: Visa öppettider`). Ange acceptanskriteriet i beskrivningen.
   - Flytta kortet på tavlan till `Granskning`.
   - En **annan** person i gruppen granskar diffen under **Files changed**, skriver en konstruktiv inline-kommentar och godkänner via **Review changes → Approve**.
   - Efter Approve klickas **Merge pull request** på GitHub. Flytta kortet till `Klart`.

#### **3. Daily Standups (Tisdag, Onsdag, Torsdag)**

* Gruppen håller korta, fokuserade Daily Standups ledda av Scrum Master.
* Varje person svarar på:
  1. *Vad har jag gjort sedan igår?*
  2. *Vad ska jag göra idag?*
  3. *Har jag några hinder?*
* Dokumentera varje möte kortfattat i `README.md` (datum, deltagare, 1 rad per person).

#### **4. Retrospektiv (Torsdag)**

Håll ett kort retrospektiv när koden är på plats och fyll i `README.md`:
- **Start:** Något vi vill börja göra i framtida sprintar.
- **Stop:** Något som fungerade dåligt eller sinkade oss.
- **Continue:** Något vi gjorde riktigt bra och ska fortsätta med.
- **En konkret förbättring** vi tar med oss.

---

### **Acceptanskriterier (Kafé Commit)**

Välj **exakt ett** acceptanskriterium per User Story. Varje rad får användas högst en gång. AK-1 och AK-2 är reserverade för exempel-storiesna US-1 och US-2, egna stories använder AK-3–AK-15.

| AK | Sidan visar exakt |
|----|-------------------|
| AK-1 | **Öppet: 08–16** *(exempel US-1, funktion01)* |
| AK-2 | **Dagens kaka: kanelbulle** *(exempel US-2, funktion02)* |
| AK-3 | **Adress: Gitgatan 1** |
| AK-4 | **Kaffe: 25 kr** |
| AK-5 | **Wifi: kafe-gast** |
| AK-6 | **Telefon: 08-123 45 67** |
| AK-7 | **Nötter: nej** |
| AK-8 | **Parkering: 2 timmar gratis** |
| AK-9 | **Veckans erbjudande: kaffe + bulle 40 kr** |
| AK-10 | **Eventkväll: quiz torsdag kl. 18** |
| AK-11 | **Vegetariskt: dagens soppa** |
| AK-12 | **Betalning: Swish och kort** |
| AK-13 | **Kundkort: var tionde kaffe gratis** |
| AK-14 | **Tillgänglighet: rullstolsanpassat** |
| AK-15 | **Uteservering: öppen maj–sep** |

---

### **README-mall**

Kopiera detta format till er `README.md`:

```markdown
# Kafé Commit — Grupp [nr]

## Roller
- Scrum Master: [Namn]
- Utvecklare: [Alla gruppens namn]

## Tavla
Länk till Google Kalkylark/Docs: [Klistra in länk här]

## Sprintmål
När sprinten är klar ska kaféets startsida visa …

## Daily standups
### [Datum 1 - Tisdag]
- [Namn]: gjort … / gör nu … / hinder …
### [Datum 2 - Onsdag]
- [Namn]: gjort … / gör nu … / hinder …
### [Datum 3 - Torsdag]
- [Namn]: gjort … / gör nu … / hinder …

## Retrospektiv
- Start:
- Stop:
- Continue:
- Konkret förbättring:

## Teorifrågor
(svara på frågorna under Teorifrågor)

## Personlig reflektion
### [Namn]
(2–3 meningar)
### [Namn]
(2–3 meningar)
```

---

### **Klart-check (gruppen)**

Allt nedan ska vara klart vid inlämningen fredag kl. 23:59. Ni behöver inte vara helt klara före redovisningen.

- [ ] Ett gemensamt **publikt** GitHub-repo, med alla inbjudna
- [ ] Kanbantavla med kolumnerna Backlog → Att göra (sprint) → Pågår → Granskning → Klart, länkad i README
- [ ] Minst **2 egna user stories per person** (utöver exemplen US-1 och US-2) med ID, story, acceptanskriterium ur listan, funktion och ansvarig
- [ ] Varje person är ansvarig för minst **2 stories** i sprinten
- [ ] Roller och sprintmål i README
- [ ] Varje story i sprinten har en egen branch och en **Pull Request** med storyns ID i titeln
- [ ] **Varje student** har minst **två mergade PR:er** som **någon annan** godkänt (Approve)
- [ ] Minst **3 dailies** dokumenterade i README
- [ ] Retrospektiv (Start / Stop / Continue + en förbättring) i README
- [ ] Svar på teorifrågorna i README
- [ ] En personlig reflektion från **varje person** i README
- [ ] Sidan visar alla stories som ligger i **Klart**

**På GitHub:** under **Pull requests → Closed** ska de mergade PR:erna synas, med en approve-review. Under **Commits** på `main` ska gruppens arbete synas. **På tavlan:** korten i Klart ska motsvara mergade PR:er.

---

### **Teorifrågor (README, gemensamt)**

Svara tillsammans. Ungefär **2–4 meningar per fråga**.

1. Vad är **agil utveckling**, och vad i ert arbetssätt den här veckan var agilt?
2. Vilka Scrum-roller och moment använde ni (till exempel Scrum Master, daily, sprint och retrospektiv)? Beskriv hur de fungerade i er grupp.
3. Beskriv hur en user story gick från `Att göra` till `Klart` hos er, med branch, Pull Request, review och merge.
4. Vad är en **merge-konflikt**, när uppstår den och hur löser man den på GitHub? Ge ett exempel med en funktion i `index.html`. Om ni fick en konflikt under veckan, beskriv den.

**Personlig reflektion (README, var och en):**  
Varje person skriver 2–3 meningar under sitt eget namn: *Vad har du lärt dig om att jobba i team med Git och Scrum den här veckan, och vad tar du med dig till nästa gång?*

---

### **Lämna in**

- Länk till gruppens GitHub-repo i Moodle senast **fredag kl. 23:59**. Ni får justera README och tavla fram till dess, även efter redovisningen.
- Länken till kanbantavlan ska finnas i README

---

### **Betyg**

Gruppexaminationen bedöms med **G** eller **IG**. Det går inte att få VG på en gruppexamination; VG kan ni få på de individuella examinationerna.

#### **Godkänt (G)**

- Allt under "Instruktioner steg för steg" och Klart-check är uppfyllt.
- Historiken och tavlan visar att alla bidragit. Varje student har minst två mergade PR:er som någon annan godkänt.
- **Muntligt:** du ger en **övergripande** förklaring av din PR, din roll och hur sprinten gick till när läraren frågar dig.
