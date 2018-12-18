---
title: Elenco di oggetti finestra delle proprietà | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6b7d238f7ce64122ac18a52dab59afb063ce47e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="properties-window-object-list"></a>Elenco di oggetti finestra delle proprietà
Nell'elenco di oggetti nel **proprietà** finestra è un elenco di riepilogo a discesa che consente di modificare la selezione ad altri oggetti disponibili all'interno di uno o più finestre selezionate. Selezione di un oggetto diverso da all'interno dell'elenco genera una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> per informare l'ambiente che è stato selezionato un nuovo oggetto. Le informazioni visualizzate nel **proprietà** finestra viene quindi modificata per visualizzare le proprietà associate all'oggetto selezionato.  
  
## <a name="the-object-list"></a>Elenco di oggetti  
 L'elenco di oggetti è costituito da due campi: il nome dell'oggetto (visualizzato in grassetto) e il tipo di oggetto.  
  
 Il nome dell'oggetto visualizzato a sinistra del tipo di oggetto in grassetto viene recuperato dall'oggetto stesso utilizzando il `Name` proprietà fornita dal <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfaccia. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, l'unico metodo sul <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, restituisce <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> per coclasse dell'interfaccia. Il **proprietà** finestra utilizza <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> per ottenere il nome della coclasse, che viene visualizzato come il nome dell'oggetto nell'elenco a discesa.  
  
 Se l'oggetto non ha un `Name` proprietà, un nome non viene visualizzata nell'area del nome dell'elenco di oggetti. Se si desidera che il nome visualizzato nell'elenco di oggetti, è possibile aggiungere una proprietà Name per l'oggetto.  
  
 Se l'oggetto COM non implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **proprietà** finestra Visualizza il nome di interfaccia al posto del nome di oggetto sul lato sinistro dell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)