---
title: 'Procedura: personalizzare un pacchetto di soluzione SharePoint tramite le destinazioni di MSBuild | Documenti Microsoft'
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
helpviewer_keywords: SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ab9aa26efe3002c28ec031457d2732c828eca445
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Procedura: personalizzare un pacchetto della soluzione SharePoint tramite le destinazioni di MSBuild
  È possibile personalizzare la modalità di creazione di Visual Studio dei file di pacchetto (con estensione wsp) di SharePoint tramite le destinazioni di MSBuild a un prompt di comandi. Ad esempio è possibile personalizzare le proprietà di MSBuild per modificare la directory intermedia dei pacchetti e i gruppi di elementi di MSBuild con cui si specificano i file enumerati.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Personalizzazione ed esecuzione delle destinazioni di MSBuild  
 Se si personalizzano le destinazioni di BeforeLayout e AfterLayout, è possibile eseguire le attività prima del layout del pacchetto, ad esempio aggiungendo, rimuovendo o modificando i file che verranno inclusi nel pacchetto.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Per personalizzare la destinazione di BeforeLayout  
  
1.  Aprire un editor, ad esempio Blocco note, quindi aggiungere il codice riportato di seguito.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     In questo esempio viene visualizzato un messaggio prima della creazione del pacchetto di questa destinazione.  
  
2.  Nome del file **CustomLayout**, quindi salvarlo nella cartella del progetto SharePoint.  
  
3.  Aprire il progetto, aprire il menu di scelta rapida e quindi scegliere **Scarica progetto**.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il progetto e quindi scegliere **modifica***ProjectName***vbproj** o **Modifica***ProjectName***csproj**.  
  
5.  Dopo la riga `Import` verso la fine del file di progetto, aggiungere la seguente riga.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Salvare e chiudere il file di progetto.  
  
7.  In **Esplora**, aprire il menu di scelta rapida per il progetto e quindi scegliere **Ricarica progetto**.  
  
 Quando si pubblica il progetto, il messaggio viene visualizzato nell'output prima che inizi la creazione del pacchetto.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Per personalizzare la destinazione AfterLayout  
  
1.  Nella barra dei menu, scegliere **File**, **aprire**, **File**.  
  
2.  Nel **Apri File** la finestra di dialogo, passare alla cartella del progetto, scegliere il file CustomLayout e quindi scegliere il **aprire** pulsante.  
  
3.  Prima del tag `</Project>` aggiungere il codice seguente:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     In questo esempio viene visualizzato un messaggio dopo la creazione del pacchetto di questa destinazione.  
  
4.  Salvare e chiudere il file di destinazioni.  
  
5.  Riavviare Visual Studio, quindi aprire il progetto.  
  
 Quando si pubblica il progetto, il messaggio di BeforeLayout viene visualizzato prima che inizi la creazione del pacchetto e il messaggio di AfterLayout viene visualizzato al termine della creazione del pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  