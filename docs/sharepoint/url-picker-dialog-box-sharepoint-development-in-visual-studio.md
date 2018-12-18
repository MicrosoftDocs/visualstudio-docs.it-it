---
title: Finestra di dialogo Selezione URL (sviluppo per SharePoint in Visual Studio) | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 65851596d7a9df1ec7da9106891dff6471f1afb6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Finestra di dialogo di selezione URL (sviluppo per SharePoint in Visual Studio)
  Nella finestra di dialogo di selezione URL è possibile scegliere i file come file di pagina master o file di immagine posizionati nel progetto o nel server locale in cui è in esecuzione SharePoint.  
  
 Questa finestra di dialogo viene visualizzata se è possibile scegliere un file per impostare una proprietà. È possibile aprire questa finestra di dialogo facendo clic sul pulsante con i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) accanto a varie proprietà nel **proprietà** finestra. Il pulsante con i puntini di sospensione inoltre viene visualizzato come un IntelliSense prompt dei comandi quando si assegnano valori a determinati attributi nel **origine** della finestra di progettazione.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Cartelle progetto**  
 Viene visualizzato un elenco delle cartelle definite nel progetto o nel server locale in cui è in esecuzione SharePoint. Scegliere il pulsante di espansione per visualizzare le sottocartelle.  
  
 Espandere il **progetto** nodo per scegliere i file nel progetto. Per essere visualizzati come selezionabili nella finestra di dialogo, i file di progetto devono soddisfare i criteri seguenti:  
  
-   Il file deve essere contenuto in una cartella mappata.  
  
-   Il file deve essere aggiunto al pacchetto della soluzione.  
  
-   Il file non può trovarsi in un altro progetto.  
  
 Se si desidera fare riferimento ai file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.  
  
 Espandere il **Server** nodo per scegliere i file che si trovano nel server locale in cui è in esecuzione SharePoint. Per essere visualizzati come selezionabili nella finestra di dialogo, questi file devono soddisfare i criteri seguenti:  
  
-   Il file deve trovarsi in una delle seguenti cartelle mappate: **immagini**, **layout**, o **ControlTemplate**.  
  
-   Il file non può trovarsi nel database del contenuto di SharePoint.  
  
 Se si desidera fare riferimento ai file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.  
  
 **Contenuto della cartella**  
 Consente di visualizzare un elenco di file contenuti nella cartella selezionata. Scegliere un file, quindi il **OK** per chiudere la finestra di dialogo e inviare la selezione al processo che lo hanno chiamato.  
  
 **File di tipo**  
 Consente di scegliere da un elenco di file appropriati per l'attività in esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
  