---
title: Personalizzare la modalità Visual Studio crea le didascalie per controlli associati a dati
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 35bcc2ed38a8330e7eb4ab38416c91a5c51ec2d4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizzare la modalità Visual Studio crea le didascalie per controlli associati a dati
Quando si trascinano elementi dal [finestra Origini dati](add-new-data-sources.md) in una finestra di progettazione, tenere presente che in: i nomi di colonna nelle etichette della didascalia vengono riformattati in una stringa più leggibile quando due o più parole risultano concatenate. È possibile personalizzare il modo in cui vengono create le etichette, impostando il **SmartCaptionExpression**, **SmartCaptionReplacement**, e **SmartCaptionSuffix** i valori in il **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data progettisti** chiave del Registro di sistema.

> [!NOTE]
> Questa chiave del Registro di sistema non esiste fino a quando non viene creata.

Didascalia smart è controllata dall'espressione regolare inserito il valore di **SmartCaptionExpression** valore. Aggiunta di **finestre di progettazione dati** chiave del Registro di sistema esegue l'override dell'espressione regolare predefinita che controlla le etichette della didascalia. Per ulteriori informazioni sulle espressioni regolari, vedere [utilizzando espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Nella tabella seguente vengono descritti i valori del Registro di sistema che controllano le etichette della didascalia.

|Elemento Registro di sistema|Descrizione|
|-------------------|-----------------|
|**SmartCaptionExpression**|L'espressione regolare utilizzata per la corrispondenza dei modelli.|
|**SmartCaptionReplacement**|Il formato di visualizzazione di una corrispondenza con tutti i gruppi di **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Stringa facoltativa da aggiungere alla fine della didascalia.|

La tabella seguente elenca le impostazioni predefinite interne per questi valori del Registro di sistema.

|Elemento Registro di sistema|Valore predefinito|Descrizione|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|Consente di ricercare un carattere minuscolo seguito da un carattere maiuscolo o un carattere di sottolineatura.|
|**SmartCaptionReplacement**|$1 $2|$1 rappresenta i caratteri di una corrispondenza con le parentesi prima dell'espressione e $2 rappresenta i caratteri di cui trovare una corrispondenza nella seconda parentesi. La sostituzione è la prima corrispondenza, uno spazio e quindi la seconda corrispondenza.|
|**SmartCaptionSuffix**|:|Rappresenta un carattere aggiunto alla stringa restituita. Se, ad esempio, la didascalia è `Company Name`, il suffisso rende `Company Name:`|

> [!CAUTION]
> È necessario prestare particolare attenzione nell'eseguire alcuna operazione nell'Editor del Registro di sistema. Eseguire il backup del Registro di sistema prima di modificarlo. Se si utilizza l'Editor del Registro di sistema in modo non corretto, può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che sia possono risolvere i problemi derivanti dall'errato utilizzo dell'Editor del Registro di sistema. L'utilizzo dell'editor del Registro di sistema è a rischio dell'utente.
>
>  Il seguente articolo della Knowledge Base contiene istruzioni per il backup, la modifica e il ripristino del Registro di sistema: [descrizione del Registro di sistema Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Per modificare il comportamento della didascalia smart della finestra Origini dati

1.  Aprire una finestra di comando facendo **avviare** e quindi **eseguire**.

2.  Tipo `regedit` nel **eseguire** la finestra di dialogo e fare clic su **OK**.

3.  Espandere il **HKEY_CURRENT_USER**, **Software*, **Microsoft**, **VisualStudio** nodo.

7.  Fare doppio clic su di **15.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.

8.  Fare doppio clic su di **finestre di progettazione dati** nodo e creare tre nuovi valori di stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Fare doppio clic su di **SmartCaptionExpression** valore e selezionare **modifica**.

12. Immettere l'espressione regolare che si desidera il **origini dati** finestra da usare.

13. Fare doppio clic su di **SmartCaptionReplacement** valore e selezionare **modifica**.

14. Immettere la sostituzione stringa formattati nel modo in cui si desidera visualizzare i modelli corrispondenti nell'espressione regolare.

15. Fare doppio clic su di **SmartCaptionSuffix** valore e selezionare **modifica**.

16. Immettere i caratteri che si desidera venga visualizzato alla fine della didascalia.

    La volta successiva che si trascinano elementi dal **origini dati** finestra, le etichette della didascalia vengono create utilizzando i nuovi valori del Registro di sistema forniti.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Per disattivare la funzionalità di sottotitoli codificata intelligente

1.  Aprire una finestra di comando facendo **avviare** e quindi **eseguire**.

2.  Tipo `regedit` nel **eseguire** la finestra di dialogo e fare clic su **OK**.

3.  Espandere il **HKEY_CURRENT_USER**, **Software**, **Microsoft**, **VisualStudio** nodo.

7.  Fare doppio clic su di **15.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.

8.  Fare doppio clic su di **finestre di progettazione dati** nodo e creare tre nuovi valori di stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Fare doppio clic su di **SmartCaptionExpression** elemento e selezionare **modifica**.

12. Immettere `(.*)` per il valore. Ciò corrisponderà alla stringa intera.

13. Fare doppio clic su di **SmartCaptionReplacement** elemento e selezionare **modifica**.

14. Immettere `$1` per il valore. Ciò consente di sostituire la stringa con il valore corrispondente, ovvero l'intera stringa, in modo che rimarrà invariata.

    La volta successiva che si trascinano elementi dal **origini dati** finestra, le etichette della didascalia vengono create con didascalie non modificate.

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)