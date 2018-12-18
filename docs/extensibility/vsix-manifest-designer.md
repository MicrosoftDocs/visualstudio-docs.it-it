---
title: Progettazione del manifesto VSIX | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b90f8acd95d913e563ff167e21b743cbffec2ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-manifest-designer"></a>Progettazione del manifesto VSIX
Modifica un file manifesto di pacchetto VSIX, che imposta il comportamento di installazione per un'estensione di Visual Studio.  
  
 Il **progettazione del manifesto VSIX** esegue il mapping allo schema VSIX sottostante. Ogni elemento nello schema può essere impostato utilizzando un controllo corrispondente nella finestra di progettazione. Per ulteriori informazioni sullo schema, vedere [riferimento 2.0 allo Schema di estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Per aprire il **progettazione del manifesto VSIX**, individuare un file vsixmanifest in **Esplora**, quindi aprire il file. Se il file non contiene codice XML valido, non si aprirà la finestra di progettazione del manifesto.  
  
> [!NOTE]
>  Quando il pacchetto viene compilato, vsixmanifest è output Extension. vsixmanifest.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 Il **progettazione del manifesto VSIX** contiene quattro sezioni che corrispondono a questi elementi di primo livello dello schema:  
  
-   Metadati  
  
-   Installare le destinazioni  
  
-   Risorse  
  
-   Dipendenze  
  
 L'area di intestazione contiene i controlli seguenti.  
  
 **Nome del prodotto**  
 Descrive il nome dell'estensione.  
  
 **ID prodotto**  
 Specifica le informazioni di identificazione univoco per il pacchetto.  
  
 **Autore**  
 Specifica il nome dell'autore dell'estensione.  
  
 **Version**  
 Specifica il numero di versione dell'estensione.  
  
 Il **metadati** scheda contiene i controlli seguenti.  
  
 **Descrizione**  
 Fornisce la descrizione testuale dell'estensione, da visualizzare **Extension Manager**.  
  
 **Lingua**  
 Specifica la lingua predefinita per il pacchetto, che corrisponde ai dati testuali nel manifesto. Il `Language` attributo segue la convenzione di codice delle impostazioni locali di common language runtime (CLR) per gli assembly di risorse, ad esempio en-us, en, fr-fr. Per impostazione predefinita, il valore è indipendente dal; Ciò significa che il pacchetto verrà eseguito in qualsiasi versione di lingua di Visual Studio.  
  
 **Licenza**  
 Specifica il file di testo che contiene la licenza dell'utente, se presente.  
  
 **Icona**  
 Specifica il file di grafica (con estensione png, bmp, JPEG, con estensione ico) che contiene l'icona da visualizzare **Gestione estensioni**, se è presente un'icona. L'immagine dell'icona deve essere 32 x 32 pixel o viene ridimensionata a queste dimensioni. Se viene specificata alcuna icona, **Extension Manager** utilizza un'icona predefinita.  
  
 **Immagine di anteprima**  
 Specifica il file di grafica (con estensione png, bmp, JPEG, con estensione ico) che contiene l'immagine di anteprima da visualizzare **Gestione estensioni**, se è presente un'immagine di anteprima. L'immagine di anteprima deve essere di 200 x 200 pixel. Se viene specificata alcuna immagine di anteprima, **Extension Manager** utilizza un'immagine predefinita.  
  
 **Tag**  
 Aggiunge il tag di testo da utilizzare per i suggerimenti di ricerca.  
  
 **Note sulla versione**  
 Specifica un file (con estensione txt,. RTF) che contiene le note sulla versione. Accetta anche l'URL di un sito Web che consente di visualizzare le note sulla versione.  
  
 **Guida introduttiva**  
 Specifica un file (con estensione txt,. RTF) che contiene informazioni sull'utilizzo dell'estensione o il contenuto nel pacchetto VSIX. Questa guida viene visualizzata quando l'installazione dell'estensione è stata completata. Accetta anche l'URL di un sito Web che consente di visualizzare la Guida.  
  
 **Ulteriori informazioni sull'URL**  
 Specifica l'URL di un sito Web che contiene informazioni aggiuntive sul prodotto.  
  
 Il **destinazioni di installazione** scheda contiene i controlli seguenti.  
  
 **Tipo di installazione**  
 Elenca **Visual Studio Extension** e **SDK di estensione** come tipi di installazione di destinazione. Le opzioni variano a seconda del tipo desiderato.  
  
 **Estensione di Visual Studio**  
 Elenca il **la destinazione di installazione** gli elementi che descrivono come il pacchetto può essere installato e in quali prodotti Visual Studio è possibile installare questa estensione. Ogni prodotto viene identificato separatamente dal nome e una versione o intervallo.  Prodotti possono essere aggiunto all'elenco, modificati ed eliminati. Il nome e la versione di un prodotto corrispondono al **Id** e **versione** gli attributi dell'oggetto associato **la destinazione di installazione** elemento.  
  
 **Intervallo di versioni** è [12.0, 14,0] e Usa la notazione seguente:  
  
-   [-versione minima inclusiva  
  
-   ]-versione massima inclusiva  
  
-   (-versione minima esclusiva  
  
-   )-versione massima esclusiva  
  
-   Versione unica # - solo la versione specificata  
  
 **SDK di estensione**  
 Specifica un'installazione globale non è nell'ambito di un prodotto specifico e una versione. **Identificatore di piattaforma di destinazione** è la piattaforma, ad esempio "Windows", che di destinazione. **Versione della piattaforma di destinazione** è la versione, ad esempio 8.0, la piattaforma di destinazione. **Nome del SDK** e **SDK versione** sono rispettivamente il nome e il numero di versione di SDK.  
  
 **Questo VSIX è installato per tutti gli utenti (richiede l'elevazione all'installazione)** casella di controllo  
 Se questa casella di controllo è selezionata, questa estensione è installata per tutti gli utenti. in caso contrario, viene installata solo per l'utente corrente.  
  
 **Questo VSIX è installato Windows Installer** casella di controllo  
 Se questa casella di controllo è selezionata, questa estensione viene installata da Windows Installer (file con estensione msi). in caso contrario, viene installato come un pacchetto VSIX tipico (file con estensione VSIX).  
  
 Il **asset** scheda contiene i controlli seguenti.  
  
 **Elenco degli asset**  
 Elenca gli elementi di Asset che descrivono gli elementi di estensione o il contenuto da questo pacchetto superfici. Ogni estensione o un elemento di contenuto è elencato separatamente dall'origine, tipo e percorso. Gli elementi di estensioni e il contenuto possono essere aggiunto all'elenco, modificati ed eliminati. Il tipo e il percorso di un elemento di estensione o il contenuto corrispondente per il `Type` e `Path` gli attributi dell'oggetto associato `Asset` elemento. I seguenti tipi sono noti:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Per aggiungere o modificare una risorsa, è necessario specificare il tipo di risorsa, se la risorsa è un progetto nella soluzione corrente o un file nel file system e il nome del progetto. È inoltre possibile specificare il nome della cartella in cui deve essere incorporato.  
  
 È anche possibile creare tipi personalizzati e assegnare loro nomi univoci.  
  
 Il **dipendenze** scheda contiene i controlli seguenti.  
  
 **Nome di origine e intervallo di versioni**  
 Elenca gli elementi di dipendenza di questo pacchetto, che sono altri pacchetti che dipende da questo pacchetto. Se viene specificato un pacchetto di dipendenze, deve essere installato prima di questo pacchetto è installato; in caso contrario, il pacchetto deve essere installata.  
  
 I pacchetti di dipendenza vengono specificati dall'identificatore, nome, l'intervallo di versioni, origine e come la dipendenza deve essere risolto. Ogni pacchetto di dipendenza è elencato separatamente per nome, versione e di origine. I pacchetti di dipendenza possono essere aggiunto all'elenco, modificati ed eliminati.  
  
 L'identificatore deve corrispondere il `ID` attributo dei metadati del pacchetto di dipendenza. L'origine può essere un progetto nella soluzione corrente, un'estensione attualmente installata o un file. Il **è come dipendenza viene risolta** impostazione può essere il percorso relativo di un pacchetto nidificato o l'URL del percorso di download per la dipendenza. L'ID, la versione e la risoluzione del pacchetto dipendenza corrispondono al `Id`, `Version`, e `Location` gli attributi dell'oggetto associato `Dependency` elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento di Schema 2.0 estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)