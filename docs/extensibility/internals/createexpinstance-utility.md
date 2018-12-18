---
title: Utilità CreateExpInstance | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdcb37374c63b96e2169de28c6fe21742024ca98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="createexpinstance-utility"></a>Utilità CreateExpInstance
Utilizzare l'utilità CreateExpInstance di creare, reimpostare, o eliminare un'istanza sperimentale di Visual Studio. È possibile utilizzare l'istanza sperimentale per eseguire il debug e testare le estensioni di Visual Studio senza modificare il prodotto sottostante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parametri  
 / Create  
 Crea l'istanza sperimentale.  
  
 / Reset  
 Elimina l'istanza sperimentale e quindi crea uno nuovo.  
  
 /Clean  
 Elimina l'istanza sperimentale.  
  
 /Vsinstance  
 Il nome della directory che contiene l'istanza di Visual Studio di base da copiare.  
  
 /Rootsuffix  
 Il suffisso da aggiungere al nome della directory istanza sperimentale.  
  
## <a name="remarks"></a>Note  
 Quando si lavora in un'estensione di Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se nessuna istanza sperimentale è disponibile, Visual Studio viene creata una con le impostazioni predefinite.  
  
 Il percorso predefinito dell'istanza sperimentale dipende dal numero di versione di Visual Studio. Per Visual Studio 2015, ad esempio, il percorso è %localappdata%\Microsoft\VisualStudio\14.0Exp\ tutti i file nel percorso della directory sono considerati parte dell'istanza. Qualsiasi istanza sperimentale aggiuntiva non verrà caricato da Visual Studio a meno che non viene modificato il nome della directory nel percorso predefinito.  
  
 Visual Studio non accede al Registro di sistema quando si apre l'istanza sperimentale. Questo comportamento è diverso da versioni precedenti di Visual Studio, che è utilizzata una versione sperimentale di hive del Registro di sistema.  
  
 L'utilità CreateExpInstance sostituisce l'utilità VsRegEx.  
  
 Nell'esempio seguente consente di reimpostare l'istanza sperimentale predefinita di Visual Studio.  
  
 **CreateExpInstance.exe exe /Reset/vsinstance=14.0 = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)