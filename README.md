# GestionaleMaestro

**Un gestionale mobile-first per maestri di sci e snowboard, con un'area dedicata ai loro clienti.**

Progetto personale di **Alessandro Joannas**, maestro di snowboard: nasce dai problemi che incontro ogni giorno in
pista. Questa pagina racconta il progetto; il codice sorgente è privato.

---

## Il problema

Un maestro lavora spesso per una o più scuole sci, ognuna con il suo gestionale, e ha anche clienti privati. Le ore
sono sparse tra sistemi diversi, ricopiate a mano; i clienti non hanno un posto dove vedere le loro lezioni; e il
punto d'incontro a inizio lezione è spesso fonte di confusione: la scuola ne indica uno, il cliente ne capisce un
altro, e ci si cerca sulle piste.

## Cosa fa

**Per il maestro**
- Agenda delle lezioni (sci e snowboard), rubrica clienti, statistiche di stagione: ore per mese, per disciplina,
  per cliente.
- **Importazione del programma dal gestionale della scuola** tramite un'estensione del browser: legge la pagina che
  il maestro ha già aperto, senza mai chiedere password di altri sistemi, e propone le lezioni in un'anteprima da
  controllare prima di salvarle.
- **Clienti e famiglie**: chi prenota (il genitore) e chi scia (il figlio) sono persone diverse; i contatti sono
  quelli del genitore, le ore e i progressi del bambino.
- **Punti d'incontro precisi**: decisi dalla scuola o dal maestro, con mappa satellitare e foto del posto.
- Meteo della località per ogni giornata.

**Per il cliente**
- Le sue lezioni con tutti i maestri, la prossima in evidenza con meteo e webcam della località.
- **"Dove ci troviamo"**: mappa, foto e indicazioni del punto d'incontro. Poco prima della lezione l'app gli dice
  se è nel posto giusto, e il maestro sa che è arrivato. Scelta voluta: al cliente non si mostra mai un cronometro
  sul maestro, che arriva dalla lezione precedente.
- La sua stagione in numeri e i traguardi raggiunti; per un genitore, le lezioni di ogni figlio.

**Per l'amministratore**
- Approvazione dei maestri, gestione degli utenti, delle scuole e dei loro punti d'incontro, avvisi a tutti gli
  utenti, registro delle azioni, stato del sistema.

## Scelte tecniche che mi interessano

- **Sessioni che non scadono ogni giorno, in modo sicuro**: un pass corto (JWT, un'ora) e un pass lungo che si
  rinnova a ogni uso, salvato sul server solo come impronta e revocabile da ogni dispositivo.
- **Privacy della posizione**: per sapere se il cliente è arrivato si calcola la distanza dal punto d'incontro e si
  salva solo il risultato, mai le coordinate; tutto sparisce a lezione conclusa.
- **Importazione senza credenziali altrui**: l'estensione ha il permesso minimo (solo la scheda attiva, solo dopo
  un clic) e il testo viaggia nel frammento dell'URL, che non arriva a nessun server intermedio.
- **Foto controllate davvero**: il formato si riconosce dai byte del file, non da quello che dichiara il browser, e
  le immagini vengono ridotte sul telefono prima dell'invio.
- **Test automatici** sui servizi del backend (JUnit 5 e Mockito).

## Tecnologie

- **Backend**: Java 21, Spring Boot 3, Spring Security con JWT, JPA/Hibernate, PostgreSQL.
- **Frontend**: React 19, Vite, React Router; mappe con Leaflet (OpenStreetMap e immagini satellitari), meteo da
  Open-Meteo.
- **Estensione**: Edge/Chrome, Manifest V3.
- **In arrivo**: Docker e un server dedicato, poi l'app installabile sul telefono (PWA) e gli store.

## Schermate

*(da aggiungere)*

## Contatti

Alessandro Joannas, [LinkedIn](https://www.linkedin.com/) *(sostituire con il link del profilo)*
