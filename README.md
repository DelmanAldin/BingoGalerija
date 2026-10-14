# Bingo Galerija

Interna evidencija IT opreme po objektima (serveri, switchevi, ruteri, provideri, IP adrese).
Radi na računaru i na mobitelu, a na mobitelu se može dodati na početni ekran kao aplikacija.

## Sadržaj repozitorija

```
index.html              ← cijeli program
bg_data.json            ← sve izmjene iz Management moda
manifest.webmanifest    ← podaci za "Dodaj na početni ekran"
icons/                  ← ikone aplikacije
oprema/                 ← slike opreme (npr. HPE_ML30_Gen11.png, HPE_ML30_Gen11_comp.jpg)
slike/                  ← fotografije objekata (npr. 088a.jpg, 088b.jpg, bp01a.jpg)
.nojekyll               ← obavezan, ne brisati
```

## Postavljanje na GitHub Pages (jednom)

1. Na github.com napravi novi **Public** repozitorij, npr. `bingogalerija`.
2. Ubaci sve datoteke i foldere iz ovog paketa (Add file → Upload files, ili GitHub Desktop).
3. Ubaci svoje slike opreme u `oprema/` i fotografije objekata u `slike/`.
4. Settings → Pages → Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)** → Save.
5. Nakon 1–2 minute aplikacija je na `https://<korisnik>.github.io/bingogalerija/`.

## Snimanje izmjena s GitHuba

GitHub Pages ne prima upis direktno, pa aplikacija snima preko GitHub API-ja.
Pri prvom snimanju u Management modu traži **lični token**:

1. GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token
2. Repository access: **Only select repositories** → odaberi `bingogalerija`
3. Permissions → Repository permissions → **Contents: Read and write**
4. Kopiraj token i zalijepi ga kad aplikacija pita.

Token se čuva samo na tom uređaju (telefon i računar unose ga svaki posebno), nikad u repozitoriju.
Svako snimanje je jedan commit, pa je historija svih izmjena vidljiva u repozitoriju (History za `bg_data.json`),
a svaka stara verzija se može vratiti. Ostali uređaji vide izmjenu za oko minut.

## Napomene

- **Velika i mala slova u imenima su bitna** na GitHubu. Program ih sam usklađuje kad nađe datoteku,
  ali je najsigurnije zadržati ista imena kao na uredskom serveru.
- Repozitorij je javan: sve što je u njemu (adrese, IP adrese, telefoni, slike) može vidjeti svako ko zna adresu.
- Ista `index.html` radi i na uredskom serveru (`bingo_server.js`) — tamo se fotografije čitaju iz glavnog foldera,
  kao i dosad, a izmjene se snimaju na server.
