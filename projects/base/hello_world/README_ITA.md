# Hello World!

È ora di scrivere il tuo primo programma Rust. È tradizione quando si impara un nuovo linguaggio scrivere un programma che stampa il testo `Hello World!` sullo schermo, quindi faremo lo stesso qui!

## Creazione di una nuova directory di progetto

Inizierai creando una directory per archiviare il tuo codice Rust. A Rust non importa dove vive il tuo codice, ma per gli esercizi e i progetti in questo repository, suggerirò di creare una directory _projects_ nella tua directory home.
Il seguente elenco di comandi creerà la directory _projects_ e posiziona il terminale in essa.

Su Linux, macOS e PowerShell su Windows:
```
$ mkdir -p ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

Su Windows Command Prompt:
```
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

## Scrivere ed eseguire il tuo primo programma

Successivamente, crea un nuovo file sorgente e chiamalo `main.rs`. I file Rust terminano sempre con l'estensione `.rs`.
__Nota__: se stai usando più di una parola nel nome del file, usa un trattino basso per separarle. Per esempio, :white_check_mark:  `hello_world.rs` è un buon nome per un file, ma :x: `hello world.rs` non lo è.

Ora, apri il file nel tuo editor di testo e digita il seguente codice:
```rust
fn main() {
    println!("Hello, world!");
}
```

Salva il file e torna alla finestra del terminale, nella stessa directory del file `main.rs`.

Su Linux e macOS, usa questo comando per compilare ed eseguire il programma:
```
$ rustc main.rs
$ ./main
Hello, world!
```

Su Windows, inserisci il comando .\main.exe invece di ./main:
```
> rustc main.rs
> .\main.exe
Hello, world!
```

Indipendentemente dal sistema operativo utilizzato, dovresti vedere l'output `Hello, world!` stampato sul tuo terminale. Congratulazioni! Hai scritto ed eseguito il tuo primo programma Rust.

## Anatomia di un programma Rust

Diamo un'occhiata più da vicino al codice che hai scritto.
Ecco il primo pezzo del puzzle:

```rust
fn main() {

}
```

Queste linee definiscono una funzione Rust. Le funzioni sono un gruppo di istruzioni che eseguono un'operazione specifica. In questo caso, la funzione `main` non ha parametri e non restituisce alcun valore, quindi le parentesi sono vuote `()`. Discuteremo di parametri e valori di ritorno in un momento successivo. 
Le parentesi graffe `{}` indicano l'inizio e la fine del corpo della funzione. Rust richiede che siano presenti le parentesi graffe attorno al corpo di ogni funzione, per rendere il codice meno ambiguo.

__Nota__: Se vuoi mantenere uno stile standard nei progetti Rust, puoi utilizzare uno strumento di formattazione automatica chiamato `rustfmt` per formattare il tuo codice in uno stile particolare. Puoi eseguire `rustfmt` sul tuo codice eseguendo `rustfmt main.rs` nel tuo terminale.

Il corpo della funzione `main` contiene una singola istruzione:

```rust
println!("Hello, world!");
```

Questa riga fa tutto il lavoro in questo piccolo programma: stampa il testo sullo schermo. Ci sono quattro dettagli importanti da notare qui:
- Lo stile Rust prevede il rientro con quattro spazi, non una tabulazione.
- Il comando `println!` richiama una macro di Rust. Se invece chiamasse una funzione, verrebbe inserita come `println` (senza il !). Parleremo delle macro più tardi. Per ora, devi solo sapere che usare `!` significa che stai chiamando una macro invece di una normale funzione e che le macro non sempre seguono le stesse regole delle funzioni.
- la stringa `"Hello, world!"` viene passata come argomento a `println!` e la stringa viene stampata sullo schermo.
- terminiamo la riga con un punto e virgola (`;`), che indica che questa espressione è finita e quella successiva è pronta per iniziare. La maggior parte delle righe del codice Rust terminano con un punto e virgola.

Se dimentichi di mettere il punto e virgola alla fine di una riga, Rust ti darà un errore e non verrà compilato. In Rust, il punto e virgola dice al compilatore di aspettarsi più codice, ma se non c'è più codice, Rust segnala un errore. Vediamo cosa succede se rimuovi il punto e virgola dalla riga `println!`:

```rust
fn main() {
    println!("Hello, world!")
}
```

Se provi a compilare questo programma, otterrai questo errore:

```rust
$ rustc main.rs
error: expected `;`, found `}`
    --> main.rs:3:1
    |
    3 | }
    |  ^
    |
    = note: If you intended to return on the last line of the function body, you can
    remove the semicolon.
```