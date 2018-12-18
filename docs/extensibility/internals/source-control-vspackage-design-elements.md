---
title: Gli elementi di progettazione di VSPackage di controllo di origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 234346aba360d70d3bbc673067d2634a5112d0f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-design-elements"></a>Elementi di progettazione di VSPackage di controllo di origine
Negli argomenti di questa sezione descrivono la struttura di controllo del codice sorgente pacchetto VSPackage deve implementare per l'integrazione completa. Elenca inoltre le interfacce e i servizi che il controllo origine VSPackage possono implementare le interfacce e i servizi è possibile utilizzare il controllo del codice sorgente VSPackage dagli altri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti per supportare la relativa origine controllano modello e la funzionalità.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Struttura di VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definisce la struttura del controllo origine pacchetto VSPackage.  
  
 [Le interfacce e i servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Elenca i servizi e interfacce correlate al pacchetto di origine controllo.  
  
 [Servizi forniti](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Viene descritto il servizio di controllo di origine specificato per il controllo del codice sorgente VSPackage.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Viene illustrato come creare un controllo del codice sorgente VSPackage che non solo fornisce controllo del codice sorgente ma può essere utilizzato per personalizzare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente di controllo del codice sorgente.