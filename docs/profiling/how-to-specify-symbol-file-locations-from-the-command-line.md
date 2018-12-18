---
title: 'Procedura: Specificare percorsi dei file di simboli dalla riga di comando | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 319d828991cff85987108cc193498b14438e5c62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Procedura: specificare percorsi dei file di simboli tramite la riga di comando
Per visualizzare informazioni sui simboli quali i nomi delle funzioni e i numeri di riga, lo strumento da riga di comando VSPerfReport richiede l'accesso ai file di simboli (con estensione pdb) dei componenti profilati e ai file di sistema di Windows. I file di simboli vengono creati quando viene compilato un componente. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport esegue automaticamente la ricerca dei file di simboli nei percorsi seguenti:  
  
-   Percorsi specificati nell'opzione **/SymbolPath** o nella variabile di ambiente **_NT_SYMBOL_PATH**.  
  
-   Percorso locale esatto in cui è stato compilato un componente.  
  
-   Directory contenente il file di dati di profilatura (con estensione vsp o vsps).  
  
 Microsoft fornisce i file con estensione pdb per molti dei suoi prodotti online in un server di simboli. Se il computer usato per la generazione di rapporti è connesso a Internet, VSPerfReport si connette al server di simboli online per cercare automaticamente informazioni sui simboli e salvare i file in un archivio locale.  
  
 È possibile specificare il percorso del file di simboli e l'archivio del server di simboli Microsoft nei modi seguenti:  
  
-   Impostare la variabile di ambiente **_NT_SYMBOL_PATH**.  
  
-   Aggiungere l'opzione **/SymbolPath** alla riga di comando VSPerfReport.  
  
 È anche possibile usare entrambi questi metodi.  
  
> [!NOTE]
>  Se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è installato nel computer locale, probabilmente è già stato specificato un percorso per i file di simboli Windows. Per altre informazioni, vedere [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md). È comunque necessario configurare VSPerfReport per usare il percorso e il server come descritto più avanti in questo argomento.  
  
## <a name="specifying-windows-symbol-files"></a>Specifica di file di simboli Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Per configurare l'uso del server di simboli Windows  
  
1.  Se necessario, creare una directory per archiviare localmente i file di simboli.  
  
2.  Usare la sintassi seguente per impostare la variabile di ambiente **_NT_SYMBOL_PATH** o l'opzione /SymbolPath di VSPerfReport:  
  
     **srv\*** *ArchivioLocale* **\*http://msdl.microsoft.com/downloads/symbols**  
  
     dove *ArchivioLocale* è il percorso della directory locale creata.  
  
## <a name="specifying-component-symbol-files"></a>Specifica di file di simboli dei componenti  
 Gli strumenti di profilatura eseguono la ricerca di file con estensione pdb dei componenti da profilare nei rispettivi percorsi originali archiviati nei componenti o nella cartella contenente il file di dati di profilatura. È possibile specificare altri percorsi per la ricerca aggiungendo uno o più percorsi a **_NT_SYMBOL_PATH** o all'opzione **/SymbolPath**. Separare i percorsi con punti e virgola.  
  
## <a name="example"></a>Esempio  
 La riga di comando seguente imposta la variabile di ambiente **_NT_SYMBOL_PATH** sul server di simboli Windows e la directory locale su **C:\Symbols**.  
  
 **set  _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 La riga di comando VSPerfReport seguente aggiunge la directory C:\Projects\Symbols al percorso di ricerca tramite l'opzione **/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**