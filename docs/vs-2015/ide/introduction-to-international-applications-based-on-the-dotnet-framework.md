---
title: Introduzione alle applicazioni internazionali basate su .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 64bdf03401c89ccf7b5731fc4126561ea975325b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530809"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Introduzione alle applicazioni internazionali basate su .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la creazione di applicazioni predisposte per l'internazionalizzazione è composta da due parti: globalizzazione, ovvero il processo di progettazione di applicazioni in grado di adattarsi a impostazioni cultura diverse, e localizzazione, ovvero il processo di conversione di risorse per impostazioni cultura specifiche. Per informazioni generali sulla progettazione di applicazioni per utenti internazionali, vedere [Procedure consigliate per lo sviluppo di applicazioni internazionali](http://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).  
  
 Il modello di localizzazione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] è costituito da un assembly principale che contiene il codice dell'applicazione e le risorse di fallback, ovvero stringhe, immagini e altri oggetti per il linguaggio in cui è sviluppata l'applicazione originale. Ogni applicazione localizzata avrà assembly satellite o assembly che contengono solo le risorse localizzate. Poiché l'assembly principale contiene sempre le risorse di fallback, se la risorsa non viene trovata nell'assembly satellite localizzato, <xref:System.Resources.ResourceManager> proverà a caricarlo in maniera gerarchica, usando la risorsa dell'assembly principale. Il sistema di fallback delle risorse è illustrato più dettagliatamente in [Organizzazione gerarchica di risorse per la localizzazione](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Una risorsa di localizzazione da considerare è il glossario di tutti i prodotti Microsoft localizzati. Questo file CSV contiene più di 12.000 termini inglesi e le traduzioni dei termini in 59 lingue diverse. Il glossario è disponibile per il download nella pagina Web [Microsoft Terminology Translations](http://go.microsoft.com/fwlink/?LinkId=128146).  
  
 Il sistema di progetto per applicazioni Windows Form può generare file di risorse per il fallback e per le impostazioni cultura dell'interfaccia utente aggiuntive. Il file di risorse di fallback viene compilato nell'assembly principale e i file di risorse specifiche delle impostazioni cultura vengono quindi compilati in assembly satellite, separati individualmente per impostazioni cultura dell'interfaccia utente. Quando si compila un progetto, i file di risorse vengono compilati dal formato XML di Visual Studio (con estensione RESX) in un formato binario intermedio (con estensione resources) e incorporati in assembly satellite.  
  
 Il sistema di progetto per Windows Form e Web Form consente di compilare file di risorse usando un modello di file di risorse Assembly, accedere alle risorse e compilare il progetto. Gli assembly satellite vengono creati insieme all'assembly principale.  
  
 Quando viene eseguita un'applicazione localizzata, il suo aspetto è determinato da due valori di impostazioni cultura. (Le *impostazioni cultura* sono un set di informazioni sulle preferenze relative alle convenzioni culturali, ambientali e linguistiche dell'utente). Le impostazioni cultura dell'interfaccia utente determinano le risorse che verranno caricate. Le impostazioni cultura dell'interfaccia utente vengono impostate come `UICulture` nei file Web.config e nelle direttive della pagina e come <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> nel codice di Visual Basic o Visual C#. Le impostazioni cultura determinano la formattazione di valori quali numeri, date, valute e così via. Le impostazioni cultura vengono impostate come `Culture` nei file Web.config e nelle direttive della pagina, come <xref:System.Globalization.CultureInfo.CurrentCulture%2A> nel codice di Visual Basic o Visual C#.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)   
 [Sicurezza e assembly satellite localizzati](../ide/security-and-localized-satellite-assemblies.md)

