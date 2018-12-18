---
title: Estensibilità di servizio di linguaggio legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7d8165060fa3b9a6445ad71a977c79414056f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-extensibility"></a>Estensibilità di servizio di linguaggio legacy
Un servizio di linguaggio fornisce il supporto di specifiche della lingua per la modifica del codice sorgente nell'IDE.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul programma per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
 Questa sezione illustra la struttura e l'implementazione di un servizio di linguaggio legacy.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Migrazione di un servizio di linguaggio Legacy](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Viene illustrato come aggiornare un servizio di linguaggio da Visual Studio 2008 alla versione più recente.  
  
 [Nozioni fondamentali sui servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-essentials.md)  
 Vengono fornite importanti informazioni sullo sviluppo di servizi di linguaggio per integrare un linguaggio di programmazione in Visual Studio.  
  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio.  
  
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fornisce informazioni sul supporto di evidenziazione della sintassi in un servizio di linguaggio.  
  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fornisce informazioni su come utilizzare il framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.  
  
 [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Descrive le librerie e strumenti che consentono di sfogliare le viste di struttura ad albero di simboli nell'IDE.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
 Viene fornita una panoramica dell'editor di Visual Studio.  
  
 [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Fornisce informazioni e un collegamento a Visual Studio Debugging SDK, che contiene le informazioni necessarie per creare e personalizzare i componenti del debugger per eseguire il debug di programmi.