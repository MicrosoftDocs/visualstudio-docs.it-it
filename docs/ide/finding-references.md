---
title: Ricerca di riferimenti nel codice | Microsoft Docs
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92c12e4d51255849843f938c032ca17b611eeeab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="finding-references-in-your-code"></a>Ricerca di riferimenti nel codice  
Per trovare i riferimenti a particolari elementi di codice presenti nella codebase è possibile usare il comando **Trova tutti i riferimenti**. Il comando **Trova tutti i riferimenti** è disponibile nel menu di scelta rapida (clic con il pulsante destro del mouse) dell'elemento per il quale si vuole trovare i riferimenti. In alternativa, se si preferisce usare la tastiera, premere **MAIUSC+F12**.  

I risultati vengono visualizzati in una finestra degli strumenti denominata **"*elemento*" riferimenti**, in cui *elemento* è il nome dell'elemento cercato. Una barra degli strumenti nella finestra dei **riferimenti** consente di:  
- Modificare l'ambito della ricerca in un elenco a discesa. È possibile scegliere di eseguire la ricerca solo nei documenti modificati o nell'intera soluzione.  
- Copiare l'elemento di riferimento selezionato scegliendo il pulsante **Copia**.  
- Scegliere i pulsanti per passare alla posizione precedente o successiva nell'elenco oppure premere **F8** e **MAIUSC+F8** per eseguire questa operazione.  
- Rimuovere tutti i filtri applicati ai risultati restituiti scegliendo il pulsante **Cancella tutti i filtri**.  
- Modificare il raggruppamento degli elementi restituiti scegliendo un'impostazione nell'elenco a discesa **Raggruppa per**.  
- Mantenere la finestra dei risultati della ricerca corrente scegliendo il pulsante **Mantieni risultati**. Quando si sceglie questo pulsante, i risultati della ricerca corrente rimangono in questa finestra e i nuovi risultati vengono visualizzati in una nuova finestra degli strumenti.  
- Cercare stringhe nei risultati della ricerca immettendo il testo nella casella di testo **Cerca in Trova tutti i riferimenti**.  

È anche possibile passare con il puntatore del mouse su un risultato della ricerca per visualizzare un'anteprima del riferimento.  

![Finestra degli strumenti Trova tutti i riferimenti](../ide/media/vside_findallreferences.png)  

### <a name="navigate-to-references"></a>Passare ai riferimenti
Per passare ai riferimenti nella finestra dei **riferimenti** è possibile usare i metodi seguenti:  

- Premere **F8** per passare al riferimento successivo oppure **MAIUSC+F8** per passare al riferimento precedente.  
- Premere **INVIO** su un riferimento oppure fare doppio clic su di esso per passare al riferimento nel codice.  
- Nel menu di scelta rapida di un riferimento scegliere i comandi **Vai alla posizione precedente** o **Vai alla posizione successiva**.  
- Premere i tasti **freccia SU** e **freccia GIÙ**, se sono abilitati nella finestra di dialogo Opzioni. Per abilitare questa funzionalità, nella barra dei menu scegliere **Strumenti**, **Opzioni**, **Ambiente**, **Schede e finestre**, **Scheda anteprima** e quindi selezionare le caselle **Consenti apertura nuovi file nella scheda anteprima** e **Anteprima file selezionati in Risultati ricerca**.  

### <a name="change-reference-groupings"></a>Modificare i raggruppamenti di riferimenti  
Per impostazione predefinita, i riferimenti sono raggruppati prima in base al progetto e quindi in base alla definizione. È però possibile modificare questo ordine di raggruppamento modificando l'impostazione nell'elenco a discesa**Raggruppa per** sulla barra degli strumenti. Ad esempio, è possibile modificare l'impostazione predefinita **Progetto, quindi definizione** in **Definizione, quindi progetto** o in altre impostazioni.  

I due raggruppamenti predefiniti usati sono **Definizione** e **Progetto**, ma è possibile aggiungerne altri scegliendo il comando **Raggruppamento** nel menu di scelta rapida dell'elemento selezionato. L'aggiunta di più raggruppamenti può essere utile se la soluzione contiene molti file e percorsi.  

## <a name="see-also"></a>Vedere anche  
[Esplorazione del codice](../ide/navigating-code.md)  