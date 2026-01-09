# 📘 GUIDA: Pubblicare SMEMOPASS su GitHub Pages

## 🎯 Obiettivo
Pubblicare SMEMOPASS come PWA accessibile online tramite GitHub Pages.

---

## 📋 PREREQUISITI

✅ Account GitHub (già ce l'hai)
✅ Files della PWA (già creati)

---

## 🚀 PROCEDURA COMPLETA

### STEP 1: Creare il Repository

1. **Vai su GitHub**: https://github.com
2. **Login** con il tuo account
3. Clicca il pulsante **"+"** in alto a destra
4. Seleziona **"New repository"**

5. **Configura il repository**:
   - **Repository name**: `smemopass` (o nome a scelta)
   - **Description**: `Gestore password sicuro e offline con crittografia AES-256`
   - **Visibility**: 
     - ✅ **Public** (consigliato - PWA accessibile a tutti)
     - ⚠️ **Private** (solo tu puoi accedere, ma Pages funziona ugualmente)
   - ✅ Seleziona **"Add a README file"** (poi lo sostituirai)
   - **License**: Scegli una licenza (es: MIT, GPL, o nessuna)

6. Clicca **"Create repository"**

---

### STEP 2: Caricare i File

Hai 2 opzioni:

#### OPZIONE A - Upload via Web (Più Semplice)

1. Nel repository appena creato, clicca **"Add file" → "Upload files"**

2. **Trascina tutti questi file** nella pagina:
   ```
   📁 Files da caricare:
   ├── index.html
   ├── manifest.json
   ├── service-worker.js
   ├── README.md
   └── icons/
       ├── icon-192.png
       ├── icon-512.png
       ├── apple-touch-icon.png
       └── favicon.png
   ```

3. **Scroll in fondo** e clicca **"Commit changes"**

#### OPZIONE B - Upload via Git (Più Tecnico)

Se hai Git installato:

```bash
# 1. Clona il repository
git clone https://github.com/[tuo-username]/smemopass.git
cd smemopass

# 2. Copia tutti i file nella cartella
# (copia i file che ti ho preparato)

# 3. Aggiungi, committa e pusha
git add .
git commit -m "Initial commit - SMEMOPASS PWA"
git push origin main
```

---

### STEP 3: Attivare GitHub Pages

1. Nel tuo repository, vai su **"Settings"** (ingranaggio in alto)

2. Nel menu a sinistra, clicca **"Pages"**

3. In **"Source"**:
   - Branch: Seleziona **"main"** (o "master")
   - Folder: Seleziona **"/ (root)"**

4. Clicca **"Save"**

5. **Aspetta 1-2 minuti** mentre GitHub pubblica il sito

6. Vedrai un messaggio:
   ```
   ✅ Your site is published at https://[tuo-username].github.io/smemopass/
   ```

7. **Clicca sul link** per vedere la tua PWA online! 🎉

---

### STEP 4: Verifica e Test

1. **Apri il link** nel browser mobile e desktop

2. **Testa l'installazione PWA**:
   - **Android**: Menu → "Installa app"
   - **iOS**: Share → "Aggiungi a Home"
   - **Desktop**: Icona "Installa" nella barra indirizzi

3. **Testa offline**:
   - Installa l'app
   - Attiva modalità aereo
   - Apri l'app → dovrebbe funzionare!

4. **Testa le funzionalità**:
   - Crea password master
   - Aggiungi password
   - Fai backup
   - Importa backup
   - Verifica dashboard

---

## 🔒 CONFIGURAZIONI SICUREZZA (Opzionale ma Consigliato)

### Forzare HTTPS
GitHub Pages usa già HTTPS per default. Verifica:

1. Settings → Pages
2. ✅ "Enforce HTTPS" dovrebbe essere selezionato

### Custom Domain (Opzionale)
Se hai un dominio personale:

1. Settings → Pages → Custom domain
2. Inserisci: `smemopass.tuodominio.com`
3. Configura DNS del tuo dominio:
   ```
   Type: CNAME
   Name: smemopass
   Value: [tuo-username].github.io
   ```

---

## 📱 CONDIVIDERE LA TUA PWA

Una volta pubblicata, puoi condividere il link:

```
🔗 Link diretto:
https://[tuo-username].github.io/smemopass/

📱 Istruzioni per gli utenti:
1. Apri il link sul tuo smartphone
2. Clicca "Installa" quando richiesto
3. L'app apparirà nella tua home screen
4. Usa SMEMOPASS completamente offline!
```

---

## 🔄 AGGIORNARE LA PWA

Quando modifichi il codice:

### Via Web:
1. Vai al file su GitHub
2. Clicca l'icona matita (Edit)
3. Modifica il codice
4. Commit changes

### Via Git:
```bash
git add .
git commit -m "Descrizione modifiche"
git push origin main
```

### Aggiornare la Versione Service Worker:
Quando fai modifiche importanti, cambia la versione in `service-worker.js`:

```javascript
const CACHE_NAME = 'smemopass-v1'; // Cambia in v2, v3, etc.
```

Gli utenti vedranno un prompt per aggiornare l'app.

---

## 🐛 RISOLUZIONE PROBLEMI

### ❌ "404 - File not found"
- Controlla che `index.html` sia nella root
- Verifica che GitHub Pages sia attivato
- Aspetta 1-2 minuti dopo il primo deploy

### ❌ "PWA non installabile"
- Verifica che il sito sia HTTPS
- Controlla che `manifest.json` sia accessibile
- Verifica che `service-worker.js` sia registrato (vedi console browser)

### ❌ "Service Worker non funziona"
- Apri DevTools (F12) → Console
- Cerca errori
- Verifica che il path sia corretto: `./service-worker.js`

### ❌ "Icone non si vedono"
- Verifica che la cartella `icons/` sia nella root
- Controlla i path nel `manifest.json`
- Cancella cache e ricarica

---

## 📊 STATISTICHE (Opzionale)

Per vedere quante persone usano la tua PWA:

1. Repository → Insights → Traffic
2. Vedrai visualizzazioni, visitatori unici, etc.

---

## 🎨 PERSONALIZZAZIONI

### Cambiare Colori
Modifica in `index.html` e `manifest.json`:

```css
/* Gradient */
background: linear-gradient(135deg, #TUO-COLORE1 0%, #TUO-COLORE2 100%);
```

```json
// manifest.json
"background_color": "#TUO-COLORE",
"theme_color": "#TUO-COLORE"
```

### Cambiare Nome
Modifica in:
- `index.html`: tag `<title>`
- `manifest.json`: campi `name` e `short_name`
- `README.md`: sostituisci "SMEMOPASS" con il tuo nome

---

## ✅ CHECKLIST FINALE

Prima di condividere, verifica:

- [ ] Repository creato su GitHub
- [ ] Tutti i file caricati correttamente
- [ ] GitHub Pages attivato
- [ ] HTTPS funzionante
- [ ] PWA installabile su mobile
- [ ] Service Worker registrato
- [ ] Funziona offline
- [ ] Backup/Import funzionano
- [ ] Dashboard mostra dati
- [ ] README aggiornato con il tuo link

---

## 🎉 CONGRATULAZIONI!

Hai pubblicato con successo SMEMOPASS come PWA su GitHub Pages!

**Il tuo link:**
```
https://[tuo-username].github.io/smemopass/
```

**Prossimi passi:**
1. Condividi il link con amici/famiglia
2. Fai un post sui social
3. Aggiungi al tuo portfolio
4. Continua a migliorare l'app!

---

## 📞 SUPPORTO

Se hai problemi:
1. Rileggi questa guida
2. Controlla la console del browser (F12)
3. Cerca l'errore su Google
4. Apri una Issue su GitHub
5. Chiedi aiuto nella community GitHub

---

**Buon lavoro! 🚀**
