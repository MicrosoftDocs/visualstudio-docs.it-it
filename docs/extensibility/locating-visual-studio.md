---
title: Individuazione di Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 08/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5623ea382266fdbcd59bbe57b71522a7a1f4a31e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="locating-visual-studio"></a>Individuazione di Visual Studio

A partire da Visual Studio 2017, è possibile installare più istanze della stessa versione o edizione anche. Ciò è utile quando si desidera visualizzare in anteprima mantenendo una precedente installazione di nuove funzionalità nel computer di sviluppo primario. A causa di queste modifiche, è presente alcun valore di variabile o del Registro di sistema di unico ambiente che è possibile utilizzare per individuare un'istanza. In alternativa, è possibile utilizzare un [query COM API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) di individuare le istanze in base a criteri appropriati per l'estensione.

Si tratta di una API rapida, di sola lettura con pacchetti NuGet disponibile per codice gestito e nativo.

| Codice | Pacchetto |
| ---- | --- |
| Nativo | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.native |
| Gestito | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

È possibile individuare una singola istanza di un percorso o il processo corrente specificata o enumerare tutte le istanze. Vedere [esempi](https://github.com/Microsoft/vs-setup-samples) per esempi completi di individuare Visual Studio.

## <a name="tools"></a>Strumenti

Per trovare Visual Studio e altri strumenti in ambienti di compilazione, script di PowerShell, programmi di installazione e più scenari, sono disponibili numerosi strumenti open source, è possibile utilizzare direttamente o ridistribuire insieme gli script personalizzati.

| Progetto | Descrizione |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Singolo file eseguibile nativo per individuare le istanze che soddisfano i criteri, ad esempio o versione non definitiva, il prodotto sia installato e la versione vengono installati i carichi di lavoro. Supporta anche la ricerca di Visual Studio 2010 e versioni successive, anche se viene restituiti che meno informazioni per Visual Studio 2017 e più recenti. Vedere il [wiki](https://github.com/Microsoft/vswhere/wiki) per gli esempi. |
| [Cmdlet VSSetup](https://github.com/Microsoft/vssetup.powershell) | Cmdlet di PowerShell supportati 2.0 e versioni più recenti che restituiscono informazioni dettagliate come oggetti di consente di individuare le istanze in base agli stessi criteri _vswhere_ e per scoprire ulteriori proprietà sulle istanze. Vedere il [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) per gli esempi. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Individua automaticamente _VSIXInstaller_ e passa la riga di comando e per installare un _*. VSIX_ file. Può essere utile per i programmi di installazione che non contengono supporto diretto per l'API di query. Vedere il [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) per gli esempi. |

## <a name="see-also"></a>Vedere anche

* [Modifiche per l'installazione di Visual Studio 2017](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
