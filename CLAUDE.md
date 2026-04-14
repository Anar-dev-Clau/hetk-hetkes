# CLAUDE.md — Hetk Hetkes

## Projekti ülevaade
Kiire ideede salvestamise PWA mobiilile. Pilt + häälkommentaar + vabatahtlik tekst.
Eesmärk: maksimaalne kiirus ja lihtsus, null hõõrdumist.

## Arhitektuur
- **Tüüp:** PWA, üks HTML fail + manifest.json + sw.js
- **Andmesalvestus:** IndexedDB (pildid + heli base64-na), localStorage (seadistused)
- **Backend:** puudub — 100% lokaalne, offline-first
- **Keel:** Eesti UI, inglise kood
- **Platvorm:** mobiil (iOS + Android), Chrome/Safari

## Failid
```
index.html      ← kogu rakenduse loogika ja UI
manifest.json   ← PWA manifest
sw.js           ← service worker (offline tugi)
CLAUDE.md       ← see fail
```

## Praegune seis
**Versioon: 0.1 — Esimene toimiv versioon**

### Valmis:
- [x] Avakuva (count, viimane idee eelvaade)
- [x] Kaamera avamine (front/back)
- [x] Pildistamine koos flash efektiga
- [x] Häälsalvestus (käsitsi start/stop, taimer)
- [x] Salvestuse kuulamine enne salvestamist
- [x] Vabatahtlik tekstikommentaar
- [x] IndexedDB salvestamine
- [x] Galerii (kronoloogiline, kaardi vaade)
- [x] Detail kuva (pilt + hääl + kommentaar)
- [x] Kustutamine koos kinnitusega
- [x] PWA manifest + service worker
- [x] Offline tugi

### Lahtised / järgmised sammud:
- [ ] PWA ikoonid (icon-192.png, icon-512.png) — vaja luua
- [ ] manifest.json lisada index.html <head> sektsiooni
- [ ] sw.js registreerimine lisada index.html <script> sektsiooni
- [ ] iOS Safari testimine (MediaRecorder tugi)
- [ ] Eksport funktsioon (ZIP või jagamine)
- [ ] Otsing galeriis

## Kriitilised reeglid
- ÄRA muuda IndexedDB skeemi ilma migratsioonita
- ÄRA lisa väliseid teeke ilma vajaduseta
- ÄRA lisa pilve/network funktsioone — rakendus peab töötama 100% offline
- Hoia kõik ühes HTML failis (v.a. manifest.json ja sw.js)
- Eesti UI tekst, inglise muutujad/kommentaarid koodis

## Teadaolevad piirangud
- iOS Safari: MediaRecorder ei pruugi toetada audio/webm — tuleb testida
- Väga suured pildid võivad aeglustada IndexedDB-d — piltide kompressioon 0.82 JPEG
- IndexedDB maht: ~200 ideed (pilt ~150KB + heli ~200KB) ≈ ~70MB kokku

## Lukupunktid
- **v0.1** — esimene toimiv versioon (praegune)
