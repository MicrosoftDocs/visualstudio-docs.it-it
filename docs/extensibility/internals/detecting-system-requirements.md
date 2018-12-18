---
title: Rilevamento dei requisiti di sistema | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e98235bd224876b00714e1f71210ea69cb6faff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="detecting-system-requirements"></a>Rilevamento dei requisiti di sistema
Un VSPackage non funzionerà a meno che non è installato Visual Studio. Quando si utilizza Microsoft Windows Installer per gestire l'installazione di un VSPackage, è possibile configurare il programma di installazione per rilevare se è installato Visual Studio. È anche possibile configurare per controllare il sistema e altri requisiti, ad esempio, una particolare versione di Windows o una determinata quantità di RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Il rilevamento delle edizioni di Visual Studio  
 Per determinare se è installata un'edizione di Visual Studio, verificare che il valore della chiave del Registro di sistema di installazione sia (REG_DWORD) 1 nella cartella appropriata, come indicato nella tabella seguente. Si noti che esiste una gerarchia delle edizioni di Visual Studio:  
  
1.  Enterprise  
  
2.  Professionale  
  
3.  Community  
  
 Quando si installa un'edizione "higher", vengono aggiunte le chiavi del Registro di sistema per questa edizione anche per le edizioni "lower". Ovvero, se è installata la versione Enterprise edition, la chiave di installazione è impostata su 1 per l'organizzazione, nonché per le edizioni Professional e Community. È pertanto necessario controllare solo per l'edizione "massimo", che è necessario.  
  
> [!NOTE]
>  Nella versione a 64 bit dell'editor del Registro di sistema, vengono visualizzate le chiavi di 32 bit in HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Le chiavi di Visual Studio sono in HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Prodotto|Chiave|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrato e isolata)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Rilevare quando è in esecuzione Visual Studio  
 Il pacchetto VSPackage non può essere registrato correttamente se Visual Studio è in esecuzione quando viene installato il pacchetto VSPackage. Il programma di installazione deve rilevare quando è in esecuzione Visual Studio e quindi rifiutare l'installazione del programma. Windows Installer non è possibile utilizzare le voci della tabella per abilitare questo rilevamento. In alternativa, è necessario creare un'azione personalizzata, come indicato di seguito: utilizzo di `EnumProcesses` funzione per rilevare il processo devenv.exe e quindi impostare una proprietà di installazione che viene utilizzata in una condizione di avvio o in modo condizionale consente di visualizzare una finestra di dialogo che chiede all'utente di chiudere Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)