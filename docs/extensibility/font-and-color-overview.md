---
title: Tipo di carattere e colore Panoramica | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8185d5c931ccf0b3b15fba10405cf050eb7c6241
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="font-and-color-overview"></a>Panoramica di colore e tipo di carattere
Questo argomento vengono illustrate le impostazioni di carattere e colori testo nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Inoltre, introduce i concetti di categorie e di elementi visualizzati e viene descritto l'utilizzo degli attributi del testo VSPackage e l'editor di componenti di base.  
  
## <a name="the-fonts-and-colors-property-page"></a>Tipi di carattere e colori pagina delle proprietà  
 È possibile gestire gli attributi del testo visualizzato nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) tramite il **tipi di carattere e colori** pagina delle proprietà. Per trovare il **tipi di carattere e colori** nella pagina proprietà di **strumenti** menu, fare clic su **opzioni**. Espandere **ambiente**, quindi fare clic su **tipi di carattere e colori**.  
  
## <a name="categories-and-display-items"></a>Le categorie e elementi visualizzati  
 Tipi di carattere e colori sono organizzati in **categorie** e **elementi visualizzati**.  
  
-   Oggetto **categoria** è un contenitore logico o funzionale per un numero di **elementi visualizzati**.  
  
     Un elenco di **categorie** è il **Mostra impostazioni per** casella di riepilogo a discesa del **tipi di carattere e colori** pagina delle proprietà.  
  
-   Oggetto **elemento visualizzato** è un'entità testo ben definiti, ad esempio un commento, una stringa o una struttura di controllo che deve essere colorati quando visualizzata.  
  
 Ogni **elemento visualizzato** è definito in modo univoco all'interno di **categoria** che lo contiene. Di conseguenza, più di un **categoria** può avere un **elemento visualizzato** con lo stesso nome.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Controllo VSPackage di tipi di carattere e colori  
 Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] consente di VSPackage in:  
  
-   Definire i tipi di carattere e colore **categorie**.  
  
-   Specificare i tipi di carattere e colori utilizzati per presentare **elementi visualizzati**.  
  
-   Interagire con il **tipi di carattere e colori** pagina delle proprietà.  
  
-   Aggregazione più **categorie** in gruppi.  
  
-   Mantenere le modifiche apportate nelle impostazioni predefinite.  
  
 Esistono due modi per interagire con tipo di carattere e colore selezioni all'interno di [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Una delle modalità è detta *colorazione della sintassi*. Viene utilizzato da un VSPackage che consente di personalizzare esistente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor per implementare un servizio di linguaggio e creare un'origine dell'editor.  
  
     Un solo **categoria** supporta questo meccanismo, vale a dire, il **Editor di testo**.  
  
-   Un'alternativa più generale supporta tutti gli altri **categorie** e i componenti dell'interfaccia utente diverso dall'editor di origine per la visualizzazione di testo. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Impostazioni di testo dell'Editor di componenti di base  
 Impostazioni di carattere e colori per l'editor di componenti di base di un oggetto servizio di linguaggio vengono gestite con il **testo EditorCategory** trovato nel **Mostra impostazioni per** casella di riepilogo a discesa del **tipi di carattere e colori** pagina delle proprietà.  
  
 Quando si lavora con gli editor, è necessario utilizzare il carattere specializzato e il meccanismo di controllo di colore che fornisce il servizio di linguaggio per controllare ed estendere il **Editor di testo** impostazioni. Il meccanismo è detto *la colorazione della sintassi* e fornisce:  
  
-   Una tecnica semplificata per la gestione di carattere e colori degli elementi visualizzati.  
  
     Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un meccanismo di colorazione ben definiti e ottimizzata.  
  
     Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   La possibilità di entrambi utilizzano gli oggetti visualizzazione incorporate il **EditorCategory testo** e per consentire l'uso.  
  
     Per ulteriori informazioni, vedere [come: elementi colorabile predefinito utilizzare](../extensibility/internals/how-to-use-built-in-colorable-items.md) e [personalizzate colorabile](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistenza automatico dell'oggetto corrente dello stato di entrambi predefinite e personalizzate visualizzare gli elementi con il **Editor di testo** categoria.  
  
 Per ulteriori informazioni sulla sintassi, vedere colorazione [colorazione della sintassi in un servizio di linguaggio Legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce legacy nell'Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)