# Wypchnięcie na GitHub — repo już utworzone ✅

Repozytorium jest gotowe na Twoim koncie:
**https://github.com/adam420412/sbu-city-website** (publiczne, puste, branch `main`).

Pozostaje wgrać pliki. Wybierz jedną z dwóch metod — obie wgrywają **komplet z wideo**.

---

## Metoda A — bez terminala (najprościej) 🖱️

1. Wejdź na **https://github.com/adam420412/sbu-city-website**
2. Kliknij **„uploading an existing file"** (link na środku pustego repo)
   lub **Add file → Upload files**.
3. Otwórz folder `Desktop/SBU/sbu-city-website` i **przeciągnij do okna przeglądarki
   całą zawartość** — czyli `index.html`, `assets/` (z podfolderami), `polityka-prywatnosci.html`,
   `regulamin.html`, `README.md`, `sitemap.xml`, `robots.txt` itd.
   GitHub zachowa strukturę folderów.
4. Na dole wpisz opis commita (np. „SBU CITY — strona inwestycji") i kliknij **Commit changes**.

> Największy plik (`assets/video/hero.mp4`, ~14 MB) mieści się w limicie przeglądarki (25 MB).

---

## Metoda B — terminal / git (jedno wklejenie) ⌨️

```bash
cd ~/Desktop/SBU/sbu-city-website
rm -rf .git                      # czyści wcześniejszy, niekompletny zalążek
git init
git add -A
git commit -m "SBU CITY — strona inwestycji"
git branch -M main
git remote add origin https://github.com/adam420412/sbu-city-website.git
git push -u origin main
```

Przy pierwszym `git push` GitHub poprosi o zalogowanie (otworzy przeglądarkę
lub poprosi o token) — to normalne, potwierdź swoim kontem `adam420412`.

---

## Po wgraniu — darmowy podgląd online (GitHub Pages)

1. Repo → **Settings → Pages**
2. *Source*: **Deploy from a branch** → *Branch*: **main** / **/(root)** → **Save**
3. Po chwili strona będzie pod: `https://adam420412.github.io/sbu-city-website/`
   (świetny link „do wglądu" do wysłania).

---

## Zanim wyślesz dalej — do ustawienia
- **Klucz formularza** `WEB3FORMS_KEY` w `index.html` (bez niego działa `mailto:` na oba adresy).
- **Domena** w meta / `sitemap.xml` / `robots.txt` (teraz placeholder `sbucity.pl`).
- **Dokumenty prawne** (`polityka-prywatnosci.html`, `regulamin.html`, klauzula RODO) —
  to wzory; przed publikacją zweryfikuj z prawnikiem/IOD.
