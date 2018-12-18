---
title: Recupero di tipo di carattere e colore per testo colorazione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c86e37d6d7da9da0a6b0978770bf7d7564fa19c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Recupero di tipo di carattere e colore per testo colorazione
Il processo che esegue il rendering o Visualizza colorato testo negli elementi dell'interfaccia utente dipende dal tipo di progetto, la tecnologia e developer di preferenze. Il **tipi di carattere e colori** pagina delle proprietà vengono archiviate le impostazioni.

 La maggior parte delle implementazioni che visualizzano testo colorato necessario il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> e associate le interfacce per le impostazioni di visualizzazione di presentazione, il recupero e l'archiviazione di testo.

> [!NOTE]
>  Quando si personalizza l'editor dei componenti di base (che supporta il **EditorCategory testo**), è consigliabile utilizzare la tecnologia di colorazione della sintassi nel servizio di linguaggio. Per ulteriori informazioni, vedere [tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md).

## <a name="getting-default-font-and-color-information"></a>Recupero di informazioni di colore e tipo di carattere predefinito
 Tutti i **tipi di carattere e colori** le impostazioni di qualsiasi finestra di visualizzazione di testo devono essere specificate nel **elementi visualizzati** di uno **categoria**. Per ulteriori informazioni, vedere [tipi di carattere e colori, ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Per colorare, un pacchetto VSPackage deve ottenere corrente **tipi di carattere e colori** impostazioni. Un pacchetto VSPackage può ottenere le impostazioni correnti nei modi seguenti, a seconda delle esigenze:

-   Utilizzare il meccanismo di persistenza di carattere e colori per recuperare lo stato corrente o archiviato. Per ulteriori informazioni, vedere [accesso archiviati tipo di carattere e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md).

-   Usare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia di un servizio che fornisce i dati di carattere e colori per ottenere un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, se il pacchetto VSPackage non sia anche il provider di carattere e colori.

-   Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Per garantire che i risultati ottenuti tramite polling sono aggiornate, potrebbe essere utile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se è necessario eseguire un aggiornamento prima di chiamare i metodi di recupero del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.

Dopo l'acquisizione di informazioni di carattere e colori, analizzare il testo da visualizzare per identificare gli elementi che richiedono colorazione. Visualizzare il testo della finestra utilizzando i tipi di carattere appropriati e i colori.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Uso di tipi di carattere e testo](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Utilizzo dei colori](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (interfaccia graphics device)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)