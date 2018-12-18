---
title: "Procedura: includere un Assembly personalizzato in una funzionalità di integrazione applicativa dei dati | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 32554a0456c34a3c8b1d96c471fd7ae8e9221943
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati
  Il progetto fa riferimento l'assembly da altri progetti nella stessa soluzione. Tuttavia, è necessario aggiungere questi assembly nel file di funzionalità del progetto tramite la **assegna a cui fa riferimento agli assembly di oggetti LobSystem** la finestra di dialogo.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Per includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati (BDC)  
  
1.  In **Esplora**, scegliere la cartella che contiene il modello di integrazione applicativa dei dati.  
  
2.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.  
  
3.  Nel **proprietà** finestra, scegliere il **assembly** proprietà, quindi sui puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET per dispositivi mobili Ellisse progettazione")).  
  
     Il **assegna a cui fa riferimento agli assembly di oggetti LobSystem** viene visualizzata la finestra di dialogo.  
  
4.  Nel **selezionare un Assembly** scegliere l'assembly personalizzato.  
  
    > [!NOTE]  
    >  Vengono visualizzati solo gli assembly di **assegna a cui fa riferimento agli assembly di oggetti LobSystem** la finestra di dialogo se è stato aggiunto un riferimento al progetto contenente l'assembly. Per ulteriori informazioni, vedere [procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  Nel **le proprietà di riferimento** gruppo, aprire l'elenco visualizzato per il **ambito LobSystem** proprietà, scegliere il sistema LOB dei metodi che utilizzano l'assembly personalizzato e quindi scegliere il **OK**  pulsante.  
  
    > [!NOTE]  
    >  Per eseguire il debug di codice nell'assembly personalizzato, è necessario aggiungere l'assembly per il pacchetto della soluzione. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: utilizzare un File di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: aggiungere un File di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Creazione di un modello di integrazione applicativa dei dati Business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  