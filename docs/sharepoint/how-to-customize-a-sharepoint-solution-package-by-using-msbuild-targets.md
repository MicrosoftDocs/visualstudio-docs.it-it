---
title: 'Procedura: personalizzare un pacchetto di soluzione SharePoint tramite le destinazioni di MSBuild | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fea1719eb80515a97a1b18336f1653cb535359e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
  
4.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto e quindi scegliere **modificare***ProjectName***vbproj** oppure **modifica***ProjectName*** csproj**.  
  
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
  
  