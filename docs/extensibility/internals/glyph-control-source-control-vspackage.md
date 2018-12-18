---
title: Icona controllo (origine controllo VSPackage) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e41fc2a7d09f50d70caca939e3fdd691b1d05c9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="glyph-control-source-control-vspackage"></a>Icona controllo (origine controllo VSPackage)
Parte dell'integrazione completa disponibile per i pacchetti VSPackage di controllo del codice sorgente è la possibilità di visualizzare le proprie icone per indicare lo stato degli elementi nel controllo del codice sorgente.  
  
## <a name="levels-of-glyph-control"></a>Livelli di controllo del glifo  
 Un'icona di stato è un'icona che indica lo stato corrente di un elemento quando è visualizzato, ad esempio in **Esplora** o in **Visualizzazione classi**. Un controllo del codice sorgente VSPackage può esercitare due livelli di controllo del glifo. È possibile limitare il numero di icone da un set predefinito di glifi fornito dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE oppure è possibile definire un set personalizzato di glifi da visualizzare.  
  
### <a name="default-set-of-glyphs"></a>Set predefinito di icone  
 Per determinare le icone di stato che sono associate a un elemento **Esplora**, un progetto richiede l'icona di stato dal controllo di origine utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Un controllo del codice sorgente VSPackage può decidere di mantenere la scelta di glifi limitato ai glifi predefiniti forniti dall'IDE. In questo caso, il pacchetto VSPackage nuovamente passa una matrice di valori che rappresentano le enumerazioni glifo definiti in vsshell.idl. Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Si tratta di un set predefinito di glifi impostata dall'IDE, ad esempio un lucchetto per l'icona "Selezionata In" e un segno di spunta come il glifo "Estratto".  
  
### <a name="custom-set-of-glyphs"></a>Insieme di glifi personalizzati  
 Un controllo del codice sorgente VSPackage è possibile utilizzare i proprio glifi per un "un aspetto univoco" quando viene installato. Quando un nuovo controllo del codice sorgente VSPackage è attivo, deve essere in grado di iniziare a usare i proprio glifi anche se un precedente controllo origine VSPackage viene ancora caricato, ma inattiva. In questa modalità, il controllo del codice sorgente VSPackage ancora possibile usare le icone esistente per mantenere un aspetto coerente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se sceglie.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servizio supporta un'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, che il pacchetto VSPackage può implementare facoltativamente e che verrà richiesto di immettere dall'IDE. Quando l'IDE effettua una richiesta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verrà a sua volta tenta di ottenere questa interfaccia dal controllo di origine attualmente registrata VSPackage. Se l'interfaccia esiste nel pacchetto VSPackage registrato, la richiesta dell'IDE per icone personalizzate ha esito positivo; in caso contrario, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Usa il set predefinito di icone.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> metodo viene utilizzato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per ottenere un elenco di immagini di controllo del codice sorgente vari stati. Restituisce il controllo del codice sorgente VSPackage all'IDE di un handle all'elenco di immagini per il relativo icone personalizzate. L'IDE crea una copia dell'elenco immagini a questo punto e viene utilizzato in un secondo momento per scegliere le icone da visualizzare. Se non è supportata la nuova interfaccia o `IVsSccGlyphs::GetCustomGlyphList` restituisce E_NOTIMPL, quindi l'IDE Ottiene relativo glifi dall'elenco predefinito di glifi forniti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>