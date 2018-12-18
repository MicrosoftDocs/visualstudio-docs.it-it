---
title: '&lt;Le pianificazioni&gt; elemento (programma di avvio automatico) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: "5"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b7924515dbb661a4281397817be4b1b68487a6ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Le pianificazioni&gt; elemento (programma di avvio automatico)
Il `Schedules` elemento contiene `Schedule` elementi che definiscono l'ora specifica a quali comandi definiti per il `Command` elemento deve essere eseguito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `Schedules` è un elemento figlio del `Product` elemento. Ogni `Product` elemento può contenere al massimo una `Schedules` elemento. Il `Schedules` elemento non ha attributi.  
  
## <a name="schedule"></a>Pianificazione  
 Il `Schedule` è un elemento figlio del `Schedules` elemento. Oggetto `Schedules` l'elemento deve avere almeno un `Schedule` elemento.  
  
 `Schedule`presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Il nome dell'elemento di pianificazione. Corrisponde alla `ScheduleName` proprietà del `Command` elemento. Quando un `Command` fa riferimento alla pianificazione specificata, verrà eseguito solo nell'orario indicato da tale `Schedule` elemento. Le pianificazioni possono anche essere associate le `FailIf` e `BypassIf` elementi, che limitano l'esecuzione in base alla pianificazione specificata questi test condizionale. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
  
 Un determinato `Schedule` elemento può avere esattamente uno degli elementi figlio seguenti.  
  
## <a name="buildlist"></a>BuildList  
 Il `BuildList` elemento indica al programma di installazione per eseguire un comando, subito dopo l'avvio di applicazione di avvio automatico.  
  
## <a name="beforepackage"></a>BeforePackage  
 Il `BeforePackage` elemento indica al programma di installazione per eseguire un comando prima di installata il pacchetto specificato.  
  
## <a name="afterpackage"></a>AfterPackage  
 Il `AfterPackage` elemento indica al programma di installazione per eseguire un comando, dopo aver installato il pacchetto specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [\<Prodotto > elemento](../deployment/product-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)