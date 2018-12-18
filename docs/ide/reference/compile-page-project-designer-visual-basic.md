---
title: Pagina Compilazione, Creazione progetti (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56efec5b538e2e84862549f6b5c7b7f30d9de75d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="compile-page-project-designer-visual-basic"></a>Compilazione (pagina), Creazione progetti (Visual Basic)
Usare la pagina **Compilazione** in Creazione progetti per specificare le istruzioni di compilazione. In questa pagina è anche possibile specificare opzioni del compilatore avanzate ed eventi di pre-compilazione o post-compilazione.  
  
Per accedere alla pagina **Compilazione**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Quindi scegliere **Progetto**, **Proprietà** sulla barra dei menu. Quando viene visualizzata la finestra Creazione progetti, fare clic sulla scheda **Compilazione**.  
  
[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="configuration-and-platform"></a>Configurazione e Piattaforma  
 Le impostazioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
> [!NOTE]
> Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Gli elenchi **Configurazione** e **Piattaforma** non vengono pertanto visualizzati.
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni sono **Debug** (impostazione predefinita), **Rilascio** o **Tutte le configurazioni**. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md) e [Procedura: creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md).
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare. È possibile specificare **Qualsiasi CPU** (impostazione predefinita), **x64** o **x86**.
  
## <a name="compiler-configuration-options"></a>Opzioni di configurazione del compilatore  
 Le impostazioni seguenti consentono di impostare le opzioni di configurazione del compilatore.  
  
 **Percorso dell'output di compilazione**  
 Specifica il percorso dei file di output per la configurazione del progetto. Digitare il percorso dell'output di compilazione in questa casella oppure fare clic sul pulsante **Sfoglia** per selezionare un percorso. Si noti che il percorso è relativo. Se si immette un percorso assoluto, sarà salvato come relativo. Il percorso predefinito è bin\Debug\ o bin\Release\\.
  
 Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Scegliendo il comando **Compila** dal menu **Debug** (F5) la compilazione verrà inserita nel percorso di debug indipendentemente dal **Percorso output** specificato. Il comando **Compila** del menu **Compila** la inserisce invece nel percorso specificato.
  
 **Option Explicit**  
 Specifica se consentire la dichiarazione implicita delle variabili. Selezionare **On** per richiedere la dichiarazione esplicita delle variabili. In questo modo il compilatore segnala errori se le variabili non vengono dichiarate prima dell'uso. Selezionare **Off** per consentire la dichiarazione implicita delle variabili.  
  
 Questa impostazione corrisponde all'opzione del compilatore [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 Se un file di codice sorgente contiene un'[istruzione Option Explicit](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), il valore `On` o `Off` nell'istruzione sostituisce l'impostazione di **Option Explicit** nella **pagina Compilazione**.  
  
 Quando si crea un progetto, l'impostazione **Option Explicit** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Explicit** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Explicit** in **Impostazioni predefinite di Visual Basic** è **On**.  
  
 L'impostazione di **Option Explicit** su `Off` non è in genere consigliabile. È possibile digitare un nome di variabile in modo errato in una o più posizioni e ciò può causare risultati imprevisti quando viene eseguito il programma.  
  
 **Option Strict**  
Specifica se applicare la semantica rigorosa per i tipi. Quando **Option Strict** è **On**, le condizioni seguenti causano un errore in fase di compilazione:  
  
-   Conversioni implicite verso un tipo di dati più piccolo  
  
-   Associazione tardiva  
  
-   Tipizzazione implicita che comporta un tipo `Object`  
  
Questi errori si verificano in presenza di una conversione implicita verso un tipo di dati più piccolo. Per altre informazioni, vedere [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) (Istruzione Open Strict), [Conversioni implicite ed esplicite](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) e [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions) (Conversioni verso un tipo di dati più grande e più piccolo).  
  
Un oggetto è ad associazione tardiva quando viene assegnato a una proprietà o a un metodo di una variabile dichiarata di tipo `Object`. Per altre informazioni, vedere [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) (Istruzione Option Strict) e [Associazione anticipata e tardiva](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding).  
  
Si verificano errori di tipo di oggetto implicito quando non è possibile dedurre un tipo appropriato per una variabile dichiarata, pertanto viene dedotto il tipo `Object`. Questo errore si verifica principalmente quando si usa un'istruzione `Dim` per dichiarare una variabile senza usare una clausola `As` e `Option Infer` è Off. Per altre informazioni, vedere [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) (Istruzione Option Strict), [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement) (Istruzione Open Infer) e [Visual Basic Language Specification](/dotnet/visual-basic/reference/language-specification) (Specifica del linguaggio Visual Basic).  
  
L'impostazione **Option Strict** corrisponde all'opzione del compilatore [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
Se un file di codice sorgente contiene un'[istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement), il valore `On` o `Off` nell'istruzione sostituisce l'impostazione di **Option Strict** nella **pagina Compilazione**.  
  
Quando si crea un progetto, l'impostazione **Option Strict** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Strict** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Strict** in **Impostazioni predefinite di Visual Basic** è **Off**.  
  
**Singoli avvisi di Option Strict.** La sezione **Configurazioni avvisi** della **pagina Compilazione** include impostazioni corrispondenti alle tre condizioni che causano un errore in fase di compilazione quando `Option Strict` è On. Queste impostazioni sono le seguenti:  
  
-   **Conversione implicita**  
  
-   **Binding tardivo. La chiamata potrebbe non riuscire in fase di esecuzione.**  
  
-   **Tipo implicito. Verrà utilizzato oggetto.**  
  
Quando si imposta **Option Strict** su **On**, tutte e tre queste impostazioni di configurazione degli avvisi vengono impostate su **Errore**. Quando si imposta **Option Strict** su **Off**, tutte e tre le impostazioni vengono impostate su **Nessuno**.  
  
È possibile modificare singolarmente ogni impostazione di configurazione degli avvisi su **Nessuno**, **Avviso** o **Errore**. Se tutte e tre le impostazioni di configurazione degli avvisi vengono impostate su **Errore**, nella casella `Option strict` viene visualizzato `On`. Se tutte e tre sono impostate su **Nessuno**, nella casella viene visualizzato `Off`. Per qualsiasi altra combinazione di queste impostazioni, viene visualizzato **(personalizzato)**.  
  
**Option Compare**  
Specifica il tipo di confronto di stringhe da usare. Selezionare **Binario** per indicare al compilatore di usare confronti di stringhe binari con distinzione tra maiuscole e minuscole. Selezionare **Testo** per usare confronti di stringhe di testo specifici delle impostazioni locali senza distinzione tra maiuscole e minuscole.  
  
Questa impostazione corrisponde all'opzione del compilatore [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
Se un file di codice sorgente contiene un'[istruzione Option Compare](/dotnet/visual-basic/language-reference/statements/option-compare-statement), il valore `Binary` o `Text` nell'istruzione sostituisce l'impostazione di **Option Compare** nella **pagina Compilazione**.  
  
Quando si crea un progetto, l'impostazione **Option Compare** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Compare** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Compare** in **Impostazioni predefinite di Visual Basic** è **Binario**.  
  
**Option Infer**  
Specifica se consentire l'inferenza del tipo di variabile locale nelle dichiarazioni di variabile. Selezionare **On** per consentire l'uso dell'inferenza del tipo di variabile locale. Selezionare **Off** per impedire l'inferenza del tipo di variabile locale.  
  
Questa impostazione corrisponde all'opzione del compilatore [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
Se un file di codice sorgente contiene un'[istruzione Option Infer](/dotnet/visual-basic/language-reference/statements/option-infer-statement), il valore `On` o `Off` nell'istruzione sostituisce l'impostazione di **Option Infer** nella **pagina Compilazione**.  
  
Quando si crea un progetto, l'impostazione **Option Infer** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Infer** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Infer** in **Impostazioni predefinite di Visual Basic** è **On**.  
  
**CPU di destinazione**  
Specifica il processore da impostare come destinazione del file di output. Specificare **x86** per qualsiasi processore compatibile con Intel a 32 bit, **x64** per qualsiasi processore compatibile con Intel a 64 bit, **ARM** per processori ARM oppure **Qualsiasi CPU** per specificare che qualsiasi processore è accettabile. **Qualsiasi CPU** è il valore predefinito per i nuovi progetti, in quanto consente all'applicazione di essere eseguita sul maggior numero di tipi di hardware.  
  
Per altre informazioni, vedere [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
**Preferisci 32 bit**  
Se la casella di controllo **Preferisci 32 bit** è selezionata, l'applicazione viene eseguita come applicazione a 32 bit sia nelle versioni di Windows a 32 bit sia in quelle a 64 bit. In caso contrario, l'applicazione viene eseguita come applicazione a 32 bit su versioni di Windows a 32 bit e come applicazione a 64 bit su versioni di Windows a 64 bit.  
  
L'esecuzione come applicazione a 64 bit raddoppia le dimensioni del puntatore e può causare problemi di compatibilità con le librerie che sono esclusivamente a 32 bit. È opportuno eseguire un'applicazione a 64 bit solo se viene eseguita con una velocità significativamente maggiore oppure se richiede più di 4 GB di memoria.  
  
Questa casella di controllo è disponibile solo se tutte le condizioni seguenti sono true:  
  
-   Nella **pagina Compilazione** l'elenco **CPU destinazione** è impostato su **Qualsiasi CPU**.  
  
-   Nella **pagina Applicazione** l'elenco **Tipo di applicazione** specifica che il progetto è un'applicazione.  
  
-   Nella **pagina Applicazione** l'elenco **Framework di destinazione** specifica .NET Framework 4.5.  
  
**Configurazioni avvisi**  
La tabella seguente elenca le condizioni di compilazione e il livello di notifica corrispondente **Nessuno**, **Avviso** o **Errore** per ognuna.  
  
Per impostazione predefinita, tutti gli avvisi del compilatore vengono aggiunti all'Elenco attività durante la compilazione. Selezionare **Disabilita tutti gli avvisi** per indicare al compilatore di non generare avvisi o errori. Selezionare **Considera tutti gli avvisi come errori** se si vuole che il compilatore consideri gli avvisi come errori che devono essere corretti.  
  
**Disabilita tutti gli avvisi**  
Specifica se consentire al compilatore di generare notifiche come specificato nella tabella **Condizione e notifica** descritta in precedenza in questo documento. Per impostazione predefinita, questa casella di controllo è deselezionata. Selezionare questa casella di controllo per indicare al compilatore di non generare avvisi o errori.  
  
Questa impostazione corrisponde all'opzione del compilatore [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
**Considera tutti gli avvisi come errori**  
Specifica come considerare gli avvisi. Per impostazione predefinita, questa casella di controllo è deselezionata, in modo che tutte le notifiche di avviso rimangano impostate su **Avviso**. Selezionare questa casella di controllo per impostare tutte le notifiche di avviso su **Errore**.  
  
Questa opzione è disponibile solo se **Disabilita tutti gli avvisi** è deselezionata.  
  
**Genera il file di documentazione XML**  
Specifica se generare le informazioni di documentazione. Per impostazione predefinita, questa casella di controllo è selezionata, per indicare al compilatore di generare informazioni di documentazione e includerle in un file XML. Deselezionare questa casella di controllo per indicare al compilatore di non creare la documentazione.  
  
Questa impostazione corrisponde all'opzione del compilatore [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).  
  
**Registra per interoperabilità COM**  
Specifica se l'applicazione gestita esporrà un oggetto COM (COM Callable Wrapper) che consente a un oggetto COM di interagire con l'applicazione.  
  
Per impostazione predefinita, questa casella di controllo è deselezionata, a indicare che l'applicazione non consentirà l'interoperabilità COM. Selezionare questa casella di controllo per consentire l'interoperabilità COM.  
  
Questa opzione non è disponibile per i progetti Applicazione Windows o Applicazione console.  
  
**Eventi di compilazione**  
Fare clic su questo pulsante per accedere alla finestra di dialogo **Eventi di compilazione**. Usare questa finestra di dialogo per specificare le istruzioni di configurazione pre-compilazione e post-compilazione per il progetto. Questa finestra di dialogo si applica esclusivamente ai progetti Visual Basic. Per altre informazioni, vedere [Finestra di dialogo Eventi di compilazione (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
**Opzioni di compilazione avanzate**  
Fare clic su questo pulsante per accedere alla finestra di dialogo **Impostazioni del compilatore avanzate**. Usare la finestra di dialogo **Impostazioni del compilatore avanzate** per specificare le proprietà avanzate di configurazione della compilazione per un progetto. Questa finestra di dialogo si applica esclusivamente ai progetti Visual Basic. Per altre informazioni, vedere [Finestra di dialogo Impostazioni del compilatore avanzate (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  

## <a name="see-also"></a>Vedere anche

[Procedura: Specificare gli eventi di compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)  
[Compilatore della riga di comando di Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)  
[Procedura: Creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)