---
title: Progetto di modellazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c3d87a44838ead7663ff4c156985ab1b8e98eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-modeling"></a>Modello di progetto
Il passaggio successivo nella fornitura di automazione per il progetto è possibile implementare gli oggetti di progetto standard: il <xref:EnvDTE.Projects> e `ProjectItems` raccolte; `Project` e <xref:EnvDTE.ProjectItem> degli oggetti e gli oggetti rimanenti univoci per l'implementazione. Questi oggetti standard vengono definiti nel file Dteinternal.h. Nell'esempio BscPrj viene fornita un'implementazione degli oggetti standard. È possibile utilizzare queste classi come modelli per creare gli oggetti di progetto standard che stand-by-side con oggetti del progetto da altri tipi di progetto.  
  
 Si presuppone un consumer di automazione per poter chiamare <xref:EnvDTE.Solution>("`<UniqueProjName>")` e <xref:EnvDTE.ProjectItems> (`n`) dove n è un numero di indice per l'acquisizione di un progetto specifico nella soluzione. Effettuare questa chiamata di automazione di conseguenza, l'ambiente di chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> nella gerarchia di progetto appropriato, passando VSITEMID_ROOT come parametro ItemID VSHPROPID_ExtObject come parametro VSHPROPID. `IVsHierarchy::GetProperty`Restituisce un `IDispatch` puntatore all'oggetto di automazione, fornendo la base `Project` interfaccia, che è stato implementato.  
  
 Di seguito è la sintassi di `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Progetti adattare l'annidamento e usare le raccolte per creare gruppi di elementi di progetto. La gerarchia è simile al seguente.  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 La nidificazione indica che un <xref:EnvDTE.ProjectItem> oggetto può essere <xref:EnvDTE.ProjectItems> insieme nello stesso momento poiché un `ProjectItems` raccolta può contenere oggetti nidificati. L'esempio di progetto di base non viene illustrato l'annidamento. Implementando il `Project` dell'oggetto, si prende parte della struttura ad albero che caratterizza la progettazione del modello di automazione generali.  
  
 L'automazione progetto segue il percorso nel diagramma seguente.  
  
 ![Gli oggetti di progetto di Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automazione di progetto  
  
 Se non si implementa un `Project` dell'oggetto, l'ambiente verrà comunque restituito un oggetto generico `Project` oggetto che contiene solo il nome del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>