# StavPE – web

Jednoduchý jednostránkový web pro StavPE: sádrokartony, obklady a dlažby. Píše se v 1. osobě jednotného čísla (klient pracuje sám).
Provozovatel: Zdeněk Pechánek, IČO 88109534 (OSVČ, živnost Zednictví od 2011), Bystřická 1246, 432 01 Kadaň.
Kontakt: 775 716 002, z.pechanek@gmail.com.

Web je samostatný, záměrně bez odkazů na Planet Express a další firmy majitele.

## Stránky

- `index.html`: úvod, služby, postup, kontakt (vše na jedné stránce)
- `ochrana-osobnich-udaju.html`, `reklamace.html`, `404.html`

Logo je nápis STAVPE podle polepu na dodávce klienta (STAV béžová, PE hnědá, A bez příčky), překreslené jako SVG přímo ve stránkách.
Ilustrace v úvodu je vlastní řez sádrokartonovou příčkou. Písma Lexend Exa a Instrument Sans jsou uložená na webu.
Bez měření návštěvnosti (klient GoatCounter nechce). Klient je plátce DPH, DIČ je odvozené z rodného čísla, proto na webu záměrně není. Ceny na webu nejsou; pokud se doplní, uvádět včetně DPH.

## Doména stavpe.cz → GitHub Pages

DNS spravuje WebSupport (ns1/ns2.websupport.cz, ns3.websupport.eu). Stav 5. 10. 2026: stavpe.cz a www ukazují na hosting WebSupportu (37.9.175.212) s prázdným WordPressem.

Ve správě DNS u WebSupportu (admin.websupport.cz → doména stavpe.cz → DNS):

**Smazat** stávající záznamy pro web:

| Typ | Název | Hodnota |
|---|---|---|
| A | @ (stavpe.cz) | 37.9.175.212 |
| AAAA | @ (stavpe.cz) | 2a00:4b40:aaaa:2011::5 |
| A / AAAA / CNAME | www | 37.9.175.212 / 2a00:4b40:aaaa:2011::5 |

**Přidat:**

| Typ | Název | Hodnota |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | patrikfanta-cze.github.io. |

TTL nechat výchozí (nebo 600).

**Nesahat** na e-mail: MX (mailin1/mailin2.stavpe.cz), záznamy mailin1, mailin2, mail, webmail, autoconfig a TXT/SPF. E-mail na doméně dál poběží u WebSupportu.

Pokud WebSupport při změně nabídne „přesměrovat doménu na hosting“ nebo se A záznam nedá smazat, je potřeba web/doménu na hostingu odpojit (WordPress pak klidně zrušit, platí-li se za hosting).

**Po propagaci DNS** (ověřit `nslookup stavpe.cz` → 185.199.x.153):

1. přidat do repa soubor `CNAME` s obsahem `stavpe.cz` a v nastavení Pages zadat custom domain `stavpe.cz`,
2. počkat na certifikát a zapnout „Enforce HTTPS“,
3. přepsat adresy `patrikfanta-cze.github.io/stavpe-web` na `https://stavpe.cz` v canonical, og:url, JSON-LD, robots.txt, sitemap.xml a v `<base>` v 404.html (na `/`),
4. přepnout odkaz v referencích na patrikfanta-web.

Doporučeno: v GitHub účtu (Settings → Pages → Verified domains) ověřit doménu TXT záznamem `_github-pages-challenge-patrikfanta-cze`, aby ji nikdo jiný nemohl převzít.

## Otevřené body

- [x] Klient upravil služby 5. 10. 2026: bez zednických prací a rekonstrukcí, přidané kazetové podhledy, obklady a dlažby, texty v 1. osobě. Ještě potvrdí zbytek textů (hlavně „cena předem“).
- [ ] Logo ve vektoru od výrobce polepu, pokud existuje (teď překreslené podle fotky).
- [ ] Fotky realizací, případně doplnit galerii.
- [ ] Oblast působnosti (teď Kadaň, Klášterec nad Ohří, Chomutov a okolí).
- [ ] Doby uchování údajů v zásadách (navržené standardní: 1 rok / 3 roky / 10 let).
- [ ] Doména stavpe.cz (klientova, DNS u WebSupportu, teď na ní je prázdný WordPress). Plán: přesměrovat DNS na GitHub Pages (CNAME soubor + záznamy A/CNAME), WordPress nepoužívat. Pak přepsat github.io adresy v canonical, og:url, JSON-LD, robots.txt a sitemap.xml.
