# 🚀 Deployment útmutató – Magyar FOXG1 Alapítvány weboldal

## Projekt struktúra

```
foxg1-alapitvany/
├── public/
│   ├── index.html     ← A weboldal HTML-je
│   ├── style.css      ← Stílusok
│   └── app.js         ← Interakciók
├── server.js          ← Node.js szerver
├── package.json       ← Függőségek
└── .gitignore
```

---

## 1. lépés – GitHub repo létrehozása

1. Menj a https://github.com oldalra, és jelentkezz be (vagy regisztrálj ingyen)
2. Kattints a **"New repository"** gombra (zöld gomb, jobb felül)
3. Töltsd ki:
   - **Repository name:** `foxg1-alapitvany`
   - **Description:** Magyar FOXG1 Szindróma Alapítvány weboldal
   - Legyen **Public** (szükséges a Render ingyenes tieréhez)
   - ✅ Add a README file – NEM kell (mi már csináltuk)
4. Kattints: **"Create repository"**

---

## 2. lépés – Kód feltöltése GitHubra

Ha még nincs telepítve a Git, töltsd le: https://git-scm.com/downloads

### Parancsok (Terminálban / Parancssorban):

```bash
# 1. Menj a projekt mappájába
cd foxg1-alapitvany

# 2. Inicializáld a git repót
git init

# 3. Csatold a GitHub repóhoz (cseréld ki YOUR_USERNAME-t a te GitHub neveddel!)
git remote add origin https://github.com/YOUR_USERNAME/foxg1-alapitvany.git

# 4. Adj hozzá minden fájlt
git add .

# 5. Commit
git commit -m "Első verzió – FOXG1 alapítvány weboldal"

# 6. Töltsd fel GitHubra
git push -u origin main
```

✅ Ha sikerült, látod a fájlokat a GitHub oldalon.

---

## 3. lépés – DigitalOcean App Platform beállítása

1. Menj a https://cloud.digitalocean.com oldalra és jelentkezz be
2. Bal oldali menüben kattints: **"App Platform"**
3. Kattints: **"Create App"**
4. Válaszd: **"GitHub"** → engedélyezd a DigitalOcean hozzáférését a GitHub fiókodhoz
5. Keressd meg és válaszd a **foxg1-alapitvany** repót
6. **Branch:** `main` ✅ | **Autodeploy:** bekapcsolva ✅
7. Kattints: **"Next"**

### Erőforrás beállítások:

A DigitalOcean automatikusan felismeri a Node.js projektet. Ellenőrizd:

| Mező | Érték |
|------|-------|
| **Type** | Web Service |
| **Run Command** | `npm start` |
| **HTTP Port** | 3000 |

Kattints: **"Next"**

### Plan (ár) kiválasztása:

- **Basic Plan – $5/hó** (legolcsóbb, tökéletes egy alapítványi oldalhoz)
- 512 MB RAM, 1 vCPU, Frankfurt régió ajánlott

Kattints: **"Next"** → **"Create Resources"**

⏳ Az első deployment 3-5 percig tart.

---

## 4. lépés – Az oldal él!

Ha minden rendben ment, megkapod az URL-t:
```
https://foxg1-alapitvany-xxxxx.ondigitalocean.app
```

✅ Az oldalad most nyilvánosan elérhető!

---

## 5. lépés – Automatikus frissítés

Mostantól **minden alkalommal, amikor pusholsz GitHubra**, a DigitalOcean automatikusan újraépíti és frissíti az oldalt!

```bash
# Ha módosítottál valamit:
git add .
git commit -m "Leírás a változtatásról"
git push
```

→ 2-3 perc múlva az éles oldalon is megjelenik a változás. 🎉

---

## 💡 Tippek

### Saját domain csatlakoztatása
Ha van saját domained (pl. `foxg1.hu`):
1. App beállításaiban: **"Settings"** → **"Domains"**
2. Add hozzá a domaint
3. A domain regisztrátornál állítsd be a CNAME rekordot a DigitalOcean által megadott értékre

### Képek hozzáadása
Tegyél képeket a `public/images/` mappába, és hivatkozz rájuk így az HTML-ben:
```html
<img src="/images/kep.jpg" alt="leírás" />
```

---

## 📞 Probléma esetén

- **GitHub:** https://docs.github.com
- **DigitalOcean App Platform:** https://docs.digitalocean.com/products/app-platform/
