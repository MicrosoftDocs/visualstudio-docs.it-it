---
title: Strumenti di valutazione per Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a149d9163e61dd49105f123b373ecd9c7c1c278
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="evaluation-tools-for-visual-studio"></a>Strumenti di valutazione per Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Elenco di controllo di prodotti per Visual Studio  
 Utilizzare questo elenco di controllo per valutare qualità delle prestazioni per i dettagli visivi e interazione dell'utente.  
  
### <a name="overview"></a>Panoramica  
  
-   Verificare che tutti i comandi generi commenti e suggerimenti che indica gli utenti che sono stati effettuati i relativi comandi.  
  
-   Verificare che tutti gli elementi dell'interfaccia utente e i controlli sono visibili in tutti i temi e in modalità a contrasto elevato.  
  
-   Verificare che inattiva e attiva la selezione si distinguano sempre, sia in modalità a contrasto elevato e di standard.  
  
-   Verificare che lo stato attivo è sempre visibile e apparente.  
  
### <a name="performance"></a>Prestazioni  
  
-   Verificare che un tipo di "occupato" indicatore viene visualizzato se un comando ha più di un secondo.  
  
-   Verificare che se un comando richiede più di 10 secondi per completare un indicatore di stato esplicita, ovvero determinata (scelta consigliata) o indeterminato, viene visualizzato.  
  
### <a name="ui-text"></a>Testo dell'interfaccia utente  
  
-   Verificare che tutte le etichette sono frase o in maiuscolo e che il testo non è in minuscolo completamente.  
  
    ||Correggere|Non corretto|  
    |-|-------------|---------------|  
    |**Testo del comando (tutto)**|Caso di frase:<br /><br /> **Nome della directory:**|Nome della directory:|  
    |**Testo del pulsante (client)**|Iniziali maiuscole:<br /><br /> **[Predefinito]**|SET AS DEFAULT|  
    |**Testo del pulsante (online)**|Caso di frase:<br /><br /> **[Impostazione predefinita]**||  
  
-   Verificare che tutte le etichette, ad eccezione di intestazioni di gruppo e i pulsanti, terminano con un virgola e precedono il controllo a cui essi sono abbinati.  
  
-   Verificare che i pulsanti, comandi e collegamenti ai comandi di avvio dell'interfaccia utente per acquisire l'input dell'utente terminano con i puntini di sospensione **[…]** .  
  
     Esempi:  
  
    -   Un **[avanzate...]**  pulsante in una finestra di dialogo.  
  
    -   Le opzioni di comando del menu Strumenti (**strumenti > Opzioni**) non deve ricevere i puntini di sospensione, perché la finestra di dialogo di avvio è lo scopo del comando.  
  
-   Verificare che l'interfaccia utente è incluso alcun abbreviazioni, ad eccezione di termini standard del settore. Ad esempio HTML né TCP/IP necessario pronunciata, sebbene PII (informazioni personali) e memoria insufficiente (memoria insufficiente) deve.  
  
### <a name="keyboard-access"></a>Accesso da tastiera  
  
-   Verificare che sia presente un modo per eseguire ogni attività con la tastiera. In genere questa operazione viene eseguita tramite l'accesso da tastiera per ogni controllo, ma per alcune aree elevato impatto visivo, risolvere il problema, ad esempio passare alla visualizzazione del codice è accettabile.  
  
-   Verificare che può spostarsi tra i controlli in un ordine logico (da sinistra a destra e dall'alto al basso). Si tratta di una procedura consigliata per la maggior parte dei controlli, non tutti i controlli richiedono questo approccio. Ad esempio, verificare tale pulsante di opzione sono controlli in un gruppo con un singolo punto di tabulazione.  
  
-   Verificare che tutti i controlli di etichette e che ogni etichetta dispone di un tasto di scelta (eccezioni includono alcuni controlli con l'etichetta non potrebbero seguire un controllo etichettato nella scheda).  
  
-   Verificare che non sono presenti conflitti di tasti di scelta rapida.  
  
### <a name="fonts"></a>Tipi di carattere  
  
-   Verificare che tutti i tipi di carattere (tipo di carattere, dimensione, colore) vengono utilizzati in modo coerente e mantenere una gerarchia.  
  
-   Verificare che tutti gli elementi dell'interfaccia utente utilizzano il servizio di tipo di carattere ambiente. (Vedere [caratteri e la formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Per verificare se il servizio è in uso, passare a **strumenti > Opzioni > tipi di carattere e colori**. Le impostazioni dal menu a discesa Scegli tipo di carattere ambiente e modificare il tipo di carattere a un elemento stylistically diverso (ad esempio Harrington o Comic Sans) e impostare le dimensioni a 12 punti. Fare clic su OK. Potrebbe essere necessario riavviare l'IDE, ma la maggior parte dell'interfaccia utente verrà modificata immediatamente. Le aree che non ricevono la modifica del tipo di carattere anche al riavvio non si utilizzano il tipo di carattere ambiente.  
  
-   Verificare che i tipi di carattere derivato del servizio (ad esempio, testo in grassetto o ingrandito) mantenere le dimensioni e la formattazione in relazione a "normale" testo quando viene modificata la dimensione del carattere di ambiente.  
  
-   Verificare che non ci sono bug ritaglio a causa di tipi di carattere ingrandite. I tipi di carattere ottenere troncati sono probabilmente il risultato dei controlli di altezza fissa o contenitori altezza fissa.  
  
### <a name="dialogs"></a>Finestre di dialogo  
  
-   Verificare che il titolo della finestra di comando che l'ha avviata.  
  
-   Verificare che tutti i controlli standard siano coerenti con il sistema operativo: colore di sfondo è standard e non i controlli devono avere uno stile basato su modelli r speciale che li rende un aspetto diverso da controlli standard.  
  
-   Verificare che i margini all'interno del form devono essere 12 pixel e dovrebbero essere visualizzato uniforme e coerente.  
  
-   Verificare che appaiano centrati all'interno di shell di IDE o nella finestra che ha generato le finestre di dialogo.  
  
-   Quando si rivela utile, finestre di dialogo possono essere ridimensionati. Per i dialoghi che sono ridimensionabili, verificare che al momento del ridimensionamento, necessario ridimensionare i controlli appropriati mentre altre parti della finestra di dialogo rimangano costante.  
  
-   Verificare che le finestre di dialogo ridimensionabili mantenere qualsiasi dimensione regolare utente (dimensioni, posizione, espansione di controlli di finestra di dialogo e così via).  
  
-   Verificare che non vi sia alcuna icona nella barra del titolo.  
  
-   Verificare che non sono presenti pulsanti Riduci a icona e Ingrandisci nella barra del titolo.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Pulsanti di operazione di finestra di dialogo (solo Client di Visual Studio)  
  
-   Verificare che i pulsanti di operazione in questo ordine: **OK**, **Annulla**, **applica**.  
  
-   Verificare che **OK** e **Annulla** pulsanti sono le dimensioni standard: x 23 di 75 pixel.  
  
-   Verificare che **OK** e **Annulla** pulsanti sono della stessa dimensione indipendentemente dalla lunghezza della stringa.  
  
-   Se l'etichetta su un pulsante di operazione richiede il pulsante deve essere maggiore di standard, verificare che il corrispondente **Annulla** pulsante è di dimensioni uguali.  
  
-   Verificare che sia presente un riempimento 6 pixel tra i pulsanti e i controlli associati.  
  
-   Verificare che il **OK** e **Annulla** pulsanti non dispone di tasti di accesso definito da una lettera sottolineata.  
  
-   Verificare che un pulsante (in genere **OK**) ha lo stato attivo per impostazione predefinita.  
  
-   Verificare che **Esc** Annulla la finestra di dialogo  
  
-   Verificare che **invio** esegue il pulsante predefinito, se lo stato attivo non è presente in un controllo che elabora l'invio.  
  
-   Verificare che il **OK** e **Annulla** pulsanti sono posizionati nell'angolo inferiore destro della finestra di dialogo. In rare eccezioni, è accettabile per poter essere sovrapposti in verticale in alto a destra.  
  
-   Verificare che la configurazione verticale viene utilizzata solo se gli altri pulsanti si trovano l'allineamento orizzontale nella finestra di dialogo.  
  
### <a name="control-standards"></a>Standard di controllo  
  
#### <a name="general"></a>Generale  
  
-   Verificare che, quando possibile, esistono buone valori predefiniti per velocizzare l'interazione dell'utente e indirizzare gli utenti verso un risultato di tipo safe o comune.  
  
-   Verificare che i controlli standard si comportano allo stesso modo, in modo che gli utenti sanno cosa accade in base all'esperienza precedente.  
  
#### <a name="label-controls"></a>Controlli Label  
  
-   Verificare che ogni controllo dispone di un'etichetta e ogni etichetta visivamente è associato al relativo controllo (in genere all'interno di un intervallo di pixel 4-6), è più vicino al relativo controllo corrispondente rispetto ad altri controlli.  
  
-   Verificare che le etichette vengono posizionate allineamento a sinistra con il controllo del bordo sinistro se posizionata di sopra e al centro orizzontalmente, in modo che la linea di base dell'etichetta è allineata alla linea di base del testo di input se posizionata a sinistra.  
  
-   Verificare che se diverse in pila etichetta e i controlli di input si trovano a sinistra di un controllo, le etichette sono allineamento a sinistra e alla stessa distanza dal bordo della finestra di dialogo, non scaricare mai destra e alla stessa distanza dai controlli. Coppie devono essere distribuite in modo uniforme a meno che non hanno bisogno la spaziatura per indicare il raggruppamento.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controlli di input (caselle di testo e caselle combinate)  
  
-   Verificare che quando si utilizza il tipo di carattere ambiente predefinito, l'altezza di visualizzazione per le caselle di testo, pulsanti e caselle combinate sono tutti di 23 pixel.  
  
-   Se viene utilizzato testo di suggerimento, verificare che il colore è impostato su `Environment.ControlEditHintText` mediante il servizio di colore.  
  
-   Se il campo è un campo obbligatorio che deve essere identificato come tali, verificare che:  
  
    -   che lo sfondo è impostato su `Environment.ControlEditRequiredBackground` e primo piano è impostato su `Environment.ControlEditRequiredHintText`  
  
    -   che vi sia all'interno del controllo che viene visualizzato come testo del suggerimento **"\<necessari >"**  
  
#### <a name="button-controls"></a>Controlli pulsante  
  
-   Verificare che i pulsanti sono una dimensione minima di 75 x 23 pixel, a meno che l'aggiunta di testo più lungo.  
  
-   Verificare che i pulsanti destra e sinistra margini di 3-5 pixel, nonché la spaziatura interna per il contenuto.  
  
-   È possibile utilizzare un piccolo pulsante quadrato con solo i puntini di sospensione **[…]**  su di esso anziché un **[Sfoglia...]**  pulsante (o simile). Se utilizzato, verificare che il pulsante è 23 x 23 nella dimensione.  
  
-   Se è presente più di **[Sfoglia...]**  pulsante in una finestra di dialogo, quindi verificare che la versione abbreviata (solo per i puntini di sospensione **[…]** ) viene utilizzato per tutti.  
  
-   Verificare che i puntini di sospensione **[…]**  pulsanti non dispone di un tasto di scelta rapida. Quando lo stato attivo sul controllo di input corrispondente, una sola scheda di spostare lo stato attivo sul pulsante con i puntini di sospensione.  
  
-   Verificare che i pulsanti, comandi e collegamenti ai comandi che avviano l'interfaccia utente secondaria per l'acquisizione di più input dell'utente deve terminare con i puntini di sospensione **[…]** .  
  
#### <a name="hyperlinks"></a>Collegamenti ipertestuali  
  
-   Verificare che un controllo hyperlink non lampeggia mai rosso quando sono attive. Si tratta di un indicatore che il servizio di colore non venga utilizzare  
  
-   Verificare che i colori di Visual Studio utilizzati sono:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Verificare che i collegamenti ipertestuali vengono visualizzati con alcun carattere di sottolineatura blu a meno che non incorporato in un paragrafo.  
  
#### <a name="check-boxes"></a>Caselle di controllo  
  
-   Se una casella di controllo è di tipo testo su più righe, verificare che la casella in linea con la prima riga di testo, non centrato verticalmente su tutte le righe.  
  
-   Verificare che le caselle di controllo sempre indicano una scelta binaria e non mostrare all'utente o aprire nuove finestre o pagine.  
  
-   Se una casella di controllo presenta un'opzione correlata a un controllo di input, verificare che sia posizionato allineamento a sinistra e molto chiudere sotto tale controllo per indicare la relazione.  
  
-   Verificare che sia una casella di controllo **mai** utilizzata come mezzo per abilitare l'intero contenuto di una finestra di dialogo o una pagina.  
  
#### <a name="group-boxes"></a>Caselle di gruppo  
  
-   Verificare che una finestra di dialogo non contiene una casella di gruppo singola in esso contenuti che contiene l'intero contenuto della finestra di dialogo.  
  
-   Verificare che siano presenti almeno due controlli all'interno di ogni casella di gruppo.  
  
-   Raramente devono essere presenti più di due caselle di gruppo in una finestra di dialogo.  
  
-   Verificare che non ci sono gruppo nidificato.  
  
### <a name="icons"></a>Icone  
  
-   Verificare che le icone vengono visualizzate correttamente invertite quando nel tema scuro.  
  
-   Verificare che tutte le icone si basano su concetti di base.  
  
-   Verificare che ogni icona è distinct, facile da riconoscere e non contiene più di due concetti (senza stato modificatore/language).  
  
-   Verificare che l'icona base centrato all'interno dello spazio.  
  
-   Verificare che tutte le icone appaiano leggibile in modalità a contrasto elevato.  
  
-   Verificare che qualsiasi colore utilizzato sia allineata con gli standard di utilizzo di colore.  
  
-   Verificare che non esistono alcun alone (bordi) intorno icone. (Se presente, alone deve corrispondere il colore di sfondo dell'interfaccia utente adiacente).  
  
### <a name="touch-enabled-ui"></a>Interfaccia utente abilitato per il tocco  
  
-   Verificare che siano sufficientemente grandi da essere facilmente touchable - minimo controlli interattivi **23 x 23 pixel** dimensioni  
  
-   Verificare che i controlli utilizzati più di frequente siano almeno **40 x 40 pixel** dimensioni.  
  
-   Verificare che dispongano almeno di controlli interattivi **5 pixel di spaziatura** tra di essi