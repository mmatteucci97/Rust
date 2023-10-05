# Hello Cargo

La semplice compilazione con `rustc` va bene per piccoli progetti con solo pochi file sorgente, ma man mano che il tuo progetto cresce, vorrai gestire le dipendenze del progetto, la configurazione della build e altre opzioni. Per questo motivo, la comunità Rust ha sviluppato una serie di strumenti per semplificare la gestione di queste attività. Quello più comunemente usato è Cargo.

Cargo è il sistema di compilazione e il gestore dei pacchetti di Rust. La maggior parte dei Rustaceani usa Cargo per gestire i propri progetti Rust perché Cargo gestisce molte attività per te, come costruire il tuo codice, scaricare le librerie da cui dipende il tuo codice e costruire quelle librerie (chiamiamo le librerie per le quali il tuo codice necessita di dipendenze).

I programmi Rust più semplici, come quello della sezione precedente, non hanno dipendenze. Se avessi costruito il messaggio "Hello, World!" programma che utilizza Cargo, utilizzerà solo la parte di Cargo che crea il tuo codice. Man mano che i tuoi programmi diventano più complessi, Cargo gestirà molto di più, come la creazione di più file sorgente in un unico programma, il download delle librerie da cui dipende il tuo programma e la creazione di tali librerie.

Poiché la maggior parte dei progetti Rust utilizza Cargo, per ora nel repository supporremo che tu stia utilizzando Cargo per creare i tuoi progetti.

Per verificare se hai installato Cargo, esegui questo comando:

```bash
$ cargo --version
cargo 1.51.0 (43b129a20 2021-03-16)
```

Se vedi un numero di versione, ce l'hai! Se viene visualizzato un errore, ad esempio `command not found`, visita [la pagina di installazione](https://www.rust-lang.org/tools/install) per installarlo.

## Creazione di un progetto con Cargo

Creiamo un progetto che utilizza Cargo in modo da poter vedere come funziona e come differisce dal programma originale "Hello, World!". Utilizzeremo Cargo per creare un nuovo progetto chiamato `hello_cargo`, quindi costruiremo e eseguiremo quel progetto. Naviga dove vuoi creare la tua directory di base del progetto e esegui questo comando:

```bash
$ cargo new hello_cargo
     Created binary (application) `hello_cargo` package
$ cd hello_cargo
```

Il primo comando crea una nuova directory e un progetto chiamato `hello_cargo`. Poiché abbiamo chiamato il nostro progetto `hello_cargo`, Cargo ha generato una directory con lo stesso nome.
Vai nella directory `hello_cargo` e vedrai che Cargo ha generato due file e una directory per noi:

```bash
$ tree
.
├── Cargo.toml
└── src
    └── main.rs

1 directory, 2 files
```

Cargo inizializzerà anche un nuovo repository git per te, insieme a un file `.gitignore` e un commit iniziale. I file Git non verranno generati se hai già un repository git nella directory corrente. Puoi annullare questa operazione con il comando `cargo new --vcs=git`.

__Nota__: Git è un sistema di controllo versione comune. Puoi modificare il comando `cargo new` per utilizzare un diverso sistema di controllo versione, come Mercurial, utilizzando il flag `--vcs`. Se non sei sicuro di quale sistema di controllo versione utilizzare, ti consigliamo Git. Esegui `cargo new --help` per vedere le opzioni disponibili.

Apri il file `Cargo.toml` nel tuo editor di testo. Dovrebbe apparire così:

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

Questo file è il formato TOML (Tom's Obvious, Minimal Language), che è il formato di configurazione di Cargo.
La prima riga, `[package]`, è un'intestazione di sezione che indica che le seguenti istruzioni stanno configurando un pacchetto.
Ognuna delle tre righe successive è una coppia chiave-valore che ha un'istruzione e un valore, come `name = "hello_cargo"`. Quelle tre righe sono informazioni che Cargo ha bisogno per compilare il tuo progetto: nome, versione e edizione di Rust da utilizzare. Parleremo in seguito della chiave `edition`.
L'ultima riga, `[dependencies]`, è l'inizio di una sezione in cui è possibile elencare le dipendenze del progetto. Se il tuo progetto non ha alcuna dipendenza, la sezione `[dependencies]` sarà vuota, come in questo esempio.

Ora apri il file `src/main.rs` nel tuo editor di testo. Dovrebbe apparire così:

```rust
fn main() {
    println!("Hello, world!");
}
```

Questo è lo stesso codice che abbiamo inserito nella sezione precedente. Cargo ha generato un messaggio "Hello, World!" programma per noi pronto per essere creato ed eseguito. Finora, l'unica differenza tra questo codice e il codice nella sezione precedente è che Cargo ha inserito il codice nella directory `src` in un file chiamato `main.rs` invece che in un file chiamato `hello_world.rs`, e Cargo ha anche creato un file `Cargo.toml`. Cargo si aspetta che tutto il codice risieda nella directory "src". La directory del progetto di livello superiore è riservata solo ai file README, alle informazioni sulla licenza, ai file di configurazione e a qualsiasi altra cosa non correlata al tuo codice.

## Compilazione e esecuzione di un progetto Cargo

Ora che hai un progetto Cargo, vediamo come compilarlo e eseguirlo.  
Assicurarti di essere nella directory `hello_cargo` che hai appena creato, contenente il file `Cargo.toml` e la directory `src` con il file `main.rs` al suo interno. Poi esegui questo comando:

```bash
$ cargo build
   Compiling hello_cargo v0.1.0 (/home/you/projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.31s
```

Questo comando crea un file eseguibile in `target/debug/hello_cargo` (o `target\debug\hello_cargo.exe` su Windows) anziché nella directory corrente. La directory `target/debug` è dove Cargo mette i file eseguibili per i progetti che costruisce.  
Essendo la build di default quella di debug, Cargo inserisce i file binari nella directory `target/debug`. La compilazione in debug impiega più tempo per compilare, ma include strumenti utili che rendono il programma più semplice da debuggare. Quando il tuo progetto è pronto per la produzione, puoi eseguire `cargo build --release` per compilare in modalità release. Questa compilazione impiega più tempo per compilare perché Rust esegue più ottimizzazioni per rendere il codice più veloce. Il risultato finale è un file binario in `target/release` invece di `target/debug`.

Esegui il file eseguibile per vedere l'output "Hello, World!":

```bash
$ ./target/debug/hello_cargo
Hello, world!
```

Se tutto è andato bene, dovresti vedere il messaggio "Hello, World!" stampato sul terminale. Eseguire `cargo build` per la prima volta genererà anche un nuovo file: `Cargo.lock`. Questo file tiene traccia delle dipendenze del tuo progetto. Non dovrai mai modificare questo file manualmente. Cargo lo aggiornerà automaticamente ogni volta che compila il tuo progetto.  
Questo progetto non contiene dipendenze, perciò il file `Cargo.lock` è molto semplice:

```bash
$ cat Cargo.lock
# This file is automatically @generated by Cargo.
# It is not intended for manual editing.
[[package]]
name = "hello_cargo"
version = "0.1.0"
dependencies = []
```

Abbiamo compilato il progetto utilizzando Cargo, ma possiamo anche utilizzare `cargo run` per compilare e eseguire il progetto in un unico comando:

```bash
$ cargo run
   Compiling hello_cargo v0.1.0 (/home/you/projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.31s
     Running `target/debug/hello_cargo`
Hello, world!
```

Cargo fornisce anche un comando `cargo check` che controlla se il codice compila senza generare un file eseguibile, quindi è molto più veloce di `cargo build`. È una buona idea eseguire `cargo check` prima di eseguire `cargo build`, in quanto ti consente di trovare errori di compilazione più rapidamente.

```bash
$ cargo check
   Checking hello_cargo v0.1.0 (/home/you/projects/hello_cargo)
   Finished dev [unoptimized + debuginfo] target(s) in 0.16s
```

Perché non si dovrebbe volere un eseguibile? Spesso, `cargo check` è molto più veloce di `cargo build`, perché non produce un file eseguibile. Se il tuo progetto è grande, può essere molto più veloce eseguire `cargo check` per controllare se il codice compila, quindi eseguire `cargo build` per generare un eseguibile per testarlo.

Ricapitoliamo quello che abbiamo imparato finora su Cargo:
- Possiamo creare un nuovo progetto che utilizza Cargo con `cargo new`.
- Possiamo costruire un progetto usando `cargo build`.
- Possiamo creare ed eseguire un progetto in un unico passaggio utilizzando "cargo run".
- Possiamo costruire un progetto senza produrre un file binario per verificare la presenza di errori utilizzando `cargo check`.
- Invece di salvare il risultato della compilazione nella stessa directory del nostro codice, Cargo lo memorizza nella directory `target/debug`.
- I comandi di Cargo sono gli stessi per tutti i sistemi operativi, quindi tutti i tuoi collaboratori potranno costruire il tuo pacchetto senza sforzi aggiuntivi da parte loro.