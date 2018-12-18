---
title: '&lt;compatibleFrameworks&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d406ecf058bf1c570b57ed8f50815cc3d9378cbe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; elemento (distribuzione di ClickOnce)
Identifica le versioni di .NET Framework in cui è possibile installare ed eseguire questa applicazione.  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) non supporta il `compatibleFrameworks` elemento durante il salvataggio di un manifesto dell'applicazione che è già stato firmato con un certificato utilizzando [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). È invece necessario usare [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
## <a name="syntax"></a>Sintassi  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `compatibleFrameworks` elemento è obbligatorio per manifesti di distribuzione che hanno come destinazione il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] runtime fornite da [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o versione successiva. Il `compatibleFrameworks` elemento contiene uno o più `framework` elementi che specificano le versioni di .NET Framework in cui è possibile eseguire questa applicazione. Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione verrà eseguita nella prima fase di esecuzione disponibili `framework` in questo elenco.  
  
 La tabella seguente elenca l'attributo che il `compatibleFrameworks` supportato dall'elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`S` `upportUrl`|Facoltativo. Specifica un URL in cui può essere scaricata la versione di .NET Framework compatibile preferita.|  
  
## <a name="framework"></a>framework  
 Obbligatorio. Nella tabella seguente vengono elencati gli attributi che il `framework` supportato dall'elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`targetVersion`|Obbligatorio. Specifica il numero di versione di .NET Framework di destinazione.|  
|`profile`|Obbligatorio. Specifica il profilo di .NET Framework di destinazione.|  
|`supportedRuntime`|Obbligatorio. Specifica il numero di versione del runtime di .NET Framework di destinazione associato.|  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un `compatibleFrameworks` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione. Questa distribuzione è possibile eseguire di [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Inoltre possibile eseguire su di [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] perché è un superset del [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)