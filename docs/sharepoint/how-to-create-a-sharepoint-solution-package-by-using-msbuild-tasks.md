---
title: 'Procedura: creare un pacchetto di soluzione SharePoint tramite le attività di MSBuild | Documenti Microsoft'
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
ms.openlocfilehash: 629b63b8645f1b5ebd84d25a04a4cec4e8bca6a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Procedura: Creare un pacchetto della soluzione SharePoint tramite le attività MSBuild
  È possibile compilare, pulire e convalidare un pacchetto di SharePoint (con estensione wsp), usare le attività di MSBuild dalla riga di comando in un computer di sviluppo. È anche possibile utilizzare questi comandi per automatizzare il processo di compilazione tramite Team Foundation Server in un computer di compilazione.  
  
## <a name="building-a-sharepoint-package"></a>Compilazione di un pacchetto di SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Per creare un pacchetto di SharePoint  
  
1.  Di Windows **avviare** menu, scegliere **tutti i programmi**, **Accessori**, **prompt dei comandi**.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per creare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei comandi seguenti per creare un progetto SharePoint denominato ListDefinition1 il pacchetto.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>La pulizia di un pacchetto di SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Per eliminare un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per eliminare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei seguenti comandi per eliminare un progetto SharePoint denominato ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>Convalida di un pacchetto di SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Per convalidare un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per convalidare un pacchetto per il progetto. Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei seguenti comandi per la convalida di un progetto SharePoint denominato ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>Impostazione delle proprietà in un pacchetto di SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Per impostare una proprietà in un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory in cui si trova il progetto SharePoint.  
  
3.  Immettere il comando seguente per impostare una proprietà in un pacchetto per il progetto. Sostituire *PropertyName* con la proprietà che si desidera impostare.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per impostare il livello di avviso.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  