---
title: 'Procedura: identificare i simboli in una libreria | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 310ba421120101ce545888bcf4c069ca454cf086
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-identify-symbols-in-a-library"></a>Procedura: identificare i simboli in una libreria
Strumenti di esplorazione simbolo visualizzano gerarchiche di simboli. I simboli rappresentano gli spazi dei nomi, gli oggetti, classi, membri della classe e altri elementi del linguaggio.  
  
 Ogni simbolo nella gerarchia può essere identificata mediante le informazioni sulla navigazione passati dalla libreria di simboli per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestione degli oggetti tramite le interfacce seguenti:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Il percorso del simbolo nella gerarchia distingue un simbolo. Consente di strumenti di esplorazione simbolo passare a un simbolo specifico. Il percorso completo univoco per il simbolo determina la posizione. Ogni elemento del percorso è un nodo. Il percorso inizia con il nodo di livello principale e termina con il simbolo specifico. Ad esempio, se il metodo M1 è un membro della classe C1 è C1 nello spazio dei nomi N1, il percorso completo del metodo M1 è N1. C1. M1. Il percorso contiene tre nodi: N1, C1 e M1.  
  
 Le informazioni sulla navigazione consente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] object manager per individuare e selezionare mantenere selezionata i simboli nella gerarchia. Consente di passare da uno strumento di visualizzazione a altra. Quando si utilizza **Visualizzatore oggetti** per individuare i simboli in un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetto, è possibile fare clic con il pulsante destro un metodo e avviare il **Visualizzatore chiamate** strumento per visualizzare il metodo in un grafico delle chiamate.  
  
 Due forme descrivono la posizione del simbolo. La forma canonica è in base al percorso completo del simbolo. Rappresenta una posizione univoca del simbolo nella gerarchia. È indipendente dello strumento per l'esplorazione del simbolo. Per ottenere le informazioni di formato canonico, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] object manager chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodo. Il formato di presentazione descrive il percorso del simbolo all'interno di uno strumento specifico per l'esplorazione del simbolo. La posizione del simbolo è relazione alla posizione di altri simboli nel hierarchicy. Un simbolo specificato potrebbe essere più percorsi di presentazione, ma solo un percorso canonico. Ad esempio, se C1 classe è ereditata dalla classe C2, entrambe le classi nello spazio dei nomi N1, il **Visualizzatore oggetti** consente di visualizzare lo struttura ad albero gerarchica seguente:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Il percorso canonico della classe C2, in questo esempio è N1 + C2. Il percorso di presentazione di C2 include nodi C1 e "E interfacce di base": N1 + C1 + "E interfacce di base" + C2.  
  
 Per ottenere le informazioni di formato di presentazione, le chiamate del gestore oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metodo.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identificazione di un simbolo nella gerarchia  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Per ottenere canonico e form di presentazione di informazioni  
  
1.  Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Gestione degli oggetti chiama questo metodo per ottenere l'elenco dei nodi contenuti nel percorso canonico del simbolo.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Gestione degli oggetti chiama questo metodo per ottenere l'elenco dei nodi contenuti nel percorso di presentazione del simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Procedura: registrare una libreria con il gestore oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)