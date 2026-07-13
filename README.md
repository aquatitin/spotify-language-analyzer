# 🎵 Analitzador de Llengües de Spotify

Aplicació web que analitza els teus fitxers de dades de Spotify i et mostra en quines llengües són les cançons que escoltes. També inclou un cercador per consultar la llengua d'una cançó concreta (p. ex. «Sort de tu» d'Oques Grasses → català).

## 💡 Com resol el problema de la base de dades

No existeix cap base de dades pública que relacioni cançó i llengua, així que l'aplicació la construeix al vol:

1. **Obté la lletra** de cada cançó des de [LRCLIB](https://lrclib.net), una base de dades de lletres oberta, gratuïta i sense clau d'API.
2. **Detecta la llengua** de la lletra amb [franc-all](https://github.com/wooorm/franc), un detector estadístic d'idiomes (n-grames) que s'executa al navegador i cobreix més de 400 llengües (incloses les minoritzades com el basc o el gallec). Com que analitza el text complet de la lletra, retorna la **llengua majoritària** de la cançó. Per a les llengües fàcilment confusibles (català, castellà, gallec, portuguès, italià, francès, basc, anglès), un segon pas desempata els candidats comptant paraules funcionals molt distintives de cada llengua («i», «amb», «perquè»… per al català; «y», «pero», «corazón»… per al castellà; «eta», «ez», «zure»… per al basc).
3. **Desa els resultats** en una memòria cau local (`localStorage`) perquè les anàlisis següents siguin instantànies i no es repeteixin consultes.

Les cançons sense lletra a LRCLIB es classifiquen com a «Desconeguda», i les marcades com a instrumentals, com a «Instrumental».

## ✨ Característiques

- 📊 Analitza el teu historial complet (o les 100/250/500/1.000 cançons més escoltades)
- 🔍 Cercador individual: escriu títol i artista i et diu la llengua (amb el repartiment si la cançó és bilingüe, p. ex. «Català 60% · Castellà 40%»)
- 🌍 Reconeix més de 35 llengües (català, castellà, anglès, francès, gallec, basc, japonès, coreà…)
- 📈 Percentatges, recompte de cançons, reproduccions i temps d'escolta per llengua
- 📅 Evolució per anys: com canvia el percentatge de cada llengua al llarg del temps
- 🎤 Rànquing dels teus artistes més escoltats amb la seva llengua
- ✨ Curiositats: cançó i artista més escoltats, any més musical, la llengua que més repeteixes…
- 📥 Exportació dels resultats en CSV (amb minuts escoltats per cançó)
- 🌙 Mode clar i fosc automàtic
- 🔒 Tot s'executa al navegador: les teves dades no s'envien a cap servidor

## 📖 Com usar-ho

1. **Demana les teves dades a Spotify:**
   - Ves a [spotify.com/account/privacy/](https://www.spotify.com/account/privacy/)
   - Demana les teves dades (poden trigar uns dies)
   - Descarrega el ZIP i extreu-ne els fitxers JSON

2. **Puja els fitxers a l'aplicació.** S'accepten tots aquests formats:
   - `Streaming_History_Audio_*.json` (historial estès)
   - `StreamingHistory_music_*.json` (historial simple)
   - `endsong_*.json` (exportacions antigues)
   - `YourLibrary.json` (cançons desades)

3. **Clica «Analitza les llengües»** i espera que acabi (les reproduccions de menys de 10 segons i els pòdcasts es descarten automàticament).

## 🛠️ Tecnologies

- **Frontend:** HTML + CSS + JavaScript sense dependències de compilació (un sol fitxer, `index.html`)
- **Lletres:** [LRCLIB API](https://lrclib.net/docs) (oberta, sense autenticació, amb CORS)
- **Detecció d'idioma:** [franc-all](https://github.com/wooorm/franc) carregat com a mòdul ES des de CDN, més un desempat per paraules distintives

## 🔧 Ús local

```bash
git clone https://github.com/aquatitin/spotify-language-analyzer.git
cd spotify-language-analyzer
# Serveix el fitxer amb qualsevol servidor estàtic, per exemple:
python3 -m http.server 8000
# i obre http://localhost:8000
```

## 🌐 Desplegament a GitHub Pages

Settings → Pages → branca `main`, carpeta `/root`. En ser una pàgina 100% estàtica no cal cap backend.

## ⚠️ Nota de privadesa

- ✅ Les teves dades de Spotify es processen **localment** al navegador
- ✅ Només s'envien a LRCLIB els noms de cançó i artista per obtenir-ne la lletra
- ✅ No es guarda cap informació dels teus hàbits d'escolta fora del teu navegador

---

Fet amb ❤️ a Catalunya
