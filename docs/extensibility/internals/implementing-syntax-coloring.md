---
title: Implementazione di colorazione della sintassi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-syntax-coloring"></a>Implementazione di colorazione della sintassi
Quando il servizio di linguaggio fornisce la colorazione della sintassi, il parser converte una riga di testo in una matrice di colori e restituisce i tipi di token corrispondenti a questi elementi colorabili. Il parser deve restituire i tipi di token che appartengono a un elenco di colori. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Consente di visualizzare ogni elemento colorabile predefinito nella finestra del codice in base agli attributi assegnati dall'oggetto rappresentazione per il tipo di token appropriato.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non specifica un'interfaccia del parser, e l'implementazione del parser viene scelta dall'utente. Tuttavia, viene fornita un'implementazione di parser predefinita nel progetto di Visual Studio Language Pack. Per codice gestito, il framework di pacchetto gestito (MPF) fornisce supporto completo per la colorazione del testo.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul programma per implementare la colorazione della sintassi, vedere [procedura dettagliata: evidenziazione testo](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Passaggi seguiti da un Editor per colorare il testo  
  
1.  L'editor Ottiene la rappresentazione mediante una chiamata di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> oggetto.  
  
2.  Le chiamate di editor la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodo per determinare se la rappresentazione è necessario lo stato di ogni riga venga mantenuto di fuori di rappresentazione.  
  
3.  Se la rappresentazione richiede lo stato venga mantenuto di fuori di rappresentazione, l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodo per ottenere lo stato della prima riga.  
  
4.  Per ogni riga nel buffer, chiama l'editor di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo, che esegue i passaggi seguenti:  
  
    1.  La riga di testo viene passata a uno scanner per convertire il testo in token. Ogni token specifica il testo del token e il tipo di token.  
  
    2.  Il tipo di token viene convertito in un indice in un elenco di colori.  
  
    3.  Le informazioni del token viene utilizzate per compilare una matrice in modo che ogni elemento della matrice corrisponde a un carattere nella riga. I valori memorizzati nella matrice sono gli indici nell'elenco di colori.  
  
    4.  Viene restituito lo stato alla fine della riga per ogni riga.  
  
5.  Se la rappresentazione richiede lo stato venga mantenuto, l'editor memorizza nella cache lo stato per tale riga.  
  
6.  L'editor viene eseguito il rendering della riga di testo utilizzando le informazioni restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo. La procedura da adottare è la seguente:  
  
    1.  Per ogni carattere nella riga, ottenere l'indice dell'elemento colorabile.  
  
    2.  Se si utilizza gli elementi di colori predefiniti, accedere a elenco di colori dell'editor.  
  
    3.  In caso contrario, chiamare il servizio di linguaggio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo per ottenere un elemento colorabile.  
  
    4.  Usare le informazioni nell'elemento colorabile predefinito per il rendering del testo nella visualizzazione di.  
  
## <a name="managed-package-framework-colorizer"></a>Rappresentazione di Framework di pacchetto gestito  
 Il framework di pacchetto gestito (MPF) fornisce tutte le classi necessarie per implementare una rappresentazione. La classe di servizio di linguaggio deve ereditare la <xref:Microsoft.VisualStudio.Package.LanguageService> classe e implementare i metodi richiesti. È necessario fornire un scanner e parser implementando il <xref:Microsoft.VisualStudio.Package.IScanner> di interfaccia e restituire un'istanza di tale interfaccia dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo (uno dei metodi che devono essere implementati nel <xref:Microsoft.VisualStudio.Package.LanguageService> classe). Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: usare elementi di colori predefiniti](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementi di colori personalizzati](../../extensibility/internals/custom-colorable-items.md)   
 [Sviluppo di un servizio di linguaggio Legacy](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)