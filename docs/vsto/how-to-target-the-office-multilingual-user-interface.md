---
title: "Procedura: l'interfaccia utente multilingue di Office di destinazione | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 54b305311b686f527a79092280fbc33c3974247e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procedura: utilizzare l'interfaccia utente multilingue (MUI) di Office
  Multilingual User Interface (MUI) è una funzionalità di Microsoft Office che consente all'utente finale la possibilità di modificare la lingua dell'interfaccia utente (UI). Ad esempio, un utente finale, utilizzo di un'interfaccia utente in inglese è possibile modificare la lingua dell'interfaccia utente per lo spagnolo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se l'applicazione verrà utilizzata da persone che utilizzano più lingue di Office, è possibile aggiungere codice per modificare automaticamente la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua utilizzata dalle applicazioni di Office nel computer dell'utente (se l'utente ha installate le risorse corrette).  
  
### <a name="to-check-the-current-office-ui-setting"></a>Per controllare l'impostazione corrente dell'interfaccia utente di Office  
  
1.  Utilizzare il <xref:System.Threading.Thread.CurrentUICulture%2A> proprietà del thread corrente. Impostare la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua utilizzata dalla versione di Office attualmente in esecuzione nel computer dell'utente.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)  
  
  