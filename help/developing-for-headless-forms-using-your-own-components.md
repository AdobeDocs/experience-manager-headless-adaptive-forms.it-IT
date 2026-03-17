---
title: Utilizzare componenti personalizzati per eseguire il rendering di un modulo headless
description: Scopri come creare componenti personalizzati e mapparli sui campi Forms adattivo headless. Questa guida spiega come mappare i componenti per tipo di campo e tipo di risorsa per ottenere un rendering e un comportamento personalizzati.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Utilizzare componenti personalizzati per eseguire il rendering di un modulo headless {#developing-for-headless-forms-using-your-own-components}

In Headless Adaptive Forms puoi creare e implementare componenti personalizzati per definire l’aspetto e le funzionalità dei moduli. Anche se i componenti predefiniti forniscono un comportamento standard, potrebbe essere necessario specificare elementi o interazioni dell’interfaccia utente, ad esempio un componente personalizzato &quot;Annuncio&quot; o un campo specifico &quot;Firma a mano&quot;.

Questo articolo ti guida attraverso la creazione di un componente React personalizzato e la mappatura sul tuo modulo adattivo headless.

## &#x200B;1. Creare un componente React personalizzato

Innanzitutto, crea il componente React che eseguirà il rendering del campo modulo. Questo componente può utilizzare qualsiasi libreria React (come l’interfaccia utente Materiali, Progettazione formiche o stili personalizzati).

Ad esempio, creiamo un componente **Annuncio** personalizzato che esegue il rendering di un messaggio di sola lettura con uno stile specifico.

1. Passare alla directory dei componenti del progetto React (ad esempio, `src/components`).
2. Creare una nuova cartella e un nuovo file per il componente, ad esempio `Announcement/index.tsx`.
3. Implementa il componente. Deve accettare `props` compatibile con il runtime Forms headless (in genere riceve lo stato del campo).

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. Mappare il componente personalizzato

Per utilizzare il componente personalizzato, è necessario mapparlo nel file `mappings.ts`. Il runtime Forms headless utilizza questo mapping per determinare quale componente React eseguire il rendering per ogni campo nel formato JSON.

Esistono due modi principali per mappare i componenti: per **Tipo campo** o per **Tipo risorsa**.

### Mappatura per tipo di campo

Il mapping standard è basato sulla proprietà `fieldType` nel JSON del modulo (ad esempio, `text-input`, `checkbox`, `button`). Questa opzione è utile quando si desidera sostituire *tutte* le istanze di un componente standard con la versione personalizzata.

1. Apri `src/utils/mappings.ts` (o dove sono definite le mappature).
2. Importa il componente personalizzato.
3. Aggiungerlo all&#39;oggetto mapping utilizzando `fieldType` come chiave.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### Mappatura per tipo di risorsa (componenti personalizzati)

Se hai creato un componente personalizzato in AEM (ad esempio, un componente &quot;Annuncio&quot; che estende un componente Testo standard) e vuoi eseguire il rendering di *solo* tale componente in modo diverso nell&#39;app React, devi mapparlo in base al suo **Tipo risorsa** o a un identificatore univoco.

Questo approccio consente di eseguire normalmente il rendering dei componenti di testo standard, mentre il componente personalizzato &quot;Annuncio&quot; utilizza l’implementazione di React specializzata.

1. Identifica l’identificatore univoco del componente. Nel JSON del modulo headless, questo si trova spesso nella proprietà `:type` o in un `fieldType` personalizzato, se configurato.
2. Aggiungi la mappatura utilizzando questo identificatore.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **Nota:** assicurarsi che il modello AEM Form esporti il `:type` o l&#39;identificatore corretto corrispondente alla chiave utilizzata in `mappings.ts`.

## &#x200B;3. Applicare le mappature

Infine, assicurati che l’istanza del modulo headless utilizzi queste mappature personalizzate.

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

Seguendo questi passaggi, puoi estendere le funzionalità del Forms adattivo headless con componenti che soddisfano i requisiti di progettazione e funzionali specifici.
