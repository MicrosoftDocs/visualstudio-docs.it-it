---
title: 'Procedura: impostare le informazioni di configurazione per una soluzione Office | Documenti Microsoft'
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
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6f604fa40a9816d5e46593bc50fcb91f82d13325
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Procedura: definire le informazioni di configurazione per una soluzione Office
  È possibile utilizzare i file di configurazione per configurare le impostazioni specifiche per le soluzioni Office. È possibile specificare impostazioni quali criteri di associazione degli assembly, oggetti remoti, debug e le impostazioni di traccia.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Per aggiungere un file di configurazione al progetto di Office  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nel **categorie** riquadro, fare clic su **generale**.  
  
3.  Nel **modelli** riquadro, selezionare **File di configurazione applicazione**.  
  
4.  Nel **nome** digitare lo stesso nome dell'assembly con estensione config. Ad esempio, un file di configurazione per un assembly di progetto di Excel denominato ExcelWorkbook1.dll verrebbe denominato Excelworkbook1.  
  
5.  Fare clic su **Aggiungi**.  
  
6.  Creare il file di configurazione in base allo schema di file di configurazione dell'applicazione. Per ulteriori informazioni, vedere [Schema di File di configurazione per .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 Non esistono considerazioni speciali per l'utilizzo di file di configurazione con i progetti di Office.  
  
## <a name="see-also"></a>Vedere anche  
 [Schema di File di configurazione per .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  