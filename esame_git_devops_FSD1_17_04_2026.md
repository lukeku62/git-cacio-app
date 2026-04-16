# Esame Finale — Git & GitHub

---

## Scenario

Sei stato assunto come sviluppatore web junior dallo studio **DevStudio**. Il tuo primo incarico è costruire e versionare un mini-sito vetrina dell'agenzia, seguendo rigorosamente le pratiche Git apprese durante il corso.

Ogni sezione corrisponde a una fase di lavoro reale. Segui i passaggi **nell'ordine indicato**.

> La valutazione avverrà esaminando il repository remoto su GitHub: cronologia dei commit, messaggi, branch, Pull Request e file. Assicurati di eseguire ogni push e pull quando richiesto.

## NOTE OPERATIVE

- Il commento di ogni commit deve descrivere le operazioni eseguite e il perché hai scelto quegli specifici comandi (definizione o motivazione).

---

## PARTE A — Fondamenta

### Sezione 1 — Setup del repository

1. Crea una cartella locale chiamata `devstudio-[tuo-nickname]`.
2. Inizializza un repository Git al suo interno.
3. Su GitHub, crea un repository **privato** con lo stesso nome. Non inizializzarlo con nessun file.
4. Aggiungi il docente come collaboratore del repository remoto (username: `lukeku62` e `robrub`).
5. Collega il repository locale al remote.
6. Crea un file `.gitignore` con il seguente contenuto:

```
*.tmp
*.log
.DS_Store
node_modules/
```

7. Esegui staging e commit con messaggio: `"chore: aggiunto .gitignore"`.
8. Esegui push impostando il tracking sulla branch principale.

---

### Sezione 2 — Prima struttura del sito

1. Crea il file `index.html`:

```html
<!DOCTYPE html>
<html lang="it">
  <head>
    <meta charset="UTF-8" />
    <title>DevStudio</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <header class="site-header">
      <h1>DevStudio</h1>
      <nav>
        <a href="index.html">Home</a>
        <a href="servizi.html">Servizi</a>
        <a href="team.html">Team</a>
        <a href="contatti.html">Contatti</a>
      </nav>
    </header>

    <main>
      <section class="hero">
        <h2>Costruiamo il web che immagini</h2>
        <p>Siamo un team di sviluppatori appassionati con sede a Milano.</p>
      </section>
    </main>

    <footer class="site-footer">
      <p>&copy; 2025 DevStudio. Tutti i diritti riservati.</p>
    </footer>
  </body>
</html>
```

2. Esegui staging **solo** di `index.html` e commit con messaggio: `"feat: aggiunta homepage"`.

3. Crea il file `style.css`:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: sans-serif;
  background-color: #f4f4f4;
  color: #222;
}

.site-header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.site-header nav a {
  color: white;
  text-decoration: none;
  margin-left: 1.5rem;
}

.hero {
  padding: 4rem 2rem;
  text-align: center;
}

.hero h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.site-footer {
  background-color: #2c3e50;
  color: white;
  text-align: center;
  padding: 1rem;
  margin-top: 3rem;
}
```

4. Verifica lo stato del repository.
5. Verifica le differenze tra la working area e l'ultimo commit.
6. Esegui staging di `style.css` e commit con messaggio: `"feat: aggiunto foglio di stile"`.
7. Esegui push.

---

### Sezione 3 — Feature branch e Pull Request: pagina servizi

1. Crea una nuova branch `feature/servizi` e spostati su di essa con un unico comando.
2. Crea il file `servizi.html`:

```html
<!DOCTYPE html>
<html lang="it">
  <head>
    <meta charset="UTF-8" />
    <title>Servizi — DevStudio</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <header class="site-header">
      <h1>DevStudio</h1>
      <nav>
        <a href="index.html">Home</a>
        <a href="servizi.html">Servizi</a>
        <a href="team.html">Team</a>
        <a href="contatti.html">Contatti</a>
      </nav>
    </header>

    <main>
      <section class="servizi">
        <h2>I nostri servizi</h2>
        <div class="card">
          <h3>Sviluppo Web</h3>
          <p>Realizziamo siti e applicazioni web su misura.</p>
        </div>
        <div class="card">
          <h3>UI/UX Design</h3>
          <p>Progettiamo interfacce intuitive e moderne.</p>
        </div>
        <div class="card">
          <h3>Consulenza DevOps</h3>
          <p>Ottimizziamo pipeline e infrastrutture cloud.</p>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <p>&copy; 2025 DevStudio. Tutti i diritti riservati.</p>
    </footer>
  </body>
</html>
```

3. Aggiungi al file `style.css` le seguenti regole:

```css
.servizi {
  padding: 3rem 2rem;
}

.servizi h2 {
  font-size: 1.75rem;
  margin-bottom: 2rem;
  text-align: center;
}

.card {
  background-color: #ffffff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
}

.card h3 {
  margin-bottom: 0.5rem;
  color: #2c3e50;
}
```

4. Verifica le differenze tra la working area e l'ultimo commit.
5. Esegui staging di entrambi i file e commit con messaggio: `"feat: aggiunta pagina servizi"`.
6. Esegui push della branch `feature/servizi` sul remote.
7. Su GitHub, apri una **Pull Request** da `feature/servizi` verso la branch principale con titolo: `"Aggiunta pagina servizi"` e una breve descrizione delle modifiche.
8. **Esegui il merge della PR dalla UI di GitHub** (pulsante _Merge pull request_).
9. In locale, spostati sulla branch principale ed esegui `git pull` per sincronizzare le modifiche.
10. Verifica con `git log --oneline -3` che il merge sia presente nella cronologia locale.

---

## PARTE B — Workflow avanzato

### Sezione 4 — Stash e lavoro urgente: pagina team

1. Crea una branch `feature/team` e spostati su di essa.
2. Crea il file `team.html`:

```html
<!DOCTYPE html>
<html lang="it">
  <head>
    <meta charset="UTF-8" />
    <title>Team — DevStudio</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <header class="site-header">
      <h1>DevStudio</h1>
      <nav>
        <a href="index.html">Home</a>
        <a href="servizi.html">Servizi</a>
        <a href="team.html">Team</a>
        <a href="contatti.html">Contatti</a>
      </nav>
    </header>

    <main>
      <section class="team">
        <h2>Il nostro team</h2>
        <div class="membro">
          <h3>Alice Rossi</h3>
          <p>Lead Developer</p>
        </div>
        <div class="membro">
          <h3>Marco Bianchi</h3>
          <p>UI/UX Designer</p>
        </div>
        <div class="membro">
          <h3>Sara Conti</h3>
          <p>DevOps Engineer</p>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <p>&copy; 2025 DevStudio. Tutti i diritti riservati.</p>
    </footer>
  </body>
</html>
```

3. **Attenzione — urgenza!** Prima di fare qualsiasi commit, metti in stash tutte le modifiche attuali compresi i file non tracciati.
4. Verifica che lo stash contenga almeno un elemento.
5. Spostati sulla branch principale.
6. Nel file `index.html`, modifica il tag `<title>` da `DevStudio` a `DevStudio — Agenzia Web Milano`.
7. Modifica il paragrafo nella sezione `.hero` da `"Siamo un team di sviluppatori appassionati con sede a Milano."` a `"Dal 2020 aiutiamo aziende e startup a costruire prodotti digitali di qualità."`.
8. Esegui staging e commit con messaggio: `"fix: aggiornamento testi homepage"`.
9. Esegui push.
10. Torna sulla branch `feature/team`.
11. Recupera le modifiche dallo stash rimuovendolo dalla pila.
12. Verifica che il file `team.html` sia presente nella working area e che lo stash risulti vuoto.
13. Aggiungi al file `style.css` le seguenti regole:

```css
.team {
  padding: 3rem 2rem;
}

.team h2 {
  font-size: 1.75rem;
  margin-bottom: 2rem;
  text-align: center;
}

.membro {
  background-color: #ffffff;
  border-left: 4px solid #2c3e50;
  padding: 1rem 1.5rem;
  margin-bottom: 1rem;
}

.membro h3 {
  color: #2c3e50;
  margin-bottom: 0.25rem;
}
```

14. Esegui staging di tutti i file e commit con messaggio: `"feat: aggiunta pagina team con stili"`.
15. Esegui push della branch `feature/team`.
16. Su GitHub, apri una Pull Request con titolo `"Aggiunta pagina team"` e una breve descrizione.
17. Esegui il merge della PR dalla UI di GitHub.
18. In locale, spostati sulla branch principale ed esegui `git pull`.

---

### Sezione 5 — Amend: commit incompleto

1. Crea una branch `feature/contatti` e spostati su di essa.
2. Crea il file `contatti.html`:

```html
<!DOCTYPE html>
<html lang="it">
  <head>
    <meta charset="UTF-8" />
    <title>Contatti — DevStudio</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <header class="site-header">
      <h1>DevStudio</h1>
      <nav>
        <a href="index.html">Home</a>
        <a href="servizi.html">Servizi</a>
        <a href="team.html">Team</a>
        <a href="contatti.html">Contatti</a>
      </nav>
    </header>

    <main>
      <section class="contatti">
        <h2>Contattaci</h2>
        <p>Email: <a href="mailto:info@devstudio.it">info@devstudio.it</a></p>
        <p>Telefono: +39 02 1234567</p>
        <p>Indirizzo: Via Roma 1, 20100 Milano</p>
      </section>
    </main>

    <footer class="site-footer">
      <p>&copy; 2025 DevStudio. Tutti i diritti riservati.</p>
    </footer>
  </body>
</html>
```

3. Esegui staging e commit con messaggio: `"feat: aggiunta pagina contatti"`.
4. Ti accorgi di aver dimenticato gli stili. Aggiungi le seguenti regole al file `style.css`:

```css
.contatti {
  padding: 3rem 2rem;
  max-width: 600px;
}

.contatti h2 {
  font-size: 1.75rem;
  margin-bottom: 1.5rem;
}

.contatti p {
  margin-bottom: 0.75rem;
  line-height: 1.6;
}

.contatti a {
  color: #2c3e50;
}
```

5. Esegui staging di `style.css` e aggiorna il commit precedente (senza crearne uno nuovo), modificando anche il messaggio in: `"feat: aggiunta pagina contatti con stili"`.
6. Verifica con `git log --oneline` che esista **un solo** commit per questa feature.
7. Esegui push della branch `feature/contatti`.
8. Su GitHub, apri una Pull Request con titolo `"Aggiunta pagina contatti"` e una breve descrizione.
9. Esegui il merge della PR dalla UI di GitHub.
10. In locale, spostati sulla branch principale ed esegui `git pull`.

---

### Sezione 6 — Reset: commit sulla branch sbagliata

1. Assicurati di essere sulla branch principale.
2. Crea il file `404.html`:

```html
<!DOCTYPE html>
<html lang="it">
  <head>
    <meta charset="UTF-8" />
    <title>Pagina non trovata — DevStudio</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <header class="site-header">
      <h1>DevStudio</h1>
    </header>
    <main>
      <section class="hero">
        <h2>404 — Pagina non trovata</h2>
        <p>
          La pagina che cerchi non esiste.
          <a href="index.html">Torna alla home</a>.
        </p>
      </section>
    </main>

    <footer class="site-footer">
      <p>&copy; 2025 DevStudio. Tutti i diritti riservati.</p>
    </footer>
  </body>
</html>
```

3. Esegui staging e commit con messaggio: `"feat: aggiunta pagina 404"`.
4. **Non eseguire push.**
5. Ti accorgi che questa modifica andava fatta su una feature branch. Utilizza `git reset` nella modalità più appropriata per annullare il commit mantenendo le modifiche nella working directory.
6. Verifica che il commit sia scomparso dal log ma che il file `404.html` esista ancora.
7. Crea una branch `feature/404` e spostati su di essa.
8. Esegui staging e commit con messaggio: `"feat: aggiunta pagina 404"`.
9. Esegui push della branch `feature/404`.
10. Su GitHub, apri una Pull Request con titolo `"Aggiunta pagina 404"`.
11. Esegui il merge della PR dalla UI di GitHub.
12. In locale, spostati sulla branch principale ed esegui `git pull`.

---

## PARTE C — Gestione della cronologia

### Sezione 7 — Risoluzione di un conflitto

1. Assicurati di essere sulla branch principale. Annota l'hash breve dell'ultimo commit con `git log --oneline -1`.
2. Crea una branch `feature/colori-a` e spostati su di essa.
3. Nel file `style.css`, modifica il `background-color` del selettore `.site-header` da `#2c3e50` a `#1a252f`.
4. Esegui staging e commit con messaggio: `"feat: aggiornamento colore header variante A"`.
5. Esegui push della branch `feature/colori-a`.
6. Torna sulla branch principale. Verifica con `git log --oneline -1` di essere sullo stesso hash annotato al punto 1.
7. **Senza eseguire alcun pull o merge**, crea una branch `feature/colori-b` e spostati su di essa.
8. Nel file `style.css`, modifica il `background-color` dello stesso selettore `.site-header` da `#2c3e50` a `#34495e`.
9. Esegui staging e commit con messaggio: `"feat: aggiornamento colore header variante B"`.
10. Torna sulla branch principale.
11. Esegui il merge di `feature/colori-a` su main: andrà a buon fine.
12. Esegui il merge di `feature/colori-b` su main: genererà un **conflitto**.
13. Apri il file in conflitto e identifica i marcatori (`<<<<<<<`, `=======`, `>>>>>>>`).
14. Risolvi il conflitto scegliendo il colore `#1a252f` (variante A). Rimuovi tutti i marcatori.
15. Esegui staging del file risolto e completa il merge con messaggio: `"fix: risolto conflitto colore header, scelta variante A"`.
16. Esegui push.

---

### Sezione 8 — Rebase: allineare una branch con main

1. Crea una branch `feature/tipografia` e spostati su di essa.
2. Crea un file `typography.css`:

```css
h1,
h2,
h3 {
  font-weight: 700;
  line-height: 1.2;
}

p {
  font-size: 1rem;
  line-height: 1.6;
  color: #444;
}

a {
  color: #2c3e50;
  text-decoration: underline;
}

a:hover {
  color: #1a252f;
}
```

3. Esegui staging e commit con messaggio: `"feat: aggiunto file tipografia"`.
4. **Non eseguire push per ora.**
5. Spostati sulla branch principale.
6. Nel file `servizi.html`, modifica il `<title>` da `"Servizi — DevStudio"` a `"I Nostri Servizi — DevStudio"`.
7. Esegui staging e commit con messaggio: `"fix: aggiornamento titolo pagina servizi"`.
8. Esegui push.
9. Torna sulla branch `feature/tipografia`.
10. Utilizza `git rebase` per riallineare la branch con main, in modo che il commit di tipografia risulti _successivo_ a quello appena fatto su main.
11. Verifica con `git log --oneline -3` che il commit `"feat: aggiunto file tipografia"` sia in cima, sopra `"fix: aggiornamento titolo pagina servizi"`.
12. Esegui push della branch `feature/tipografia`.
13. Spostati sulla branch principale, esegui merge di `feature/tipografia` e push.

---

### Sezione 9 — Revert: annullare un commit già pushato

1. Assicurati di essere sulla branch principale.
2. Aggiungi alla fine del file `style.css` la seguente regola volutamente errata:

```css
body {
  font-size: 437px;
  background-color: pink;
}
```

3. Esegui staging e commit con messaggio: `"feat: stili creativi homepage"`.
4. Esegui push.
5. Il commit è sbagliato ed è già sul remote. Utilizza il comando Git appropriato per **annullarlo senza riscrivere la cronologia**, accettando il messaggio proposto da Git.
6. Esegui push del commit di annullamento.
7. Verifica con `git log --oneline -3` che esistano sia il commit errato sia il commit di revert.

---

### Sezione 10 — Merge squash: pagina chi siamo

1. Crea una branch `feature/chi-siamo` e spostati su di essa.
2. Crea il file `chi-siamo.html`:

```html
<!DOCTYPE html>
<html lang="it">
  <head>
    <meta charset="UTF-8" />
    <title>Chi siamo — DevStudio</title>
    <link rel="stylesheet" href="style.css" />
    <link rel="stylesheet" href="typography.css" />
  </head>
  <body>
    <header class="site-header">
      <h1>DevStudio</h1>
      <nav>
        <a href="index.html">Home</a>
        <a href="servizi.html">Servizi</a>
        <a href="team.html">Team</a>
        <a href="contatti.html">Contatti</a>
        <a href="chi-siamo.html">Chi siamo</a>
      </nav>
    </header>

    <main>
      <section class="chi-siamo">
        <h2>Chi siamo</h2>
        <p>
          DevStudio nasce nel 2020 dalla passione di tre sviluppatori milanesi.
        </p>
        <p>
          Crediamo che il codice pulito e il design curato siano la base di ogni
          prodotto di successo.
        </p>
      </section>
    </main>

    <footer class="site-footer">
      <p>&copy; 2025 DevStudio. Tutti i diritti riservati.</p>
    </footer>
  </body>
</html>
```

3. Esegui staging e commit con messaggio: `"feat: struttura pagina chi siamo"`.
4. Aggiungi al file `style.css`:

```css
.chi-siamo {
  padding: 3rem 2rem;
  max-width: 700px;
}

.chi-siamo h2 {
  font-size: 1.75rem;
  margin-bottom: 1.5rem;
}

.chi-siamo p {
  margin-bottom: 1rem;
}
```

5. Esegui staging e commit con messaggio: `"feat: stili pagina chi siamo"`.
6. Aggiungi il link `<a href="chi-siamo.html">Chi siamo</a>` nella `<nav>` di **tutti** gli altri file HTML del progetto: `index.html`, `servizi.html`, `team.html`, `contatti.html`, `404.html`.
7. Esegui staging e commit con messaggio: `"feat: aggiunto link chi siamo alla navigazione"`.
8. Verifica con `git log --oneline` che sulla branch `feature/chi-siamo` ci siano **tre** commit.
9. Torna sulla branch principale.
10. Esegui il merge di `feature/chi-siamo` usando l'opzione `--squash`.
11. Esegui il commit risultante con messaggio: `"feat: aggiunta sezione chi siamo"`.
12. Verifica con `git log --oneline -2` che su main compaia **un solo** commit per tutta la feature.
13. Esegui push.

---

## PARTE D — Organizzazione finale

### Sezione 11 — Pulizia branch

1. Assicurati di essere sulla branch principale con tutti i merge completati.
2. Visualizza l'elenco di tutte le branch locali.
3. Elimina **tutte** le branch di feature locali già integrate (usa `-d`, oppure `-D` se necessario).
4. Elimina le branch remote corrispondenti con `git push origin --delete <nome-branch>`.
5. Verifica con `git branch -a` che rimangano solo la branch principale e il suo riferimento remoto.

---

### Sezione 12 — README e consegna finale

1. Crea un file `README.md` con il seguente contenuto. **Completa le parti tra parentesi quadre** navigando il repository su GitHub:

```markdown
# DevStudio — Sito Vetrina

Progetto realizzato come esame finale del corso Git & GitHub.

## Struttura del progetto

- `index.html` — Homepage
- `servizi.html` — Pagina servizi
- `team.html` — Pagina team
- `contatti.html` — Pagina contatti
- `chi-siamo.html` — Pagina chi siamo
- `404.html` — Pagina di errore
- `style.css` — Stili principali
- `typography.css` — Stili tipografici
- `.gitignore` — File ignorati da Git

## Informazioni dal repository

1. Numero totale di commit su main: [___]
2. Hash breve del primo commit in assoluto: [___]
3. Numero di Pull Request aperte durante il progetto: [___]
```

2. Esegui staging e commit con messaggio: `"docs: aggiunto README con riepilogo"`.
3. Esegui push finale.
