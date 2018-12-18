---
title: Gestione dei pacchetti VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9e3241bae84b89b53e30c3d0949e4f8551110e7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="managing-vspackages"></a>Gestione dei pacchetti VSPackage
Nella maggior parte dei casi non è necessario preoccuparsi di gestione dei pacchetti VSPackage, poiché i modelli di progetto e di elemento di registrare e caricare automaticamente il pacchetto. Tuttavia, in alcuni casi potrebbe essere necessario apprendere un po' più per gestire il pacchetto.  
  
## <a name="using-the-experimental-instance"></a>Utilizzando l'istanza sperimentale  
 Per altre informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrazione e annullamento della registrazione VSPackage  
 Per sapere come registrare e annullare la registrazione di pacchetti VSPackage e altri tipi di estensione, vedere [registrazione e annullamento della registrazione VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Il caricamento di un pacchetto VSPackage  
 VSPackage possono essere impostati su autoload quando una particolare che CMDUICONTEXT GUID è attivata. Per ulteriori informazioni, vedere [VSPackage durante il caricamento](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Utilizzo di AsyncPackage per caricare pacchetti VSPackage in Background  
 La classe AsyncPackage consente pacchetto durante il caricamento in un thread in background per una migliore velocità di risposta dell'interfaccia utente in Visual Studio. Per ulteriori informazioni, vedere [procedura: utilizzare AsyncPackage ai pacchetti VSPackage di caricamento in Background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basata su regole per le estensioni  
 Contesti di interfaccia utente basata su regole consente agli autori di estensione definire le condizioni esatte in cui viene attivato un contesto dell'interfaccia utente e caricato VSPackage associati. Per ulteriori informazioni, vedere [come: basato su regole di utilizzo di contesto dell'interfaccia utente per le estensioni di Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>La diagnosi delle prestazioni di estensione  
Le estensioni possono influire soluzione e avvio del caricamento. Informazioni su modalità di calcolo impatto di estensione di Visual Studio e come è possibile analizzare in locale per verificare se un'estensione può essere visualizzata come estensione conseguenze sulle prestazioni. Per ulteriori informazioni, vedere [procedura: diagnosticare le prestazioni di estensione](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi di VSPackage  
 Scoprire le tecniche per la risoluzione dei problemi relativi a pacchetti VSPackage che non vengono caricati o segnalano errori: [VSPackage di risoluzione dei problemi](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)