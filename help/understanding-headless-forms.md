---
title: 'Informazioni sui moduli headless: concetti e domande frequenti'
description: Risposte alle domande comuni su cosa sono i moduli headless, come differiscono dalle librerie di moduli tradizionali, dettagli sull’implementazione, controllo dell’interfaccia utente, prestazioni e integrazione con framework e back-end.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: moduli headless, libreria di moduli headless, moduli adattivi, gestione dello stato, convalida, sistema di progettazione, SSR, CMS
hide: false
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 0%

---


# Informazioni sui moduli headless: concetti e domande frequenti {#understanding-headless-forms}

Questa guida risponde alle domande comuni sui moduli headless in generale e su come vengono applicati ad AEM Headless Adaptive Forms. Puoi utilizzarlo per decidere quando utilizzare un approccio headless e come implementare, assegnare stili e integrare i moduli nel tuo stack.

## Nozioni di base e comprensione {#basics-understanding}

### Cos’è esattamente una libreria di moduli headless?

Una **libreria di moduli headless** è una soluzione di moduli che separa **logica del modulo** (stato, convalida, regole, invio) da **presentazione** (componenti e stile dell&#39;interfaccia utente). L’intestazione è l’interfaccia utente del modulo visibile; &quot;headless&quot; significa che la libreria non detta o invia un’interfaccia utente fissa. Invece, espone:

* Un **modello modulo** (spesso JSON): struttura, campi, vincoli e regole.
* **API o hook** per leggere e aggiornare lo stato del modulo, eseguire la convalida e gestire l&#39;invio.
* **Eventi e ciclo di vita** per consentire all&#39;interfaccia utente di reagire alle modifiche.

In AEM Headless Adaptive Forms, il modulo è una [struttura JSON](architecture.md) ospitata su Adobe Experience Manager. [Forms Web SDK](architecture.md#developer-tools) (client-side runtime) fornisce il livello di logica, ovvero processore delle regole business, gestione dello stato e convalida, mentre l&#39;app fornisce l&#39;interfaccia utente che esegue il rendering di tale struttura.

### Quali sono le differenze tra un modulo headless e una libreria di moduli tradizionale?

| Aspetto | Raccolta moduli tradizionale | Libreria moduli headless |
|--------|---------------------------|------------------------|
| **Interfaccia utente** | Fornisce componenti e stili incorporati | Interfaccia utente non prescritta; si portano i propri componenti |
| **Definizione dello stile** | Theming o sostituzioni sui componenti della libreria | Controllo completo; utilizza il sistema di progettazione così com’è |
| **Definizione modulo** | Spesso solo codice (componenti in JSX/HTML) | Spesso basato su dati (JSON/schema da CMS o API) |
| **Stato e convalida** | Associato ai componenti della libreria | Esposto tramite API/hook; qualsiasi interfaccia utente può associarsi ad essi |
| **Canali** | Solitamente web (a volte un framework) | La stessa definizione di modulo può essere utilizzata per il web, i dispositivi mobili, le chat e così via. |

Con AEM Headless Adaptive Forms, [crei e pubblichi un modulo](create-and-publish-a-headless-form.md) una volta in AEM; qualsiasi client (React, Angular, mobile nativo, chatbot) può [recuperare il modulo JSON](architecture.md) ed eseguirne il rendering con l&#39;interfaccia utente appropriata per quel canale.

### Perché dovrei usare moduli headless invece di una soluzione di moduli basata su interfaccia utente?

Le forme headless sono ideali per:

* **Coerenza del sistema di progettazione**: utilizza i componenti e il marchio esistenti senza disattivare i valori predefiniti della libreria.
* **Multicanale** - Una definizione di modulo per web, dispositivi mobili e altri punti di contatto (vedi [Panoramica](overview.md)).
* **Moduli guidati da CMS o back-end** - Gli autori modificano la struttura del modulo e le regole senza distribuzioni di codice; l&#39;app utilizza solo il JSON.
* **Flessibilità framework** - La libreria [AF-core](https://www.npmjs.com/package/@aemforms/af-core) è indipendente dal framework; le associazioni React sono fornite per comodità, ma puoi creare associazioni per altri framework.
* **Funzionalità di back-end** - Sfrutta AEM Forms per precompilare, convalidare, inviare, flussi di lavoro e Forms Data Model senza bloccarsi in uno stack di interfaccia utente specifico.

### Quando ha senso utilizzare un approccio headless?

Utilizza i moduli headless quando:

* È disponibile o si desidera un sistema di progettazione o una libreria di componenti avanzata.
* Forms è creato da non sviluppatori (ad esempio, in un CMS) e deve funzionare su più app o canali.
* È necessaria la stessa logica del modulo (convalida, regole) tra client web, mobili o altri.
* Desideri ridurre al minimo i rendering e mantenere la logica del modulo testabile indipendentemente dall’interfaccia utente.

Considera una libreria di moduli tradizionale inclusa nell’interfaccia utente quando:

* Hai bisogno di un modulo di lavoro in una singola app web rapidamente e non ti importa dell’interfaccia utente personalizzata o del multicanale.
* Il tuo team preferisce definire i moduli solo nel codice in un unico framework.

### &quot;headless&quot; è solo una parola d&#39;ordine o risolve problemi reali?

Risolve i veri problemi architettonici:

* **Separazione dei problemi** - La struttura del modulo, le regole e la convalida sono attive nei dati e in un livello logico; il livello dell&#39;interfaccia utente esegue il rendering e invia solo le azioni utente. Ciò migliora la testabilità e il riutilizzo.
* **Indipendenza canale** - Una definizione di modulo può gestire diverse interfacce utente (ad esempio, React Web, React Native, Angular o voice). AEM Headless Adaptive Forms è stato creato per questo: [generare una volta, distribuirlo tra React, SPA, web, dispositivi mobili e altro ancora](overview.md).
* **Authoring senza codice** - Gli utenti aziendali possono modificare campi e regole nell&#39;[Editor moduli adattivi](create-a-headless-adaptive-form.md); gli sviluppatori non devono ridistribuire le modifiche al contenuto.
* **Integrazione con gli stack esistenti** - Mantiene il sistema di progettazione, la gestione dello stato e il routing; il livello headless gestisce solo lo stato del modulo, la convalida e l&#39;invio.

## Attuazione e questioni tecniche {#implementation-technical}

### In che modo i moduli headless gestiscono lo stato?

In AEM Headless Adaptive Forms, lo stato è gestito da **Forms Web SDK**:

* **Processore regole business**: accetta il formato JSON, gestisce lo stato del campo ed esegue le regole e i gestori eventi definiti nel JSON.
* **Binder React** - Fornisce hook (ad esempio, `useRuleEngine`) sul controller in modo che i componenti React ricevano lo stato corrente e i gestori; lo stesso stato può essere utilizzato dalle interfacce utente non React tramite le API di base.
* **Stato** include i valori dei campi, la visibilità, la validità ed eventuali proprietà personalizzate definite nel modello di modulo.

I componenti dell&#39;interfaccia utente ricevono lo stato e i gestori (ad esempio, `[state, handlers] = useRuleEngine(props)`). Il rendering viene eseguito da `state` e si chiama `handlers` quando l&#39;utente interagisce. Il runtime mantiene lo stato sincronizzato con la definizione e le regole del modulo. Consulta [Architettura](architecture.md) e [Utilizzare componenti personalizzati per eseguire il rendering di un modulo headless](developing-for-headless-forms-using-your-own-components.md).

### Come funziona la convalida in una configurazione di moduli headless?

La convalida fa parte del livello logica del modulo:

* **I vincoli** sono definiti nel formato JSON (ad esempio obbligatorio, min/max, pattern). Forms Web SDK applica questi vincoli ed espone lo stato di convalida (ad esempio, messaggi di errore validi/non validi) ai componenti.
* **Convalida lato client** applicata da SDK in base alla struttura del modulo. Nell&#39;interfaccia utente vengono visualizzati errori dallo stato.
* **La convalida lato server** è disponibile tramite le API AEM (ad esempio, l&#39;endpoint di convalida); è possibile eseguire la convalida prima o durante l&#39;invio.

Non si implementa la logica di convalida nell’interfaccia utente, ma si visualizzano solo lo stato di convalida e i messaggi forniti dal runtime.

### Posso integrare i moduli headless con la convalida dello schema (Yup, Zod, Joi)?

La convalida incorporata è guidata dai vincoli JSON del modulo. Per usare Yup, Zod, Joi o simili:

* Puoi **derivare o generare** il JSON del modulo adattivo headless dallo schema (ad esempio, convertire lo schema JSON in JSON) in modo che un&#39;unica origine di verità determini sia la convalida dello schema che la struttura del modulo.
* Per la **convalida personalizzata** oltre al modulo JSON, puoi eseguire le tue convalide (Yup/Zod/Joi) nei gestori eventi o prima dell&#39;invio e inviare i risultati allo stato del modulo o al blocco dell&#39;invio. I punti di integrazione sono gli stessi hook/API utilizzati per lo stato e l’invio.

La [specifica Forms adattiva](/help/assets/headless-adaptive-forms-specification.pdf) e la [formula JSON](architecture.md) definiscono il modello di regole e vincoli utilizzato dal runtime.

### Come posso gestire la convalida asincrona (ad esempio, disponibilità del nome utente)?

La convalida asincrona può essere implementata nel livello dell’applicazione:

* Utilizza **regole o gestori eventi** nel modulo JSON (se supportato) per attivare la logica quando un campo cambia.
* Nei **componenti personalizzati**, utilizza gli stessi hook stato/gestore per chiamare il backend (ad esempio, API disponibilità nome utente), quindi aggiorna la validità del campo o visualizza un errore tramite le API di runtime o lo stato locale visualizzato nell&#39;interfaccia utente.
* In alternativa, eseguire il controllo **in caso di sfocatura o prima dell&#39;invio** e impostare lo stato del campo su non valido con un messaggio personalizzato se il controllo asincrono non riesce.

Il modello esatto dipende dal modo in cui l&#39;app si integra con il [processore per regole business](architecture.md) e i componenti personalizzati.

### Come posso inviare dati alle API utilizzando moduli headless?

L’invio è separato dall’interfaccia utente:

* **Azioni di invio AEM** - Configura il modulo in AEM per l&#39;invio a endpoint REST, e-mail o integrazioni (ad esempio, Microsoft Dynamics, Salesforce). Il modulo viene inviato tramite AEM, che gestisce la chiamata HTTP/backend effettiva. Vedi [Utilizzare gli eventi per gestire e inviare i dati del modulo](use-events-to-handle-and-submit-form-data.md).
* **Invio lato client** - L&#39;app può ascoltare o raccogliere i dati del modulo dallo stato di runtime e inviarli alle proprie API. Le [API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) elencano, recuperano, convalidano, inviano e tengono traccia dello stato di invio.
* **Precompilazione** - I dati possono essere precompilati tramite endpoint REST o lato server in modo che, al caricamento del modulo, lo stato sia già popolato. Vedi [Storybook - esempio di precompilazione](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data).

## Interfaccia utente e controllo della progettazione {#ui-design-control}

### Posso utilizzare un sistema di progettazione o una libreria di componenti personalizzati con moduli headless?

Sì. Questo è un vantaggio fondamentale dei moduli headless. Con AEM Headless Adaptive Forms:

* **mappi** i tuoi componenti al modello del modulo (per tipo di campo o di risorsa). Consulta [Utilizzare componenti personalizzati per eseguire il rendering di un modulo headless](developing-for-headless-forms-using-your-own-components.md) e [Utilizzare i componenti React dell&#39;interfaccia utente di Google Material per eseguire il rendering di un modulo headless](use-google-material-ui-react-components-to-render-a-headless-form.md).
* Il runtime fornisce **lo stato e i gestori**; i componenti eseguono il rendering utilizzando il sistema di progettazione e chiamano i gestori in modo che la logica del modulo rimanga sincronizzata.
* Puoi utilizzare **React Spectrum**, Material UI, Chakra UI o qualsiasi libreria di componenti personalizzata; la [specifica](/help/assets/headless-adaptive-forms-specification.pdf) può essere estesa per i componenti personalizzati (ad esempio, Chakra UI, Vue.js). Vedi [Domande frequenti - framework personalizzati](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks).

### I moduli headless supportano l’accessibilità (ARIA, gestione della tastiera)?

L&#39;accessibilità è implementata nel **livello interfaccia utente** fornito. Il livello headless non esegue il rendering del DOM, pertanto non aggiunge ARIA o il comportamento della tastiera di per sé. Per ottenere l’accessibilità, segui questi passaggi:

* Utilizzo di **componenti accessibili** dal sistema di progettazione o dalla libreria (molti includono il supporto per ARIA e tastiera).
* Segui le **best practice per l&#39;accessibilità** nei componenti dei campi personalizzati (etichette, messaggi di errore, gestione dello stato attivo, navigazione da tastiera).
* Assicurati che la struttura e lo stato del modulo ricevuti (ad esempio obbligatorio, non valido, visibile) si riflettano negli attributi e nel comportamento ARIA dei componenti.

Se utilizzi i componenti predefiniti basati su React Spectrum, puoi sfruttare la loro accessibilità incorporata.

### Come posso gestire componenti dell’interfaccia utente complessi (selettori di date, elenchi a discesa personalizzati)?

Considerali come **componenti personalizzati** mappati ai tipi di campo corrispondenti o ai tipi di risorse personalizzate in formato JSON:

* Implementa il componente per accettare gli stessi **prop/stato/gestori** degli altri componenti del campo (ad esempio tramite `useRuleEngine`).
* Utilizza **state** per valore, visibilità e validità; utilizza **handler** per aggiornare il valore e attivare la convalida.
* Esegui il rendering del selettore di date o del menu a discesa personalizzato con la libreria dell’interfaccia utente scelta. Al momento della modifica, chiama il gestore con il nuovo valore in modo che lo stato del modulo rimanga corretto.

Vedi [Utilizzare componenti personalizzati per eseguire il rendering di un modulo headless](developing-for-headless-forms-using-your-own-components.md) per la mappatura per tipo di campo e tipo di risorsa.

### È possibile aggiungere o rimuovere campi (moduli dinamici) in modo dinamico?

La struttura del modulo è definita dal **modulo JSON** restituito dal server. Il comportamento dinamico si ottiene:

* **Regole nel formato JSON**: mostrare/nascondere, abilitare/disabilitare o impostare valori in base alle espressioni. Il processore [regola business](architecture.md) esegue queste regole. I componenti reagiscono a `state.visible` e simili.
* **Struttura basata su server** - Utenti o contesti diversi possono ricevere JSON in moduli diversi (ad esempio passaggi o sezioni diverse), pertanto &quot;dinamico&quot; può significare &quot;definizione di modulo diversa per richiesta&quot;.
* **Modifiche lato client** - Se l&#39;app può modificare il modello del modulo (ad esempio, aggiungere/rimuovere elementi in una struttura ripetibile), il runtime può rifletterlo; la funzionalità esatta dipende dallo schema del modulo e dalle API di runtime.

Il [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) include esempi di comportamento dinamico.

### Come posso gestire i campi condizionali (mostrare/nascondere in base all’input)?

La visibilità condizionale è guidata da **regole** nel formato JSON, valutata dal processore delle regole business. È possibile definire le condizioni (ad esempio, &quot;quando il campo A è uguale a X, mostra il campo B&quot;); lo stato di aggiornamento del runtime (ad esempio, `state.visible`). I componenti devono solo **rispettare lo stato** (ad esempio, `if (!state.visible) return null;`). Non è richiesta alcuna logica aggiuntiva dell’interfaccia utente per mostrare/nascondere elementi oltre il rendering dallo stato. Il comportamento a cascata e condizionale è documentato nella [specifica di Forms adattivo](/help/assets/headless-adaptive-forms-specification.pdf) ed è dimostrato in [Storybook - campi a cascata](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down). Vedi anche [Domande frequenti - campi a catena](faq.md#do-headless-adaptive-forms-support-cascading-fields).

## Prestazioni e scalabilità {#performance-scalability}

### I moduli headless sono più performanti delle librerie di moduli tradizionali?

Possono essere, ma dipende dall’implementazione:

* **Aggiornamenti mirati** - Un runtime headless ben progettato aggiorna solo lo stato che è stato modificato e notifica solo i componenti che dipendono da esso, riducendo così i rirendering non necessari rispetto a un componente modulo monolitico.
* **Bundle interfaccia utente più piccolo** - Spedisci solo i componenti dell&#39;interfaccia utente utilizzati (sistema di progettazione), non un set completo di componenti libreria.
* **Caricamento differito** - Il JSON del modulo può essere recuperato quando necessario; il bundle iniziale può rimanere più piccolo.

Le prestazioni dipendono anche dal modo in cui vengono implementati i componenti (ad esempio, evitando rendering non necessari, memorie).

### In che modo riducono al minimo i rendering?

* **Forma stato** - Il runtime mantiene lo stato del modulo in una struttura che consente aggiornamenti dettagliati, in modo che solo le parti interessate della struttura debbano essere rieseguite.
* **Progettazione hook** - È possibile implementare hook come `useRuleEngine` per sottoscrivere i componenti solo allo stato in uso, pertanto le modifiche a livello di padre o di pari livello non forzano il rendering di ogni campo.
* **Responsabilità** - Puoi ridurre ulteriormente i rendering utilizzando le best practice React (ad esempio, `React.memo`, callback stabili) nei componenti personalizzati.

### I moduli headless hanno una buona scalabilità per i moduli di grandi dimensioni e con più passaggi?

Sì, se progettato in modo appropriato:

* **Definizione modulo** - I moduli di grandi dimensioni possono essere suddivisi in passaggi o sezioni nel JSON; solo il passaggio o la sezione visibile potrebbe dover essere completamente attivo nell&#39;interfaccia utente, con valutazione lenta delle regole per le sezioni nascoste, se supportata.
* **Stato** - Il runtime contiene uno stato di modulo coerente. La navigazione dei passaggi mostra o nasconde sezioni o aggiorna il &quot;passaggio corrente&quot; senza duplicare i dati.
* **Chunking e caricamento lento** - Puoi recuperare il JSON del modulo in blocchi o caricare sezioni aggiuntive al passaggio di avanzamento per mantenere basso il payload iniziale e il costo di analisi.

Per i moduli di grandi dimensioni, considera la struttura (ad esempio, i passaggi della procedura guidata), le varianti di moduli guidate dal server e la misurazione dell’esecuzione di rendering e regole con payload reali.

## Integrazione ed ecosistema {#integration-ecosystem}

### I moduli headless possono funzionare con le azioni Next.js/SSR/Server?

* **Next.js / React** - Sì. Il renderer React e gli hook funzionano in un ambiente React. Utilizza Forms Web SDK nei componenti client; recupera il JSON modulo sul server o sul client in base alle esigenze.
* **SSR** - È possibile recuperare il modulo JSON sul server e passarlo al client in modo che il modulo si idrati con i dati. L’interattività del modulo (stato, convalida, regole) viene eseguita sul client in cui viene caricato SDK. Evita il rendering dei campi modulo che dipendono dallo stato solo del client durante SSR, oppure utilizza un segnaposto che idrata sul client.
* **Azioni server (Next.js)** - È possibile chiamare Azioni server dal gestore di invio: quando l&#39;utente invia, il codice client raccoglie i dati del modulo (dallo stato headless) e chiama un&#39;azione server invece o in aggiunta agli endpoint di invio di AEM.

### In che modo i moduli headless si integrano con CMS, e-commerce headless o sistemi back-end?

* **CMS** - AEM è il CMS per la definizione del modulo: gli autori creano e pubblicano il modulo JSON. Altri CMS possono fare riferimento o collegarsi al modulo URL/API. L’app recupera il modulo da AEM (o da una rete CDN) e, facoltativamente, estrae una copia o un layout da un altro CMS.
* **Precompila e invia** - [Precompila](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) e invia possono raggiungere gli endpoint REST, quindi puoi precompilare da un back-end CRM, DAM o commerce e inviare allo stesso sistema o a sistemi diversi. AEM Forms supporta anche [Microsoft Dynamics e Salesforce](faq.md), REST, e-mail e azioni di invio personalizzate.
* **Forms Data Model** - AEM Forms fornisce un Forms Data Model per connettersi a diverse origini dati; i moduli headless possono utilizzare queste funzionalità per la precompilazione, la convalida e l&#39;invio senza dover creare personalmente ogni integrazione.

Per gli scenari mobili e offline, l&#39;approccio consigliato è quello di [creare la propria app e recuperare le definizioni dei moduli tramite l&#39;API Forms adattiva headless](mobile-forms-best-practices.md).

## Consulta anche {#see-also}

* [Panoramica](overview.md)
* [Architettura](architecture.md)
* [Domande frequenti](faq.md)
* [Creare e pubblicare un modulo headless](create-and-publish-a-headless-form.md)
* [API per moduli adattivi headless](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [Playground del codice](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=en)
* [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
