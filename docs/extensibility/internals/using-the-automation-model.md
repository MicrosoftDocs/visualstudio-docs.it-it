---
title: Utilizzando il modello di automazione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 679e9966e66de1c79cb3c6394f1d80ab6d6733bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-automation-model"></a>Utilizzando il modello di automazione
Dopo aver connesso il pacchetto VSPackage per l'automazione, è possibile ottenere le proprietà e metodi chiamando il <xref:EnvDTE.DTEClass.GetObject%2A> metodo il <xref:EnvDTE._DTE> oggetto, passando una stringa che rappresenta l'oggetto che si desidera recuperare.  
  
## <a name="obtaining-project-objects"></a>Recupero di oggetti del progetto  
 Di seguito è riportati due esempi di codice che illustrano come un consumer di automazione Ottiene il progetto oggetti di automazione. Per informazioni su come ottenere l'oggetto DTE, vedere [procedura: ottenere riferimenti a DTE e DTE2 oggetti](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 A questo punto, è possibile utilizzare gli oggetti di progetto standard che fanno parte di un VSPackage specifico per spostare verso il basso il modello di gerarchia.  
  
 Esempio di codice seguente viene illustrato come ottenere un oggetto personalizzato che è una proprietà di un tipo di progetto personalizzato.:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 Il codice seguente elenca i nomi di tutte le proprietà nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente **generale** opzione il **strumenti** menu:  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE.DTEClass.GetObject%2A>