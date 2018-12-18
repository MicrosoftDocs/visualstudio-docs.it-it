---
title: Pagina Compilazione, Creazione progetti (C#) | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4572975b534d240cfd535f7d70f57fd958ff218d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="build-page-project-designer-c"></a>Pagina Compilazione, Progettazione progetti (C#)
Usare la pagina **Compilazione** di **Creazione progetti** per specificare le proprietà di configurazione della compilazione del progetto. Questa pagina è applicabile solo ai progetti [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  

Per accedere alla pagina **Compilazione**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Scegliere **Visualizza**, **Pagine delle proprietà** dal menu. Quando si apre Progettazione progetti, scegliere la scheda **Compila**.  

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  

## <a name="configuration-and-platform"></a>Configurazione e Piattaforma  
Le opzioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  

> [!NOTE]
> Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Queste opzioni non sono di conseguenza visualizzate. Per altre informazioni, vedere [Procedura: Impostare le configurazioni di debug e rilascio](/debugger/how-to-set-debug-and-release-configurations.md).

**Configurazione**  
Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni possono essere **Attiva (Debug)** (il valore predefinito), **Debug**, **Release** o **Tutte le configurazioni**.  

**Piattaforma**  
Specifica le impostazioni della piattaforma da visualizzare o modificare. L'impostazione predefinita è **Active (Any CPU)** (Attiva (qualsiasi CPU)). È possibile modificare la piattaforma attiva tramite **Gestione configurazione**. Per altre informazioni, vedere [How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md) (Procedura: Creare e modificare le configurazioni).  

## <a name="general"></a>Generale  
Le opzioni seguenti consentono di configurare diverse impostazioni del compilatore C#.  

**Simboli di compilazione condizionale**  
Specifica i simboli su cui eseguire la compilazione condizionale. Separare i simboli con un punto e virgola (";"). Per altre informazioni, vedere [/define (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).  

**Definisci costante DEBUG**  
Definisce DEBUG come simbolo in tutti i file di codice sorgente dell'app. Selezionare questa opzione equivale a usare l'opzione della riga di comando `/define:DEBUG`.  

**Definisci costante TRACE**  
Definisce TRACE come simbolo in tutti i file di codice sorgente dell'app. Selezionare questa opzione equivale a usare l'opzione della riga di comando `/define:TRACE`.  

**Piattaforma di destinazione**  
Specifica il processore da impostare come destinazione del file di output. Scegliere **x86** per qualsiasi processore compatibile con Intel a 32 bit, scegliere **x64** per qualsiasi processore compatibile con Intel a 64 bit, scegliere **ARM** per processori ARM oppure scegliere **Any CPU** (Qualsiasi CPU) per specificare che qualsiasi processore è accettabile. **Any CPU** (Qualsiasi CPU) è il valore predefinito per i progetti, in quanto consente all'applicazione di essere eseguita su una vasta gamma di hardware.  

Per altre informazioni, vedere [/platform (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).  

**Preferisci 32 bit**  
Se la casella di controllo **Preferisci 32 bit** è selezionata, l'applicazione viene eseguita come applicazione a 32 bit sia nelle versioni di Windows a 32 bit sia in quelle a 64 bit. Se la casella di controllo non è selezionata, l'applicazione viene eseguita come applicazione a 32 bit nelle versioni di Windows a 32 bit e come applicazione a 64 bit nelle versioni a 64 bit di Windows.  

Se un'applicazione viene eseguita come applicazione a 64 bit, le dimensioni del puntatore raddoppiano e si possono verificare problemi di compatibilità con altre librerie che sono esclusivamente a 32 bit. È utile eseguire un'applicazione a 64 bit solo se sono necessari più di 4 GB di memoria o se le istruzioni a 64 bit garantiscono un miglioramento significativo delle prestazioni.  

Questa casella di controllo è disponibile solo se tutte le condizioni seguenti sono true:  

-   Nella **pagina Compilazione** l'elenco **Piattaforma di destinazione** è impostato su **Any CPU** (Qualsiasi CPU).  

-   Nella **pagina Applicazione** l'elenco **Tipo di Output** specifica che il progetto è un'applicazione.  

-   Nella **pagina Applicazione** l'elenco **Framework di destinazione** specifica .NET Framework 4.5.  


**Consenti codice unsafe**  
Consente la compilazione del codice che usa la parola chiave [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Per altre informazioni, vedere [/unsafe (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).  

**Ottimizza codice**  
Abilita o disabilita le ottimizzazioni eseguite dal compilatore per ridurre le dimensioni del file di output e aumentarne la velocità e l'efficienza. Per altre informazioni, vedere [/optimize (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).  

## <a name="errors-and-warnings"></a>Errori e avvisi  
Le impostazioni riportate di seguito sono usate per configurare le opzioni di errori e avvisi del processo di compilazione.  

**Livello avvisi**  
Specifica il livello da visualizzare per gli avvisi del compilatore. Per altre informazioni, vedere [/warn (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).  

**Non visualizzare avvisi**  
Blocca la capacità del compilatore di generare uno o più avvisi. Separare più numeri di avvisi tramite virgola o punto e virgola. Per altre informazioni, vedere [/nowarn (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).  

## <a name="treat-warnings-as-errors"></a>Considera gli avvisi come errori  
Le impostazioni riportate di seguito sono usate per specificare quali avvisi considerare come errori. Selezionare una delle opzioni seguenti per indicare in quali condizioni restituire un errore se la compilazione rileva un avviso. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).  

**None**  
Non considera gli avvisi come errori.  

**Avvisi specifici**  
Considera gli avvisi specificati come errori. Separare più numeri di avvisi tramite virgola o punto e virgola.  

**All**  
Considera tutti gli avvisi come errori.  

## <a name="output"></a>Output  
Le impostazioni riportate di seguito sono usate per configurare le opzioni di output del processo di compilazione.  

**Percorso output**  
Specifica il percorso dei file di output per la configurazione del progetto. Immettere il percorso dell'output di compilazione in questa casella, oppure scegliere il pulsante **Sfoglia** per specificare un percorso. Si noti che il percorso è relativo. Se si immette un percorso assoluto, sarà salvato come relativo. Il percorso predefinito è bin\Debug o bin\Release\\.

Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Scegliendo il comando **Compila** dal menu **Debug** (F5) la compilazione verrà inserita nel percorso di debug indipendentemente dal **Percorso output** specificato. Il comando **Compila** del menu **Compila** la inserisce invece nel percorso specificato. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).

**File di documentazione XML**  
Specifica il nome di un file in cui saranno elaborati i commenti relativi alla documentazione. Per altre informazioni, vedere [/doc (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).  

**Registra per interoperabilità COM**  
Indica che l'applicazione gestita esporrà un oggetto COM (COM Callable Wrapper) che consentirà a un oggetto COM di interagire con l'applicazione gestita. La proprietà **Tipo di output** nella [pagina Applicazione](../../ide/reference/application-page-project-designer-visual-basic.md) di **Creazione progetti** dell'applicazione deve essere impostata su **Libreria di classi** per rendere disponibile la proprietà **Registra per interoperabilità COM**. Per una classe di esempio che è possibile includere nell'applicazione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ed esporre come oggetto COM, vedere [Example COM Class](/dotnet/csharp/programming-guide/interop/example-com-class) (Esempio di classe COM).  

**Genera assembly di serializzazione**  
Specifica se il compilatore userà lo strumento per la generazione di serializzatori XML (Sgen.exe) per creare assembly di serializzazione XML. Gli assembly di serializzazione possono migliorare le prestazioni di avvio della classe <xref:System.Xml.Serialization.XmlSerializer>, se è stata usata per serializzare i tipi nel codice. Per impostazione predefinita, questa opzione è impostata su **Auto**. Specifica quindi che saranno generati assembly di serializzazione solo se è stata usata la classe <xref:System.Xml.Serialization.XmlSerializer> per codificare i tipi nel codice in XML. **Off** specifica che non saranno mai generati assembly di serializzazione, indipendentemente dal fatto che il codice usi o meno la classe <xref:System.Xml.Serialization.XmlSerializer>. **On** specifica che saranno sempre generati assembly di serializzazione. Gli assembly di serializzazione sono denominati `TypeName`.XmlSerializers.dll. Per altre informazioni, vedere [Strumento per la generazione di serializzatori XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).  

**Avanzate**  
Selezionare il collegamento per informazioni sulla finestra di dialogo [Impostazioni di compilazione avanzate (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md).  

## <a name="see-also"></a>Vedere anche  
[Project Properties Reference](../../ide/reference/project-properties-reference.md)  (Riferimenti alle proprietà di progetto)  
[Opzioni del compilatore C#](/dotnet/csharp/language-reference/compiler-options/index)
