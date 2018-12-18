---
title: 'Procedura: aggiungere e rimuovere assembly aggiuntivi | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 13ea5388a7b4ce2d1a045dec6339dc59e5c68393
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Procedura: Aggiungere e rimuovere assembly aggiuntivi
  Se un pacchetto di SharePoint dipende da altri assembly per la funzionalità o dati, è possibile aggiungere gli assembly al pacchetto della soluzione (con estensione wsp). In questo modo, il server SharePoint assicura che gli assembly personalizzati vengono installati con un pacchetto.  
  
 È anche possibile aggiungere e modificare i controlli sicuri e il file di risorse di classe associati agli assembly.  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>Aggiunta di assembly aggiuntivi, controlli sicuri e le risorse di classe  
 È possibile aggiungere ulteriori assembly nel pacchetto della soluzione SharePoint. Distribuzione di assembly aggiuntivi in una soluzione creata mediante sandbox global assembly cache, ma gli elementi di progetto SharePoint in una soluzione creata mediante sandbox vengono aggiunti al database del contenuto. È anche possibile aggiungere controlli sicuri e risorse di classe a questi assembly aggiuntivi. Per ulteriori informazioni sui controlli sicuri, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o "Creazione di una voce di SafeControl" nel [distribuzione di Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Per aggiungere un assembly esistente  
  
1.  Aprire il **Progettazione pacchetti**. Per ulteriori informazioni, vedere [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere il **avanzate** scheda.  
  
3.  Scegliere il **Aggiungi** e quindi scegliere **Aggiungi Assembly esistente** dall'elenco.  
  
     Il **Aggiungi Assembly esistente** viene visualizzata la finestra di dialogo.  
  
4.  Scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")), quindi scegliere l'assembly che si desidera aggiungere. È consigliabile utilizzare un percorso relativo per l'assembly selezionato per motivi di portabilità.  
  
5.  Per il **destinazione distribuzione**, scegliere il **GlobalAssemblyCache** pulsante di opzione per distribuire l'assembly in global assembly cache, oppure scegliere di **WebApplication** opzione pulsante per distribuire l'assembly nella cartella WebApplication nel server in cui è in esecuzione SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Per aggiungere un assembly da output del progetto  
  
1.  Aprire il **Progettazione pacchetti**.  
  
     Per ulteriori informazioni, vedere [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere il **avanzate** scheda.  
  
3.  Scegliere il **Aggiungi** e quindi scegliere **Aggiungi Assembly da Output del progetto** dall'elenco.  
  
     Il **Aggiungi Assembly da Output del progetto** viene visualizzata la finestra di dialogo.  
  
4.  Nel **progetto di origine** elenco e scegliere il progetto di origine che si desidera aggiungere.  
  
5.  Per il **destinazione distribuzione**, scegliere il **GlobalAssemblyCache** pulsante di opzione per distribuire l'assembly in global assembly cache, oppure scegliere di **WebApplication** opzione pulsante per distribuire l'assembly nella cartella WebApplication nel server in cui è in esecuzione SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Per aggiungere un controllo sicuro  
  
1.  Aprire il **modifica Assembly esistente** la finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly, quindi il **modifica**pulsante.  
  
2.  Nel **controlli sicuri** riquadro, scegliere il **fare clic qui per aggiungere un nuovo elemento** pulsante.  
  
3.  Nel **nome Assembly** colonna, immettere il nome dell'assembly.  
  
4.  Nel **Namespace** colonna, immettere il nome dello spazio dei nomi per il controllo sicuro.  
  
5.  Nel **nome del tipo** colonna, immettere il nome del tipo.  
  
#### <a name="to-add-a-class-resource"></a>Per aggiungere una risorsa di classe  
  
1.  Aprire il **modifica Assembly esistente** la finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly, quindi il **modifica** pulsante.  
  
2.  Nel **risorse di classe** riquadro, scegliere il **fare clic qui per aggiungere un nuovo elemento** pulsante.  
  
3.  Nel **nome File** colonna, scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) e scegliere la risorsa di classe che si desidera aggiungere.  
  
## <a name="deleting-custom-assemblies"></a>Eliminazione di assembly personalizzati  
 È possibile eliminare gli assembly da un pacchetto di SharePoint o eliminare i controlli sicuri e risorse di classe da assembly esistenti.  
  
#### <a name="to-delete-an-existing-assembly"></a>Per eliminare un assembly esistente  
  
1.  Aprire il **Progettazione pacchetti**. Per ulteriori informazioni, vedere [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere il **avanzate** scheda.  
  
3.  Nel **assembly aggiuntivi** riquadro, scegliere l'assembly personalizzato che si desidera eliminare.  
  
4.  Scegliere il **eliminare** pulsante.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Per eliminare un controllo sicuro per un assembly  
  
1.  Aprire il **modifica Assembly esistente** la finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly, quindi il **modifica** pulsante.  
  
2.  Scegliere il controllo sicuro che si desidera eliminare.  
  
3.  Scegliere il tasto CANC.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Per eliminare una risorsa di classe per un assembly  
  
1.  Aprire il **modifica Assembly esistente** la finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly, quindi il **modifica** pulsante.  
  
2.  Scegliere la risorsa di classe che si desidera eliminare.  
  
3.  Scegliere il tasto CANC.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
  