# 🎵 Analitzador d'Idiomes de Spotify

Aplicació web que analitza els teus arxius de dades de Spotify i et mostra el percentatge de cançons que escoltes en cada idioma.

## ✨ Característiques

- 📊 Analitza les primeres 100 cançons úniques dels teus arxius de Spotify
- 🌍 Detecta idiomes: català, castellà, anglès, francès, italià, portuguès, alemany, coreà, japonès i altres
- 🎯 Usa l'API oficial de Spotify per obtenir metadades reals (gèneres, mercats disponibles)
- 📈 Mostra percentatges i número de reproduccions per idioma
- 🔍 Llista detallada de cançons per cada idioma

## 🚀 Demo en viu

Disponible a: `https://el-teu-usuari.github.io/spotify-language-analyzer`

## 📖 Com usar-ho

1. **Demana les teves dades a Spotify:**
   - Ves a [spotify.com/account/privacy/](https://www.spotify.com/account/privacy/)
   - Desplaça't fins a "Descarrega les teves dades"
   - Demana les dades (poden trigar uns dies)
   - Descarrega el ZIP i extreu els arxius JSON

2. **Puja els arxius:**
   - Obre l'aplicació
   - Puja els arxius que comencin amb `Streaming_History` o similar
   - Clica "Analitzar Idiomes"

3. **Veu els resultats:**
   - Percentatge de cançons per idioma
   - Llista completa de cançons
   - Estadístiques de reproduccions

## 🛠️ Tecnologies

- **Frontend:** React (via CDN), Tailwind CSS
- **API:** Spotify Web API
- **Inspiració:** [Anna's Archive - Backing up Spotify](https://annas-archive.li/blog/backing-up-spotify.html)
- **Metadades:** Usa la base de dades de 199.9GB de metadata de Spotify d'Anna's Archive

## 📁 Estructura del projecte

```
spotify-language-analyzer/
├── index.html          # Frontend (aplicació React)
├── api/
│   └── analyze.js      # Backend serverless (opcional, per IA)
├── vercel.json         # Configuració Vercel
├── package.json        # Dependències
└── README.md          # Aquest fitxer
```

## 🔧 Instal·lació local

```bash
# Clonar el repositori
git clone https://github.com/el-teu-usuari/spotify-language-analyzer.git
cd spotify-language-analyzer

# Obrir index.html directament al navegador
open index.html
```

## 🌐 Desplegar a GitHub Pages

```bash
# 1. Puja el codi a GitHub
git add .
git commit -m "Afegir analitzador de Spotify"
git push origin main

# 2. Activa GitHub Pages
# Ves a Settings > Pages
# Selecciona: main branch, /root
# Guarda i espera uns minuts
```

## 🎯 Com funciona la detecció d'idiomes

L'aplicació usa múltiples estratègies per detectar l'idioma:

1. **Gèneres musicals:** Detecta etiquetes com "catalan", "spanish", "k-pop", "j-pop", "french", etc.
2. **Mercats disponibles:** Analitza en quins països es distribueix la cançó
3. **Metadades de l'artista:** Consulta la informació oficial de Spotify
4. **Fallback intel·ligent:** Si no detecta l'idioma, assumeix anglès per defecte

### Exemples de detecció:

- **Català:** Gènere "rumba catalana" o "catalan folk"
- **Castellà:** Gèneres "reggaeton", "latin pop", "urbano latino"
- **Coreà:** Gènere "k-pop" o "korean pop"
- **Japonès:** Gèneres "j-pop", "j-rock", "anime"

## 📊 Font de dades

Aquest projecte està inspirat pel treball d'Anna's Archive sobre backup de Spotify:
- 📝 [Blog post: Backing up Spotify](https://annas-archive.li/blog/backing-up-spotify.html)
- 💾 [Torrent de metadades](https://annas-archive.li/torrents#aa_misc_data) (199.9GB)
- 🔍 Conté informació de gèneres, popularitat, artistes i mercats per milions de cançons

## 🤝 Contribucions

Les contribucions són benvingudes! Si vols millorar la detecció d'idiomes o afegir noves funcionalitats:

1. Fes un fork del projecte
2. Crea una branca (`git checkout -b feature/millora`)
3. Fes commit dels canvis (`git commit -m 'Afegir millora'`)
4. Puja la branca (`git push origin feature/millora`)
5. Obre un Pull Request

## 📝 Llicència

MIT License - Lliure per usar, modificar i distribuir.

## 🙏 Agraïments

- **Anna's Archive** per la documentació i base de dades de metadades
- **Spotify** per l'API pública
- **Comunitat open source** per les eines usades

## ⚠️ Nota de privadesa

Aquesta aplicació:
- ✅ Processa les dades **localment** al teu navegador
- ✅ No envia les teves dades personals a cap servidor
- ✅ Només consulta l'API pública de Spotify amb els IDs de les cançons
- ✅ No guarda cap informació sobre els teus hàbits d'escolta

---

Fet amb ❤️ a Catalunya
