---
title: Aggiunta di icone ai comandi di Menu | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8591c55a176493ace23df2de61ba26d58a3155e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-icons-to-menu-commands"></a>Aggiunta di icone ai comandi di Menu
I comandi possono apparire su entrambi i menu e barre degli strumenti. Sulla barra degli strumenti, è comune per un comando da visualizzare solo un'icona (per risparmiare spazio) durante il menu che viene visualizzato in genere un comando con un'icona e testo.  
  
 Le icone sono 16 pixel di larghezza per 16 pixel di altezza e possono essere profondità di colore a 8 bit (256 colori) o profondità di colore a 32 bit (colore a true). icone di colori a 32 bit sono preferite. Le icone vengono disposte in genere in una singola riga orizzontale in una singola bitmap, anche se sono consentite più immagini bitmap. Questa bitmap è dichiarata nel file vsct insieme le singole icone disponibili nella bitmap. Vedere la Guida di riferimento per il [elemento bitmap](../extensibility/bitmaps-element.md) per altri dettagli.  
  
## <a name="adding-an-icon-to-a-command"></a>Aggiunta di un'icona per un comando  
 La procedura seguente si presuppone che si dispone di un progetto VSPackage esistente con un comando di menu. Per informazioni su come eseguire questa operazione, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Creare una bitmap con una profondità di colore pari a 32 bit. Un'icona è sempre un multiplo di 16 pixel di larghezza e di 16 x 16, pertanto questa bitmap deve essere 16 pixel di altezza.  
  
     Ogni icona viene posizionato su una bitmap uno accanto a altro in una singola riga. Utilizzare il canale alfa per indicare posizioni di trasparenza in ogni icona.  
  
     Se si utilizza una profondità di colore a 8 bit, utilizzare magenta, `RGB(255,0,255)`, come la trasparenza. Tuttavia, le icone di colori a 32 bit sono preferite.  
  
2.  Copiare il file dell'icona nella directory delle risorse nel progetto VSPackage. In Esplora soluzioni, aggiungere l'icona al progetto. (Selezionare le risorse e nel menu di scelta rapida fare clic su Aggiungi, quindi l'elemento esistente e selezionare il file di icona.)  
  
3.  Aprire il file con estensione vsct nell'editor.  
  
4.  Aggiungere un `GuidSymbol` elemento con un nome di **testIcon**. Creare un GUID (**strumenti / creare GUID**, quindi selezionare **il formato del Registro di sistema** e fare clic su copia) e incollarlo il `value` attributo. Il risultato dovrebbe essere simile al seguente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Aggiungere un `<IDSymbol>` per l'icona. Il `name` attributo è l'ID dell'icona e `value` indica la relativa posizione nell'elenco, se presente. Se è presente solo un'icona, aggiungere 1. Il risultato dovrebbe essere simile al seguente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Creare un `<Bitmap>` nel `<Bitmaps>` sezione del file vsct per rappresentare la bitmap contenente le icone.  
  
    -   Impostare il `guid` valore al nome del `<GuidSymbol>` elemento è stato creato nel passaggio precedente.  
  
    -   Impostare il `href` valore per il percorso relativo del file bitmap (in questo caso **risorse\\< nome file dell'icona\>**.  
  
    -   Impostare il `usedList` valore per il IDSymbol creato in precedenza. Questo attributo specifica un elenco delimitato da virgole delle icone da utilizzare nel pacchetto VSPackage. Le icone non presenti nell'elenco sono esclusi modulo compilazione.  
  
         Il blocco di Bitmap dovrebbe essere simile al seguente:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Esistente `<Button>` elemento, impostare il `Icon` elemento ai valori GUIDSymbol e IDSymbol creato in precedenza. Di seguito è riportato un esempio di un elemento Button con tali valori:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Verificare l'icona. Compilare il progetto e avviare il debug. Nell'istanza sperimentale, trovare il comando. Dovrebbe visualizzare l'icona che è stato aggiunto.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Riferimenti sullo schema XML VSCT](../extensibility/vsct-xml-schema-reference.md)