---
title: Utilizzo di moduli per includere i file nella soluzione | Documenti Microsoft
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
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c7f0fff081215e1bf1a9e2c5320668f2c698b2e6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="using-modules-to-include-files-in-the-solution"></a>Utilizzo di moduli per includere file nella soluzione
  È possibile che quando si desidera distribuire i file nel server di SharePoint indipendentemente dal tipo di file, ad esempio pagine master. A tale scopo, è possibile utilizzare *moduli* (da non confondere con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli di codice). I moduli sono contenitori per i file in una soluzione di SharePoint. Quando si distribuisce la soluzione, i file nel modulo vengono copiati nelle cartelle specificate nel server SharePoint.  
  
## <a name="module-items-and-elements"></a>Elementi del modulo  
 Per creare un modulo, aggiungerlo a un progetto scegliendolo nella **Aggiungi nuovo elemento** la finestra di dialogo. Quindi, modificare il file Elements.xml per includere i nomi dei file di cui che si desidera distribuire, in cui si trovano nel sistema e devono essere copiati nel server SharePoint.  
  
 Di seguito è riportato un esempio del file Elements.xml per un modulo:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Appena creato moduli contengono i file predefiniti seguenti:  
  
|Nome file|Descrizione|  
|---------------|-----------------|  
|Elements|File di definizione per il modulo.|  
|Sample|File segnaposto che funge da un esempio di un file nel modulo.|  
  
 Il file Elements.xml contiene gli elementi seguenti:  
  
|Nome elemento|Descrizione|  
|------------------|-----------------|  
|Elementi|Contiene tutti gli elementi definiti nel modulo.|  
|Modulo|L'elemento di modulo ha un solo attributo, *nome*, che specifica il nome del modulo nel formato `<Module Name="Module1">`.<br /><br /> Si noti che se si modifica il nome del modulo (o dai relativi *nome della cartella* proprietà), è necessario aggiornare manualmente il nome nell'elemento modulo.<br /><br /> Se si specifica una sottodirectory per i file nell'elemento modulo [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) crea automaticamente una struttura di directory corrispondente per loro.|  
|File|Il File dispone di due parametri, *percorso* e *Url*.<br /><br /> -Path: Il nome e percorso del file della soluzione di SharePoint. Il formato è, `Path="Module1\Sample.txt"`.<br /><br /> -Url: Il percorso in cui verrà distribuito il file nel server SharePoint. Il formato è, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Attributo facoltativo che dispone di due impostazioni: *GhostableInLibrary* e *Ghostable*. Il formato è, `Type="GhostableInLibrary"`. Specifica di *GhostableInLibrary* significa che il file verrà aggiunto a una raccolta documenti di SharePoint insieme a un elemento di elenco associata al file quando viene aggiunto alla raccolta. Specifica di *Ghostable* , il file viene aggiunto a SharePoint all'esterno della libreria di documenti.|  
  
 Ogni file che si desidera distribuire richiede un apposito `<File>` voce elemento Elements.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: includere file mediante un modulo](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [Procedura: eseguire il provisioning di un file](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  