---
title: Manifesti dell'applicazione per le soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e31eda8b1e3a1a0c311b35245f9b7690cc37aae0
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="application-manifests-for-office-solutions"></a>Manifesti di applicazione per le soluzioni Office
  Un manifesto dell'applicazione è un file XML che descrive gli assembly caricati in una soluzione Microsoft Office. Gli strumenti di sviluppo di Microsoft Office in Visual Studio usano lo schema del manifesto dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] definito nel riferimento [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest) .  
  
 I manifesti dell'applicazione delle soluzioni Office usano gli elementi e gli attributi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] seguenti.  
  
|Elemento|Descrizione|Attributi|  
|-------------|-----------------|----------------|  
|[&#60;assembly&#62; elemento &#40;dell'applicazione ClickOnce&#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|Obbligatorio. Elemento di primo livello.|`manifestVersion`|  
|[&#60;assemblyIdentity&#62; elemento &#40;dell'applicazione ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|Obbligatorio. Identifica l'assembly primario dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60;trustInfo&#62; elemento &#40;dell'applicazione ClickOnce&#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|Identifica i requisiti di sicurezza dell'applicazione.|Nessuno|  
|[&#60;entryPoint&#62; elemento &#40;dell'applicazione ClickOnce&#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|Obbligatorio. Identifica il punto di ingresso del codice dell'applicazione per l'esecuzione.|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60;dipendenza&#62; elemento &#40;dell'applicazione ClickOnce&#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|Obbligatorio. Identifica ogni dipendenza necessaria per l'esecuzione dell'applicazione. Può anche identificare gli assembly che è necessario preinstallare.|Nessuno|  
|[&#60;file&#62; elemento &#40;dell'applicazione ClickOnce&#41;](/visualstudio/deployment/file-element-clickonce-application)|Obbligatorio. Identifica ogni file non di assembly usato dall'applicazione. Può includere i dati sull'isolamento COM (Component Object Model) associati al file.|`name`<br /><br /> `size`|  
  
 I manifesti dell'applicazione delle soluzioni Office contengono l'elemento seguente nello spazio dei nomi `co.v1` .  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>   
```  
  
 Questi manifesti dell'applicazione contengono anche gli elementi e gli attributi seguenti nello spazio dei nomi `vstav3` .  
  
```  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customizations>  
      <customization>  
      </customization>  
    </customizations>  
  </application  
</addIn>  
```  
  
|Elemento|Descrizione|Attributi|  
|-------------|-----------------|----------------|  
|[&#60;customHostSpecified&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Obbligatorio. Contrassegna specificatamente il manifesto come soluzione Office.|Nessuno|  
|[&#60;componente aggiuntivo&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia i punti di ingresso in un solo spazio dei nomi.|Nessuno|  
|[&#60;entryPointsCollection&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Obbligatorio. Raggruppa tutti gli assembly di una o più soluzioni Office.|`id`|  
|[&#60;entryPoints&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Obbligatorio. Raggruppa tutti gli assembly da eseguire in una soluzione Office.|Nessuno|  
|[&#60;entryPoint&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Obbligatorio. Identifica l'assembly da eseguire in una soluzione Office.|`class`<br /><br /> `contract`|  
|[&#60;aggiornare&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Obbligatorio. Configura gli aggiornamenti per la soluzione.|`enabled`<br /><br /> `expiration`|  
|[&#60;postActions&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Facoltativo. Raggruppa tutte le azioni post-distribuzione, ovvero azioni che vengono eseguite dopo l'installazione di soluzioni Office.|Nessuno|  
|[&#60;postAction&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Facoltativo. Identifica un'azione post-distribuzione.|Nessuno|  
|[&#60;postActionData&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Facoltativo. Configura i dati di un'azione post-distribuzione.|Nessuno|  
|[&#60;applicazione&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Obbligatorio. Esegue il wrapping delle informazioni specifiche dell'applicazione in un solo nodo.|Nessuno|  
|[&#60;le personalizzazioni&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia le informazioni host specifiche di tutte le applicazioni in uno spazio dei nomi separato.|Nessuno|  
|[&#60;personalizzazione&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Obbligatorio. Archivia le informazioni host specifiche dell'applicazione in uno spazio dei nomi separato.|`xmlns`|  
|[&#60;documento&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Obbligatorio solo per soluzioni a livello di documento. Archivia le informazioni specifiche della personalizzazione.|`solutionId`|  
|[&#60;appAddin&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Obbligatorio solo per soluzioni a livello di applicazione. Archivia le informazioni specifiche della personalizzazione.|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60;friendlyName&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Facoltativo. Archivia il nome del componente aggiuntivo VSTO che viene visualizzato nell'elenco di componenti aggiuntivi VSTO installati.|Nessuno|  
|[&#60;Descrizione&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Obbligatorio solo per componenti aggiuntivi VSTO. Archivia la descrizione che viene visualizzata nell'elenco dei programmi installati.|Nessuno|  
|[&#60;formRegions&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo.|Nessuno|  
|[&#60;formRegion&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo.|`Name`|  
|[&#60;vstoRuntime&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Obbligatorio. Descrive una versione specifica del runtime di Visual Studio Tools per Office supportata dalla soluzione Office.|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## <a name="remarks"></a>Note  
 È possibile modificare manualmente i manifesti dell'applicazione e di distribuzione nelle soluzioni Office. In seguito, tali manifesti devono essere firmati nuovamente tramite lo Strumento per la generazione e la modifica di manifesti (mage.exe e mageui.exe). Per altre informazioni, vedere [Procedura: ripetere la firma dei manifesti dell'applicazione e di distribuzione](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="file-location"></a>Percorso file  
 Un manifesto dell'applicazione è specifico per una singola versione di una soluzione. Per questo motivo, i manifesti dell'applicazione devono essere archiviati separatamente da quelli di distribuzione. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posiziona i file specifici della versione in una sottodirectory denominata in base alla versione associata nella sottodirectory **File applicazione** nella cartella di pubblicazione.  
  
## <a name="file-name-syntax"></a>Sintassi del nome file  
 Il nome di un file manifesto dell'applicazione deve essere composto dal nome completo e dall'estensione dell'applicazione come identificati nell'elemento `assemblyIdentity` , seguiti dall'estensione manifest. Ad esempio, un manifesto dell'applicazione che fa riferimento alla personalizzazione OutlookAddIn1.dll userà la sintassi del nome file seguente.  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  