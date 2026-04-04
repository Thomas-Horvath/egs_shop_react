# Electric Guitar Shop Frontend

Az Electric Guitar Shop egy fiktív hangszerbolt és webáruház frontend alkalmazása. A projekt egy full-stack rendszer kliensoldali része, amely React alapokon valósítja meg a termékböngészést, a keresést, a szűrést, a kosárkezelést, a felhasználói hitelesítést, valamint a rendelési és profilkezelési folyamatokat.

## Élő demó

- Weboldal: [electricguitarshop.eu](https://thomas-horvath.github.io/EGS_shop_client)

## Projekt célja

A projekt célja egy modern, reszponzív, többoldalas e-kereskedelmi felület elkészítése volt, amely valós API-kapcsolaton keresztül kommunikál a backend szolgáltatásokkal, és a felhasználó számára teljes vásárlási folyamatot biztosít a termékek böngészésétől a rendelés leadásáig.

## Főbb funkciók

### Termékkezelés

- termékek listázása kategóriák és alkategóriák szerint
- akciós termékek külön megjelenítése
- termék részletes adatlap külön oldalon
- szűrés márka, szín és modell alapján
- rendezés ár és név szerint
- lapozás nagyobb terméklisták esetén

### Keresés

- keresés terméknév, márka, kategória és alkategória alapján
- találatok külön oldalon történő megjelenítése

### Kosár és rendelés

- termék kosárba helyezése egyedi darabszámmal
- kosár tartalmának módosítása és törlése
- kosár állapotának mentése `localStorage`-ba
- automatikus átirányítás pénztárhoz vagy bejelentkezéshez
- rendelés leadása profiladatok alapján előtöltött szállítási adatokkal
- rendelési előzmények és rendelésrészletek megtekintése

### Felhasználókezelés

- regisztráció kliensoldali validációval
- bejelentkezés JWT tokennel
- munkamenet-kezelés `sessionStorage` használatával
- profiladatok megjelenítése és frissítése
- szállítási címek kezelése
- jelszómódosítás
- profil törlése

### Egyéb funkciók

- hírlevél-feliratkozás
- statikus információs oldalak
- kapcsolat oldal
- cookie-kezelő komponens

## Technológiai háttér

### Frontend

- React 18
- Create React App
- React Router DOM v6
- Context API
- JavaScript (ES6+)
- HTML5
- CSS3

### Külső csomagok

- `swiper` - kiemelt tartalmak és slider elemek
- `react-icons` - ikonok
- `react-paginate` - lapozás
- `jwt-decode` - JWT token feldolgozás
- `libphonenumber-js` - telefonszám kezeléshez kapcsolódó segédcsomag
- `@fortawesome/*` - további ikonkezelés
- `gh-pages` - GitHub Pages deploy

## Architektúra röviden

A projekt komponensalapú felépítést követ. Az alkalmazás fő állapotkezelése három külön Context-en keresztül történik:

- `AuthContext` - bejelentkezési állapot és tokenkezelés
- `CartContext` - kosár műveletek, darabszám kezelés, checkout navigáció
- `SearchContext` - keresőkifejezés globális megosztása

Az útvonalkezelést a `HashRouter` biztosítja, ami GitHub Pages környezetben különösen praktikus megoldás. Az alkalmazás külső backend API-hoz csatlakozik, amelyet környezeti változó segítségével ér el.

## Projektstruktúra

```text
src/
  assets/                      statikus képek, bannerek, segédadatok
  components/                  újrafelhasználható UI és üzleti komponensek
    HeaderSection/             fejléc, navigáció, kereső, login elemek
    HomePageSections/          nyitóoldali blokkok
    LoginComponents/           bejelentkezés, regisztráció, jelszókezelés
    ProductFilter/             szűrési felület
    ProfileComponents/         profil és rendeléskezelő nézetek
  contexts/                    globális állapotkezelés
  pages/                       route-szintű oldalkomponensek
  App.jsx                      route-ok és provider struktúra
  index.js                     belépési pont
```

## Használt route-ok

Az alkalmazás főbb kliensoldali útvonalai:

- `/` - kezdőlap
- `/termékek/:category` - kategóriaoldalak
- `/termékek/keresés` - keresési találatok
- `/termékadatok/:id` - termék adatlap
- `/rendelés/kosár` - kosár
- `/rendelés/pénztár` - pénztár
- `/rendelés/bejelentkezés` - checkout előtti bejelentkezés
- `/profil/:category` - bejelentkezés, regisztráció, jelszókezelés
- `/fiókom/:category/:orderId?` - profil, rendeléseim, szerkesztés, címeim
- `/:links` - információs oldalak
- `/kapcsolat` - kapcsolat

## Környezeti változók

A projekt az alábbi környezeti változót használja:

```env
REACT_APP_API_URL=https://egs.thomasapi.eu
```

Fejlesztői környezetben hozz létre egy `.env` fájlt a projekt gyökerében ezzel az értékkel, vagy a saját backend URL-ednek megfelelően.

## Telepítés és futtatás

### Előfeltételek

- Node.js
- npm

### Telepítés

```bash
npm install
```

### Fejlesztői szerver indítása

```bash
npm start
```

Az alkalmazás alapértelmezetten a `http://localhost:3000` címen indul el.

### Production build

```bash
npm run build
```

### Tesztek futtatása

```bash
npm test
```

### Deploy GitHub Pages-re

```bash
npm run deploy
```

## Elérhető npm scriptek

- `npm start` - fejlesztői szerver indítása
- `npm run build` - production build készítése
- `npm test` - tesztkörnyezet indítása
- `npm run deploy` - build publikálása GitHub Pages-re

## Demo felhasználó

Teszteléshez használható minta fiók:

- Felhasználónév: `testuser`
- Jelszó: `Password`

## Backend kapcsolat

A frontend REST API végpontokat használ többek között az alábbi folyamatokhoz:

- bejelentkezés
- regisztráció
- profil lekérdezés és módosítás
- terméklista és termékadatok lekérdezése
- rendelés leadása
- saját rendelések lekérdezése
- hírlevél-feliratkozás

## Kiemelt megvalósítási részletek

- a bejelentkezett állapot `sessionStorage` segítségével marad meg böngészőfül szinten
- a kosár tartalma `localStorage`-ba mentődik, így oldalfrissítés után is megmarad
- a pénztárfolyamat a profilból előtölti a szállítási adatokat
- a kategóriaoldalak dinamikus szűrőket építenek fel az adott terméktípus alapján
- a projekt GitHub Pages kompatibilitás miatt `HashRouter`-t használ

## Továbbfejlesztési lehetőségek

- automatizált tesztek bővítése
- újrafelhasználható API service réteg kialakítása
- részletesebb hibakezelés és felhasználói visszajelzések
- adminisztrációs felület integrálása
- teljesítményoptimalizálás és lazy loading

## Szerző

Thomas Horváth
