Istruzioni funzionamento Quiz VIVI Energy Hub
Sono tutti inseriti dentro questa pagina Quiz VIVI Energy Hub in Instapage. Si può raggiungere i vari quiz modificando il referrer in query string:

https://casa.vivienergia.it/quiz-vivienergyhub?referrer=caldaia
https://casa.vivienergia.it/quiz-vivienergyhub?referrer=fotovoltaico
https://casa.vivienergia.it/quiz-vivienergyhub?referrer=climatizzatore
https://casa.vivienergia.it/quiz-vivienergyhub?referrer=wallbox
https://casa.vivienergia.it/quiz-vivienergyhub?referrer=depuratore
https://casa.vivienergia.it/quiz-vivienergyhub?referrer=greentips
https://casa.vivienergia.it/quiz-vivienergyhub?referrer=telethon
Per generare un nuovo quiz è possibile farlo da questo tool Generatore di Quiz Avanzato che consente di generare quiz a più risposte e personalizzare colori e cta in funzione della percentuale di risposte corrette. Il tool consente di copiare i singoli quiz, generare codici univoci o generare un codice universale per l'import su instapage e associabile ad un referrer personalizzato.

Per l'import è sufficiente copiare il codice di questa pagina nella sezione dedicata del tool e si riavrà la situazione as-is. Codice generato da nuovo tool - 16.10.25.html

Ogni volta conviene salvare il codice come avanzamento.

TRACCIAMENTI
I tracciamenti vanno inseriti nel file HTML all'interno del tag <script> che contiene tutta la logica di funzionamento del quiz. Nello specifico, vanno associati ai due pulsanti che vuoi monitorare: quello che avvia il quiz e quello finale che porta al sito.

Tracciamento per il pulsante "Inizia il Quiz" Questo codice serve a tracciare quando un utente clicca sul pulsante per avviare il quiz.
Dove inserirlo: Cerca la funzione initializeQuiz() nel tuo codice. Il punto esatto è subito dopo la riga startBtn.addEventListener('click', startQuestions);.

Codice da copiare: JavaScript

// ----- INSERISCI QUESTO CODICE PER IL PULSANTE 'START' ----- startBtn.addEventListener('click', function() { if (typeof tC !== 'undefined' && tC.event && typeof tC.event.quiz_veh === 'function') { tC.event.quiz_veh(this, { 'tipo_quiz': quizConfig.referrer, 'azione': 'start' }); } }); 
<img width="939" height="564" alt="image" src="https://github.com/user-attachments/assets/2cabd039-9a2e-4630-9c55-2ea9ea05b887" />


2. Tracciamento per il pulsante finale (CTA) Questo codice traccia i click sul pulsante finale che compare nella schermata dei risultati (es. "Scopri di più").
Dove inserirlo: Cerca la funzione showResults() nel tuo codice. Il punto perfetto è subito dopo la riga resultLinkEl.innerText = resultConfig.ctaText;.

Codice da copiare: JavaScript

// ----- INSERISCI QUESTO CODICE PER IL PULSANTE 'FINISH' ----- resultLinkEl.addEventListener('click', function() { if (typeof tC !== 'undefined' && tC.event && typeof tC.event.quiz_veh === 'function') { tC.event.quiz_veh(this, { 'tipo_quiz': quizConfig.referrer, 'azione': 'finish' }); } }); In sintesi, stai semplicemente aggiungendo un nuovo "ascoltatore" (addEventListener) a ciascun pulsante per inviare l'evento di tracciamento specifico quando vengono cliccati. Il codice è già configurato per recuperare dinamicamente il tipo di quiz (quizConfig.referrer) e l'azione corretta (start o finish).

<img width="947" height="1065" alt="image" src="https://github.com/user-attachments/assets/5aeef129-68e0-4440-bfc7-7f8560b72c55" />

