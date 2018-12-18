---
title: Sito Web di supporto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09b43963d657e8d1fe7aa24e98632d2ca46240c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support"></a>Sito Web di supporto
Un sistema di progetto di sito Web è un sistema di progetto che consente di creare progetti Web. Progetti Web consentono di creare applicazioni Web. Un progetto di sito Web genera un file eseguibile per ogni pagina Web che contiene il codice associato. File eseguibile aggiuntivi vengono generati dal file di codice sorgente nella cartella /App_Code.  
  
 Sistemi di progetto di sito Web vengono creati tramite l'aggiunta di modelli e gli attributi di registrazione in un sistema di progetto esistente. Uno di questi attributi seleziona il provider di IntelliSense per la lingua. L'implementazione del provider IntelliSense gestisce riferimenti e il compilatore di linguaggio viene chiamato quando viene richiesta una pagina Web smart non memorizzato nella cache.  
  
 Il compilatore di linguaggio utilizzato per compilare le pagine Web deve essere registrato con [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. È possibile utilizzare il [ \<compilatore > elemento](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) in un file Web. config per registrare il compilatore, come nell'esempio seguente:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>In questa sezione  
 [Modelli di supporto per siti Web](../../extensibility/internals/web-site-support-templates.md)  
 Vengono elencati i modelli che è possibile utilizzare per creare nuovi progetti di sito Web e gli elementi associati.  
  
 [Attributi di supporto per siti Web](../../extensibility/internals/web-site-support-attributes.md)  
 Presenta gli attributi di registrazione che si connettono a un progetto di sito Web [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Progetti Web](../../extensibility/internals/web-projects.md)  
 Viene presentata una panoramica dei due tipi di progetti Web, progetti di siti Web e progetti di applicazione Web.