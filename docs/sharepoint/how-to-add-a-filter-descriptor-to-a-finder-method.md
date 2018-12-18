---
title: 'Procedura: aggiungere un descrittore di filtro a un metodo Finder | Documenti Microsoft'
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
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 06dcea1c8e6d8220461c201de443a26162a608e3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Procedura: aggiungere un descrittore di filtro a un metodo Finder
  Descrittori di filtro consentono agli utenti del modello di passare valori a metodi prima che vengano eseguiti. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Uno scenario comune è che gli utenti di SharePoint recuperare le istanze di un tipo di contenuto esterno che corrispondono a certi criteri. È possibile supportare questo scenario tramite l'aggiunta di un descrittore di filtro a un metodo Finder.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Per aggiungere un descrittore di filtro a un metodo Finder  
  
1.  Nel **Dettagli metodo di integrazione applicativa dei dati** finestra, espandere il nodo di un metodo Finder, espandere il **parametri** nodo, quindi aggiungere un parametro di input. Per ulteriori informazioni, vedere [procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  Nel **Dettagli metodo** finestra, scegliere il descrittore di tipo del parametro.  
  
3.  Nella barra dei menu, scegliere **vista**, **finestra proprietà**.  
  
4.  Nel **proprietà** finestra, impostare il **nome del tipo** proprietà a un tipo di dati appropriato per il filtro.  
  
     Ad esempio, un filtro potrebbe utilizzare una data di ordine per limitare il numero di ordini di vendita restituito dal metodo. Per supportare tale filtro, il **nome del tipo** proprietà del descrittore di tipo deve essere impostata su **System. DateTime**.  
  
5.  Nel **Dettagli metodo di** finestra, espandere il **descrittori di filtro** nodo.  
  
6.  In **aggiungere un descrittore di filtro** scegliere **Crea descrittore di filtro**.  
  
     Verrà visualizzato un nuovo descrittore di filtro di **descrittori di filtro** nodo.  
  
7.  Nella barra dei menu, scegliere **vista**, **finestra proprietà**.  
  
8.  Nel **proprietà** finestra, scegliere il **tipo** proprietà.  
  
9. Nell'elenco visualizzato per il **tipo** proprietà, scegliere il criterio di filtro desiderati.  
  
     Ad esempio, per creare un filtro che utilizza una data di ordine per limitare il numero di ordini di vendita restituiti in un metodo Finder, scegliere **confronto**. Un filtro di confronto garantisce che un metodo finder restituisce solo le istanze che soddisfano una condizione specifica. Per ulteriori informazioni su ogni criterio di filtro, vedere [tipi di filtri supportati per l'integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. Nel **proprietà** finestra, scegliere il **descrittori di tipo associati** proprietà.  
  
11. Nell'elenco visualizzato per il **descrittori di tipo associati** proprietà, scegliere il descrittore di tipo creato precedentemente in questa procedura. Il filtro verrà associato al parametro di input del metodo Finder.  
  
12. Aggiungere codice al metodo Finder che restituisce i dati. È possibile utilizzare il parametro di input come una condizione in una query select.  
  
     L'esempio seguente restituisce gli ordini di vendita sono la data specificata.  
  
    > [!NOTE]  
    >  Sostituire il valore di `ServerName` campo con il nome del server.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Progettazione di un modello di integrazione applicativa dei dati Business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  