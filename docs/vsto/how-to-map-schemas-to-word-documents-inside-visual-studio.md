---
title: 'Procedura: mappare schemi a documenti di Word in Visual Studio | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 65ecd3adbeb6f554a901345c2fa5dbf8359a1428
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Procedura: effettuare il mapping degli schemi a documenti di Word in Visual Studio
  **Importante** le informazioni in questo argomento relative a Microsoft Word sono presentata esclusivamente per il vantaggio e l'uso di singoli utenti e organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che utilizzano o lo sviluppo i programmi eseguibili in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio 2010, Microsoft la rimozione di un'implementazione di una particolare funzionalità correlata a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word potrebbero non essere lette o utilizzate dal singoli individui o organizzazioni negli Stati Uniti o relativi territori, che utilizza o lo sviluppo di programmi eseguibili in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti con licenza prima di tale data o acquistati e concesso in licenza di fuori degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 È possibile eseguire il mapping di uno schema XML a un documento mentre il documento è aperto in Visual Studio. Utilizzare gli stessi strumenti di Microsoft Office Word che è utilizzare quando il documento è aperto all'esterno di Visual Studio. Se si esegue il mapping dello schema al documento prima o dopo aver creato la soluzione per Word, il progetto di Office crea gli stessi oggetti.  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Per eseguire il mapping di uno schema XML a un documento di Word in Visual Studio  
  
1.  Aprire il progetto di modello o documento di Word in Visual Studio.  
  
2.  Fare clic nel documento per spostare lo stato attivo alla finestra di progettazione.  
  
3.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Nel **XML** gruppo, fare clic su **Schema**.  
  
     Il **modelli e componenti aggiuntivi** verrà visualizzata la finestra di dialogo.  
  
5.  Fare clic su di **XML Schema** scheda.  
  
6.  Fare clic su **aggiungere Schema**.  
  
     Il **Aggiungi Schema** verrà visualizzata la finestra di dialogo.  
  
7.  Individuare il file di schema, selezionarlo e quindi fare clic su **aprire**.  
  
     Il **impostazioni Schema** verrà visualizzata la finestra di dialogo.  
  
8.  Assegnare un alias o fare clic su **OK** per aggiungere lo schema senza un alias.  
  
9. Fare clic su **OK**.  
  
     Il **struttura XML** verrà visualizzata la finestra.  
  
10. Trascinare gli elementi dal **struttura XML** finestra per i punti del documento in cui si desidera creare i corrispondenti controlli.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: mappare schemi a fogli di lavoro all'interno di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  