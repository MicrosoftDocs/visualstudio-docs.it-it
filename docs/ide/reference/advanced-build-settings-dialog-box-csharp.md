---
title: Finestra di dialogo Impostazioni di compilazione avanzate (C#)
ms.date: 06/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cf4fd5b48dc3bfcfbfe1809eebe656a5b8f2079d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928282"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Finestra di dialogo Impostazioni di compilazione avanzate (C#)

Per specificare le proprietà di configurazione avanzate della build del progetto, usare la finestra di dialogo **Impostazioni di compilazione avanzate** di **Progettazione progetti**. Questa finestra di dialogo è applicabile solo ai progetti [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].

## <a name="general"></a>Generale

Le opzioni seguenti consentono di configurare le impostazioni avanzate generali.

**Versione linguaggio**

Specifica la versione del linguaggio da usare. Il set di funzionalità varia a seconda della versione. Questa opzione può quindi essere usata per forzare il compilatore ad attivare solo un sottoinsieme delle funzionalità implementate oppure solo le funzionalità compatibili con uno standard esistente. Le opzioni di questa impostazione sono le seguenti:

- **default**

   Fa riferimento alla versione corrente.

- **ISO-1** e **ISO-2**

   Fa rispettivamente riferimento alle funzionalità standard ISO-1 e ISO-2.

- **C# [numero versione]**

   Fa riferimento a una versione specifica di C#. Per altre informazioni, vedere [/langversion (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).

**Segnalazione errori interni del compilatore**

Specifica se gli errori del compilatore devono essere segnalati a Microsoft. Se l'opzione è impostata su **prompt**, al verificarsi di un errore del compilatore interno sarà chiesto se si vuole inviare elettronicamente a Microsoft una segnalazione errori. Se è impostata su **send**, sarà inviata automaticamente una segnalazione errori. Se è impostata su **queue**, le segnalazioni errori saranno accodate. Se è impostata su **none**, l'errore sarà segnalato soltanto nell'output di testo del compilatore. Per altre informazioni, vedere [/errorreport (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Controlla overflow/underflow aritmetico**

Specifica se un'istruzione aritmetica intera non inclusa nell'ambito della parola chiave [checked](/dotnet/csharp/language-reference/keywords/checked) o [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) e che restituisce un valore al di fuori dell'intervallo del tipo di dati causerà un'eccezione in fase di esecuzione. Per altre informazioni, vedere [/checked (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Ometti riferimenti a mscorlib.dll**

Specifica se nel programma verrà importato il file mscorlib.dll per l'intero spazio dei nomi <xref:System>. Selezionare questa casella se si vuole definire o creare lo spazio dei nomi <xref:System> e gli oggetti personalizzati. Per altre informazioni, vedere [/nostdlib (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Output

Le opzioni seguenti consentono di specificare impostazioni di output avanzate.

**Informazione di debug**

Specifica il tipo di informazioni di debug generate dal compilatore. Per informazioni su come configurare le prestazioni di debug di un'applicazione, vedere [Semplificazione del debug di un'immagine](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Le opzioni di questa impostazione sono le seguenti:

- **none**

   Specifica che non saranno generate informazioni di debug.

- **full**

   Consente di associare un debugger al programma in esecuzione.

- **pdbonly**

   Consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma l'assembler viene visualizzato solo se il programma in esecuzione è associato al debugger.

-  **portatile**

   Crea un file con estensione pdb, vale a dire un file di simboli di tipo PE non specifico per la piattaforma che offre altri strumenti, soprattutto debugger, informazioni su cosa contiene il file eseguibile principale e come è stato generato. Vedere [Portable PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (PDB portatile) per altre informazioni.

- **incorporata**

   Incorpora informazioni sui simboli di tipo PE nell'assembly. Non vengono generati file con estensione pdb esterni.

Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Allineamento file**

Specifica le dimensioni delle sezioni nel file di output. I valori validi sono **512**, **1024**, **2048**, **4096** e **8192**. Questi valori sono misurati in byte. Ogni sezione sarà allineata in base a un limite multiplo di questo valore, determinando così le dimensioni del file di output. Per altre informazioni, vedere [/filealign (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Indirizzo di base DLL**

Specifica l'indirizzo di base preferenziale in cui caricare una DLL. L'indirizzo di base predefinito per una DLL viene impostato dal Common Language Runtime [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]. Per altre informazioni, vedere [/baseaddress (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md)