---
title: '&lt;aggiornare&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f0e1fdc26e285ce9b6a1fd5ecc1aa638fe909b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;aggiornare&gt; elemento (sviluppo per Office in Visual Studio)
  Il `update` elemento specifica l'intervallo in cui la soluzione controllerà gli aggiornamenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `update` è obbligatorio e si trova nello spazio dei nomi `vstav3`.  
  
 Il `update` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`enabled`|Obbligatorio. Impostare enabled su uno dei valori seguenti:<br /><br /> -   **true** per cercare gli aggiornamenti.<br />-   **false** per impedire il controllo degli aggiornamenti.|  
  
 Il `update` i seguenti elementi figlio.  
  
### <a name="expiration"></a>scadenza  
 L'elemento `expiration` è obbligatorio e si trova nello spazio dei nomi `vstav3`. Questo elemento specifica l'intervallo in cui la soluzione controlla gli aggiornamenti.  
  
 Il `expiration` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`maximumAge`|-Obbligatorio. Impostare su un numero intero.|  
|`unit`|Obbligatorio. Impostare `unit` a uno dei valori seguenti:<br /><br /> -   **Ore**<br />-   **Giorni**<br />-   **Settimane**|  
  
## <a name="example-of-always-checking-for-updates"></a>Ad esempio sempre il controllo degli aggiornamenti  
  
### <a name="description"></a>Descrizione  
 Nell'esempio di codice seguente viene illustrato un `update` elemento su cui è impostata per verificare sempre gli aggiornamenti nelle soluzioni Office.  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Esempio di impostazione di un intervallo di aggiornamento predefinito  
  
### <a name="description"></a>Descrizione  
 Nell'esempio di codice seguente viene illustrato un `update` elemento in un manifesto dell'applicazione per le soluzioni Office. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  