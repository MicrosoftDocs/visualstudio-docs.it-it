---
title: Riferimento (acquisizione a livello di codice) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3755dbb95dc220d070219fbac4a03885d5ed0158
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="reference-programmatic-capture"></a>Riferimento (acquisizione a livello di codice)
Diagnostica grafica supporta il controllo a livello di programmazione sulle funzionalità di acquisizione, tramite l'API di acquisizione a livello di programmazione. È possibile utilizzare questa API per attivare o disattivare e aggiungere messaggi alla diagnostica grafica HUD (Head-Up Display), inizializzare e creare file di log di grafica e acquisire informazioni grafiche.  
  
## <a name="programmatic-capture-apis"></a>API di acquisizione a livello di programmazione  
  
### <a name="classes"></a>Classi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[VsgDbg Class](vsgdbg-class.md)|Rappresenta l'interfaccia attraverso cui il componente in-app di diagnostica della grafica è controllato a livello di programmazione.|  
  
### <a name="preprocessor-symbols"></a>Simboli del preprocessore  
  
|nome|Descrizione|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definisce il nome file predefinito del file di log di grafica.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Quando presente, definisce se viene fornita un'istanza predefinita della classe `VsgDbg`.|  
  
## <a name="related-articles"></a>Articoli correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Capturing Graphics Information](capturing-graphics-information.md)|Viene indicato come acquisire informazioni grafiche dall'app basata su DirectX per poter usare gli strumenti di diagnostica grafica [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per diagnosticare problemi di rendering.|  
|[Panoramica](overview-of-visual-studio-graphics-diagnostics.md)|Viene indicato come la diagnostica della grafica consente di eseguire il debug degli errori di rendering nei giochi e nelle app DirectX.|