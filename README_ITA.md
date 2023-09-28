# Rust
Repository pubblico in cui puoi trovare vari esempi di programmi ed algoritmi per imaprare il linguaggio Rust e le sue librerie

All'interno delle varie directories puoi trovare alcuni file README o altri file in formato Markdown in cui tutti i concetti e le funzionalità sono descritte.

Assicurati di usare Rust 1.62.0 (rilasciato il 30/06/2022) o versioni successive, insieme a

    ```
    edition = "2021" 
    ```

nel file Cargo.toml di tutti i progetti per configurarli per utilizzare gli idiom di Rust 2021 edition.

La edizione 2021 del linguaggio di programmazione Rust include una serie di miglioramenti che rendono Rust più ergonomico e correggono alcune incongruenze.

La edizione Rust 2021 è retrocompatibile con la edizione Rust 2018, quindi tutto il codice Rust esistente continuerà a compilarsi con la edizione Rust 2021.

## Introduzione

Benvenuto nel linguaggio di programmazione Rust, un linguaggio che ti aiuta a scrivere software più veloce e affidabile. L'ergonomia ad alto livello e il controllo a basso livello sono spesso in conflitto nella progettazione dei linguaggi di programmazione; Rust sfida quel conflitto. Bilanciando una potente capacità tecnica e un'ottima esperienza per lo sviluppatore, Rust ti dà la possibilità di controllare i dettagli a basso livello (come l'utilizzo della memoria) senza tutti i problemi tradizionalmente associati a tale controllo.

## Iniziare

In questa parte, discuteremo come installare Rust sul tuo sistema.

### Installazione

Il primo passo è installare Rust. Scaricheremo Rust tramite _rustup_, uno strumento a riga di comando per la gestione delle versioni di Rust e degli strumenti associati.
__Nota__: se preferisci non utilizzare _rustup_, consulta la pagina Altri metodi di installazione di Rust [qui](https://forge.rust-lang.org/infra/other-installation-methods.html) per ulteriori opzioni.

I seguenti passaggi installano l'ultima versione stabile del compilatore Rust. Le garanzie di stabilità di Rust garantiscono che tutti gli esempi in questo repository che compilano continueranno a compilarsi con le future versioni di Rust.
__L'output potrebbe differire leggermente tra le versioni__ perché Rust migliora spesso i messaggi di errore e gli avvisi.

#### Installazione di rustup su Linux o macOS

Se stai usando Linux o macOS, apri un terminale e inserisci il seguente comando:
```
$ curl --proto '=https' --tlsv1.3 -sSf https://sh.rustup.rs | sh
```
Il comando scarica uno script e avvia l'installazione dello strumento _rustup_, che installa l'ultima versione stabile di Rust. Segui le istruzioni visualizzate sullo schermo per completare l'installazione. Se l'installazione è riuscita, vedrai il seguente output:
```
Rust is installed now. Great!
```
Ti servirà anche un linker, che è un programma che Rust utilizza per unire le sue uscite compilati in un unico file. Il linker è incluso nella GNU Compiler Collection (GCC). La maggior parte dei sistemi ha già GCC installato, ma se non lo hai, puoi installarlo con il tuo gestore di pacchetti. Su Ubuntu e Debian, esegui il seguente comando:
```
$ sudo apt install build-essential
```
Su macOS, dovrai installare gli strumenti della riga di comando di Xcode. Puoi farlo eseguendo il seguente comando:
```
$ xcode-select --install
```

#### Installazione di rustup su Windows

Se stai usando Windows, da [qui](https://www.rust-lang.org/tools/install) puoi scaricare e installare l'ultima versione di rust. Ad un certo punto dell'installazione, riceverai un messaggio che spiega che avrai bisogno anche dello strumento di compilazione MSVC per Visual Studio 2013 o versioni successive.
Per acquisire gli strumenti di compilazione, dovrai installare Visual Studio 2022 Community. Puoi scaricarlo da [qui](https://visualstudio.microsoft.com/downloads/). Quando ti viene chiesto quali workload installare, assicurati di selezionare
- il carico di lavoro "Sviluppo desktop con C ++"
- l'SDK di Windows 10 o 11 (10.0.19041.0 o successivo)
- il pacchetto lingua inglese per Visual Studio, insieme a qualsiasi altra lingua che desideri utilizzare.