# Chanel Adoption Page — Implementation Guide

> **For the implementation Claude session.**
> Launch this session from `/Users/krzysztof/Documents/claude-workspace/projects/web-dev/chanel-adoption/`
> Instruction: *"Build the page described in IMPLEMENTATION_GUIDE.md"*

---

## What You Are Building

A static HTML adoption page for **Chanel** — a small German Shepherd mix in a shelter near Wrocław, Poland. The goal: one adoption by the right person.

This is a **proof of concept** using stock photos. Real Chanel photos and a YouTube video URL will be provided later to replace placeholders.

**Deliverables:**
1. `index.html` — the full page
2. `style.css` — all styles
3. `images/` — stock photos downloaded from Unsplash

---

## Tone: "Chanel Interviews You"

Every shelter page leads with compassion and guilt. This page leads with **confidence and personality**.

- Chanel speaks in first person
- She is selective, not desperate
- She has "requirements" — not the shelter listing "ideal adopter criteria"
- The adopter must qualify, not be persuaded
- Never sentimental. Never pleading. Warm only in unexpected moments.

**Do not use:** paw print icons, heart emojis, "give her a chance", "poor dog", "please help"
**Do use:** confident framing, direct language, slight wit, warmth earned through specificity

---

## Technical Spec

**Stack:** `index.html` + `style.css` only. No JavaScript except YouTube embed iframe. No frameworks, no build tools.

**Fonts (Google Fonts CDN):**
- Headings: `Oswald` (weight 400, 700) — bold, confident
- Body: `Inter` (weight 400, 500) — clean, readable

**Color palette:**
```
Background:      #FFFFFF
Text primary:    #111111
Text secondary:  #555555
Accent (gold):   #B8860B  — used sparingly: key words, borders, highlights
Section alt bg:  #F7F5F2
Dividers:        #E8E8E8
```

**Layout:**
- Mobile-first, max content width `720px`, centered
- Full-bleed hero (100vw, no max-width constraint)
- Generous white space — sections breathe
- No sidebar, no grid complexity — single column throughout

---

## Page Structure

Build these sections **in order**:

### 1. Hero
- Full-bleed image (100vw, min-height 85vh, object-fit: cover)
- Dark overlay (rgba 0,0,0,0.45) over photo
- Centered text in white:
  ```
  CHANEL
  Szukam właściwego człowieka.
  Nie byle jakiego.
  ```
- CTA button linking to `#wymagania`:
  ```
  Sprawdź, czy się kwalifikujesz ↓
  ```
- Stock photo: search Unsplash for `german shepherd dog portrait outdoor`
  Use first high-quality horizontal result. Mark with: `<!-- REPLACE: hero photo of real Chanel -->`

---

### 2. Kim jestem (Who I am)
- Section heading: `Kim jestem`
- Body copy:
  ```
  Mam na imię Chanel.

  Jestem mieszanką owczarka niemieckiego —
  małą jak na swoją rasę, ale z charakterem
  znacznie większym.

  Przeżyłam wypadek samochodowy.
  Wróciłam do zdrowia.
  I wiem teraz, czego chcę od życia.

  Na początku jestem ostrożna. Obserwuję. Oceniam.
  Ale kiedy zdecyduję, że ktoś jest wart mojego zaufania —
  jestem jego. Bez reszty.

  Kocham spacery (długie, nie symboliczne).
  Kocham zabawki. Lubię kiedy jest coś do roboty.
  I potrafię sprawić, że zaśmiejesz się z mojego wyglądu —
  to mieszanka, która wyszła... oryginalnie.
  ```
- Place a secondary photo (landscape) below or beside the text
  Stock: search `dog playing toy grass happy`
  Mark: `<!-- REPLACE: real Chanel personality photo -->`

---

### 3. Oceń mnie sam/a (Video)
- Section heading: `Oceń mnie sam/a.`
- Subheading: `Słowa to jedno. Oto ja w akcji.`
- YouTube embed (responsive, 16:9 ratio):
  ```html
  <div class="video-wrapper">
    <iframe
      src="https://www.youtube.com/embed/VIDEO_ID"
      title="Chanel w akcji"
      frameborder="0"
      allowfullscreen>
    </iframe>
  </div>
  <!-- REPLACE: swap VIDEO_ID with real Chanel YouTube video URL -->
  ```
- CSS for responsive embed:
  ```css
  .video-wrapper {
    position: relative;
    padding-bottom: 56.25%;
    height: 0;
    overflow: hidden;
  }
  .video-wrapper iframe {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
  }
  ```
- Use `alt bg` color (`#F7F5F2`) for this section background

---

### 4. Moje wymagania (Requirements)
- `id="wymagania"` on this section (CTA button target)
- Section heading: `Moje wymagania`
- Intro paragraph:
  ```
  Nie szukam kogoś, kto mnie "uratuje".
  Szukam kogoś, kto podoła.
  ```
- Requirements list (use `◎` as bullet, styled with gold accent):
  ```
  ◎  Znać się na diecie psów z wrażliwym układem
     pokarmowym — i traktować ją poważnie

  ◎  Być gotowy/a na regularne wizyty weterynaryjne

  ◎  Mieć cierpliwość — zaufanie buduję stopniowo,
     nie na komendę

  ◎  Mieszkać w Polsce
     (Wrocław i okolice to plus — inne miasta do omówienia)

  ◎  Nie szukać łatwego psa.
     Szukać właściwego psa.
  ```
- Closing lines (italic, slightly smaller):
  ```
  Jeśli to nie Ty — bez urazy.
  Jeśli to Ty — czytaj dalej.
  ```

---

### 5. Co dostajesz w zamian (What you get)
- Section heading: `Co dostajesz w zamian`
- Body copy:
  ```
  Partnera na spacery, który nigdy nie odmawia.
  Kogoś, kto zawsze jest szczęśliwy, że wróciłeś/aś do domu.
  Psa, który po czasie zaskakuje — swoją energią,
  lojalnością i charakterem.

  Nie jestem łatwa.
  Ale jestem warta zachodu.
  ```
- Add a walking/action photo here
  Stock: search `dog walking leash path outdoor`
  Mark: `<!-- REPLACE: real Chanel action photo -->`

---

### 6. Schronisko za mną stoi (Shelter support)
- Section heading: `Schronisko za mną stoi`
- Use alt background `#F7F5F2`
- Body intro:
  ```
  Adoptując mnie, nie zostajesz z tym sam/a.
  ```
- Three support items (checkmark list, use `✓` styled in gold):
  ```
  ✓  Bezpłatna opieka weterynaryjna
  ✓  Wsparcie w adaptacji w nowym domu
  ✓  Kontakt z opiekunką, która zna mnie najlepiej
  ```
- Closing line:
  ```
  Masz pytania — oni mają odpowiedzi.
  ```

---

### 7. Kontakt (Contact / CTA)
- Section heading: `Gotowy/a na rozmowę kwalifikacyjną?`
- Body:
  ```
  Napisz do nas. Chanel oceni kandydaturę osobiście.
  ```
- Two contact elements:
  ```html
  <a href="mailto:REPLACE_EMAIL" class="btn-primary">Napisz do nas</a>
  <p class="contact-phone">Lub zadzwoń: <strong>REPLACE_PHONE</strong></p>
  ```
  Mark both with: `<!-- REPLACE: contact email / phone -->`
- Small footer note below:
  ```
  Chanel przebywa w schronisku w okolicach Wrocławia.
  ```

---

## CSS Guidelines

```css
/* Typography scale */
h1 (hero): 4.5rem, Oswald 700, uppercase, letter-spacing: 0.05em
h2 (section heading): 2rem, Oswald 400, uppercase, letter-spacing: 0.08em
h2 accent line: 3px solid #B8860B, width 40px, below heading
body: 1.125rem, Inter 400, line-height 1.8
small/caption: 0.9rem, Inter 400, color #555555

/* Sections */
padding: 80px 24px (desktop), 60px 20px (mobile)
max-width: 720px, margin: 0 auto

/* CTA Button */
background: #B8860B
color: #FFFFFF
padding: 16px 36px
font: Oswald 400, 1rem, uppercase, letter-spacing: 0.1em
border: none, no border-radius (sharp edges = confident)
hover: background #8B6914

/* Requirements list ◎ */
◎ symbol: color #B8860B, font-size 1.2em
indent: 2rem
spacing between items: 20px

/* Support list ✓ */
✓ symbol: color #B8860B
```

---

## Stock Photos Reference

| File | Unsplash search | Notes |
|------|----------------|-------|
| `images/hero.jpg` | `german shepherd dog portrait outdoor` | Horizontal, dog looking at camera |
| `images/personality.jpg` | `dog playing toy grass happy` | Energy and fun |
| `images/action.jpg` | `dog walking leash path outdoor` | Movement |

Download free from [unsplash.com](https://unsplash.com) — no attribution required for Unsplash photos used in this context.

Each `<img>` tag must have a `<!-- REPLACE: real Chanel photo -->` comment above it.

---

## Facebook Post Templates

Save these as `FACEBOOK_POSTS.md` in the same folder.

### Post 1 — Intro / personality hook
```
Poznajcie Chanel. Suczka, która sprawdza kandydatów. 🐾

Nie żartuję.

Chanel przeżyła wypadek samochodowy, wróciła do zdrowia
i wie dokładnie, czego chce od życia.
Na początku jest ostrożna — ale kiedy zdecyduje,
że ktoś jest wart jej zaufania, jest jego.
Bez reszty.

Szukamy dla niej kogoś, kto podoła.
Szczegóły + wymagania rekrutacyjne 😄 tutaj:
[REPLACE: page URL]
```

### Post 2 — Health transparency
```
Nie będziemy nic ukrywać.

Chanel wymaga szczególnej opieki.
Wrażliwy układ pokarmowy, ścisła dieta,
regularne wizyty u weterynarza.

To nie jest pies dla każdego.
To jest pies dla kogoś odpowiedzialnego —
kto rozumie, że prawdziwa opieka oznacza też
troskę w trudniejszych chwilach.

Schronisko oferuje bezpłatną opiekę weterynaryjną
i pełne wsparcie dla nowego właściciela.

Czy znasz kogoś, kto mógłby być jej człowiekiem?
[REPLACE: page URL]
```

### Post 3 — Share appeal
```
Nie musisz adoptować Chanel.
Ale możesz jej pomóc.

Jedno udostępnienie może dotrzeć do właściwej osoby.

Chanel czeka. 🐾
[REPLACE: page URL]
```

---

## Polish Facebook Adoption Groups (to post in)

During the implementation session, search the web for current active Polish Facebook groups. Prioritize:
- Groups for Dolny Śląsk / Wrocław region
- National Polish dog adoption groups
- Groups for dogs with special needs / health issues

Search terms: `"adopcja psów Polska" Facebook`, `"psy do adopcji Wrocław" Facebook`, `"psy specjalnej troski adopcja" Facebook`

List the top 10 groups with their URLs in `FACEBOOK_POSTS.md`.

---

## Photo Brief (for real Chanel photos — to replace PoC stock)

| # | Filename | Description |
|---|---------|-------------|
| 1 | `hero.jpg` | Chanel looking at camera. Confident expression. Natural light, outdoors. Horizontal 16:9. Most important. |
| 2 | `personality.jpg` | Playing with toy — energy, happy, fun side |
| 3 | `action.jpg` | Walking/running on leash, tongue out if possible |
| 4 | `face.jpg` | Close-up face — eyes, expression, emotional |
| 5 | `human.jpg` | With a trusted person showing affection — proves she bonds |

**Tips:** Natural/outdoor settings, avoid shelter backgrounds, multiple takes each.

**Video:** 1-2 min YouTube clip showing personality progression: walking → playing → close contact with trusted person.

---

## Deployment

1. Verify `index.html`, `style.css`, `images/` folder all present
2. Go to [netlify.com/drop](https://app.netlify.com/drop)
3. Drag the entire `chanel-adoption` folder onto the page
4. Netlify generates a URL instantly (free, no account needed)
5. Share URL with Kris for review
6. After review: replace stock photos with real Chanel photos, add YouTube URL, add contact details → redeploy

---

## Replacements Checklist

When real assets are available, replace all these before launch:

- [ ] `images/hero.jpg` → real Chanel hero photo
- [ ] `images/personality.jpg` → real Chanel personality photo
- [ ] `images/action.jpg` → real Chanel action photo
- [ ] YouTube `VIDEO_ID` → real Chanel YouTube video ID
- [ ] `REPLACE_EMAIL` → shelter contact email
- [ ] `REPLACE_PHONE` → shelter contact phone
- [ ] All `<!-- REPLACE -->` comments resolved
