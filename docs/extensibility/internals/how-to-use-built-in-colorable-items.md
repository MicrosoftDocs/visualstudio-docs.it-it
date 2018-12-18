---
title: 'Procedura: usare elementi colorabili predefiniti | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6cf51516677aeca71dba269bcdd132e0830b6b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: usare elementi di colori predefiniti
Prima di utilizzare gli elementi di colori predefiniti, è necessario innanzitutto segnalare all'ambiente di sviluppo integrato (IDE) che si desidera non fornire i propri elementi di colori personalizzati, in questo caso sarebbe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> oggetti. Questo caso, impostare una voce del Registro di sistema per il servizio di linguaggio.  
  
### <a name="to-use-built-in-colorable-items"></a>Utilizzare gli elementi di colori predefiniti  
  
1.  In HKEY_LOCAL_MACHINE\VisualStudio\\*x. y*\Languages\Language servizi\\*nome di lingua*, dove *x. y* è una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e *nome di lingua* è il nome del linguaggio di creare un valore di voce del Registro di sistema DWORD denominato `RequestStockColors`.  
  
2.  Impostare il `RequestStockColors` valore di una voce del Registro di sistema su 1.  
  
     Dopo aver creato la voce di registro, la rappresentazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo può utilizzare i membri del <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumerazione per riempire la matrice di attributi di colore da utilizzare dall'editor.  
  
    > [!NOTE]
    >  Non impostare questa voce del Registro di sistema se si distribuiscono gli elementi di colori personalizzati. Per ulteriori informazioni, vedere [personalizzate colorabile](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sintassi colorazione nell'editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [In un servizio di linguaggio Legacy colorazione sintassi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione di colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementi di colori personalizzati](../../extensibility/internals/custom-colorable-items.md)   
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)