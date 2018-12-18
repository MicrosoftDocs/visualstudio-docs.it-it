---
title: Procedure consigliate per la sicurezza in VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 689c85e090e44612a87474e8c77dc0e146706e84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedure consigliate per la sicurezza in VSPackage
Per installare il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nel computer in uso, è necessario essere in esecuzione in un contesto con credenziali amministrative. L'unità di base della sicurezza e la distribuzione di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] applicazione è il [VSPackage](../../extensibility/internals/vspackages.md). Un pacchetto VSPackage deve essere registrato tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], che richiede credenziali amministrative.  
  
 Gli amministratori dispongono delle autorizzazioni complete per scrivere il Registro di sistema e file system e per eseguire qualsiasi codice. È necessario sviluppare, distribuire o installare un pacchetto VSPackage di tali autorizzazioni.  
  
 Non appena viene installato, un VSPackage è completamente attendibile. A causa di questo livello elevato di autorizzazione associata a un pacchetto VSPackage, è possibile installare inavvertitamente un VSPackage che malintenzionati.  
  
 Gli utenti devono assicurarsi che installano i pacchetti VSPackage solo da origini attendibili. Società di sviluppo di VSPackages fortemente deve assegnare un nome e le firmerà, per garantire l'utente che manomissioni non è consentita. Sviluppo di VSPackages società deve esaminare le dipendenze esterne, ad esempio servizi web e l'installazione remota, valutare e correggere eventuali problemi di sicurezza.  
  
 Per altre informazioni, vedere linee guida per la generazione di codice sicuro per .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Vedere anche  
 [Componente aggiuntivo di sicurezza](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Sicurezza DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)