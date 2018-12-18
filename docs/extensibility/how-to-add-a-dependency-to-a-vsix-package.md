---
title: 'Procedura: aggiungere una dipendenza a un pacchetto VSIX | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 27fbf8c079ca1270074d7cae683ef6f8127e2a5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: aggiungere una dipendenza a un pacchetto VSIX

È possibile configurare una distribuzione di pacchetto VSIX che installa tutte le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze del progetto VSIX per il file vsixmanifest.

## <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza

1. Aprire il file vsixmanifest nel **progettazione** visualizzazione. Passare al **dipendenze** scheda e fare clic su **New**.

2. Per aggiungere un'estensione installata: nel **aggiungere nuove dipendenze** nella finestra di dialogo **estensione installata** e quindi, per il **nome**, selezionare un'estensione nell'elenco.

3. Per aggiungere un altro progetto VSIX che non è installato:: nel **aggiungere nuove dipendenze** nella finestra di dialogo **File nel file system** e quindi usare il **Sfoglia** per selezionare il progetto VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Richiede una versione specifica di Visual Studio

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio, una funzionalità rilasciata in 15.3 dipende, è possibile specificare il numero di build in un progetto VSIX del **la destinazione di installazione**. Ad esempio, versione 15.3 presenta un numero di build di '15.0.26730.3'. È possibile visualizzare il mapping delle versioni per i numeri di build [qui](../install/visual-studio-build-numbers-and-release-dates.md). Si noti che tramite il numero di versione '15.3' non funzionerà correttamente.

Se l'estensione richiede 15.3 o versioni successive, è necessario dichiarare il **la destinazione di installazione versione** come [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Il VSIXInstaller rileverà le versioni precedenti di Visual Studio e informare l'utente che è necessario un aggiornamento successivo.


## <a name="see-also"></a>Vedere anche

 [Riferimento dello Schema 1.0 dell'estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md) [preparazione estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)