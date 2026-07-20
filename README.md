# CITY SBU — strona inwestycji

Strona internetowa (one-page) nowoczesnej inwestycji **CITY SBU** — kompleksu modułów
magazynowo-biurowych w formacie *Small Business Unit* w Zabrzu przy ul. Lompy.

Statyczna strona bez frameworków i bez procesu budowania — czysty **HTML + CSS + JavaScript**.
Otwiera się bezpośrednio w przeglądarce, hostuje na dowolnym serwerze statycznym
(GitHub Pages, Netlify, Vercel, zwykły hosting).

---

## Zawartość strony

- **Dwujęzyczność PL / EN** — przełącznik w menu (wybór zapamiętywany w przeglądarce)
- **Hero z wideo z drona** (wyciszone, zapętlone, start od 15 s) + poster
- Pasek kluczowych liczb inwestycji
- **O projekcie** i opis formatu **SBU**
- **Specyfikacja modułu** (metraże z dokumentacji hal A i B)
- **Interaktywny plan sytuacyjny** — klikalne moduły A1–A4 i B1–B9 ze statusem i metrażem (SVG), z podpowiedzią (tooltip) po najechaniu
- **Rzuty parteru** — interaktywny podgląd rzutów Hala A / Hala B (z lightboxem)
- **Proces najmu** (6 kroków)
- **Kinowy przelot dronem** — wideo scrubbowane scrollem (desktop), zwykły odtwarzacz na mobile
- **Postęp inwestycji** — przeciągany suwak „przed / po budowie" + oś czasu etapów (paź 2025 → mar 2026)
- **Galeria** zdjęć z drona (lightbox)
- **Lokalizacja i dojazd** z mapą (OpenStreetMap)
- **Do pobrania** — rzuty, schemat dostępności i karta oferty (PDF)
- **FAQ** (rozwijane)
- **Formularz kontaktowy** (Web3Forms z fallbackiem `mailto:`)
- **RODO**: baner cookies + strona polityki prywatności
- **Sticky CTA + WhatsApp** na mobile
- **SEO**: pełne meta, Open Graph/Twitter, dane strukturalne (schema.org), `sitemap.xml`, `robots.txt`, favicon

Detale „wow": ekran startowy (preloader) z licznikiem, pasek postępu przewijania,
kinetyczny pasek haseł (marquee), własny kursor + magnetyczne przyciski + świetlny
spotlight w ciemnych sekcjach (desktop), efekt 3D tilt na kartach oraz podpowiedzi na planie.
Efekty desktopowe wyłączają się automatycznie na urządzeniach dotykowych i przy
`prefers-reduced-motion`.

Tłumaczenia EN znajdują się w obiekcie `T` w skrypcie; aby dodać/poprawić tekst EN, edytuj tę mapę.

---

## Konfiguracja przed publikacją

Dane firmy i kontaktowe są już **wpisane** (City SBU Sp. z o.o.; komercjalizacja: Karolina
Pawełczak, kontakt inwestora: Wojciech Urbańczyk — tylko e-mail). Do ustawienia zostają:

| Co | Gdzie | Obecnie |
|----|-------|---------|
| **Klucz formularza** (żeby zapytania szły na e-mail) | `const WEB3FORMS_KEY=''` w `index.html` | pusty → działa fallback `mailto:` (na oba adresy) |
| **Domena** | meta `og:url`, `canonical`, `sitemap.xml`, `robots.txt` | `https://sbucity.pl/` (placeholder) |
| **Data / drobne pola** | `polityka-prywatnosci.html`, `regulamin.html` (pola `[…]`) | do uzupełnienia + weryfikacja prawna |

**Formularz — darmowy klucz Web3Forms (ok. 30 s):** wejdź na https://web3forms.com,
podaj e-mail odbiorczy (np. `kontakt@karolinapawelczak.pl`), skopiuj `Access Key`
i wklej do `WEB3FORMS_KEY`. Bez klucza formularz działa przez `mailto:` (wysyła do Karoliny, DW do Wojciecha).

> **Dokumenty prawne** (`polityka-prywatnosci.html`, `regulamin.html`, klauzula RODO w formularzu)
> to **wzory/szkice** przygotowane na podstawie przekazanych danych — przed publikacją należy je
> zweryfikować z osobą odpowiedzialną za ochronę danych/prawnikiem. To nie jest porada prawna.

---

## Struktura projektu

```
sbu-city-website/
├── index.html                 # cała strona (HTML + CSS + JS w jednym pliku)
├── polityka-prywatnosci.html  # strona RODO (wzór do uzupełnienia)
├── sitemap.xml
├── robots.txt
├── assets/
│   ├── favicon.svg
│   ├── img/                    # zdjęcia (zoptymalizowane pod web)
│   │   ├── aerial-01..09.jpg   # galeria z drona (mar 2026)
│   │   ├── context-01.jpg      # kadr do sekcji „O projekcie"
│   │   ├── before.jpg / after.jpg   # suwak przed/po
│   │   └── stage1..4.jpg       # oś czasu etapów
│   ├── plans/                  # rzuty hal (obrazy do podglądu)
│   │   ├── hala-a.jpg / .png
│   │   └── hala-b.jpg / .png
│   ├── downloads/              # pliki PDF do pobrania
│   │   ├── CITY-SBU_rzut_hala-A.pdf / hala-B.pdf
│   │   └── CITY-SBU_schemat-dostepnosci.pdf
│   └── video/
│       ├── hero.mp4            # wideo z drona 720p, wyciszone, od 15 s (~14 MB)
│       └── poster.jpg          # klatka-poster do wideo
├── README.md
├── GITHUB.md
├── .gitignore
└── LICENSE
```

---

## Uruchomienie lokalnie

Najprościej — otwórz `index.html` w przeglądarce.

Zalecane (poprawne ładowanie wideo i mapy) — lokalny serwer:

```bash
# Python 3
python3 -m http.server 8080
# następnie otwórz http://localhost:8080
```

---

## Dane modułów

Metraże pochodzą z rysunków „HALA 1 (B) PARTER" i „HALA 2 (A) PARTER":

| Hala | Moduły | Magazyn | Biuro (parter) |
|------|--------|---------|----------------|
| B (nr 1) | B1–B9 | 244,8–251,5 m² | 54 m² |
| A (nr 2) | A1–A4 | 244,8–251,5 m² | 49–54 m² |

Status dostępności ustawia się w obiekcie `MOD` w `index.html` (`status: 'free' | 'rented'`).

---

## Do uzupełnienia przed publikacją (TODO)

- [ ] Prawdziwe **dane kontaktowe** (e-mail, telefon) — obecnie placeholdery `kontakt@sbucity.pl`, `+48 000 000 000`
- [ ] **Logo** CITY SBU (obecnie sygnet tekstowy)
- [ ] Backend / usługa formularza (np. Formspree) zamiast `mailto:` — jeśli potrzebna wysyłka bez klienta poczty
- [ ] Potwierdzenie parametrów technicznych modułu (wysokość, bramy, media)
- [ ] Domena i hosting (np. GitHub Pages)
- [ ] Polityka prywatności / RODO przy formularzu

> Treści i część danych mają charakter roboczy/koncepcyjny — przed publikacją należy je zweryfikować z inwestorem.

---

© 2026 CITY SBU. Realizacja: Kamiński. Wszelkie prawa zastrzeżone.
