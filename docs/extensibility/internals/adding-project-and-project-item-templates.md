---
title: Aggiunta di progetto e modelli di elemento di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94d521d288b470db56736668f11d47dab71d2533
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-project-and-project-item-templates"></a>Aggiunta di progetto e i modelli di progetto
Quando si creano tipi di progetto, è necessario fornire il supporto per l'aggiunta di nuovi progetti ed elementi di progetto con lo standard [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestre di dialogo (IDE) di ambiente di sviluppo integrato. Negli argomenti seguenti vengono illustrano diverse tecniche per l'aggiunta di progetti ed elementi di progetto.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Contesto di progetto](../../extensibility/internals/project-context.md)  
 Viene illustrato che il progetto non offre la maggior parte delle informazioni di contesto per ciò che accade realmente nell'ambiente.  
  
 [Priorità di progetto](../../extensibility/internals/project-priority.md)  
 Viene illustrato un elemento di progetto è in genere un membro di un progetto per evitare ambiguità sulle progetto viene utilizzato per aprire l'elemento.  
  
 [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)  
 Vengono fornite informazioni sui due tipi di editor che può essere utilizzato per aprire i file in un progetto e il ruolo viene riprodotto il progetto per determinare quale editor da utilizzare quando si apre un elemento di progetto.  
  
 [Registrazione di modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)  
 Viene spiegato cosa accade quando un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creazione del progetto.  
  
 [Aggiunta di elementi nelle finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Viene illustrato il processo per l'aggiunta di elementi di **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 [Aggiunta di directory nella finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fornisce un esempio di registrazione di una nuova directory che contiene i modelli personalizzati resi disponibili da un pacchetto VSPackage.  
  
 [Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Viene fornito un esempio di registrazione di un nuovo set di directory per il **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Elenca i diversi tipi di elementi di comando utilizzati per estendere i sistemi di progetto.  
  
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Elenca i CATID per gli oggetti che vengono utilizzati per estendere [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemi di progetto.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un elemento intrinsecamente associato a un editor specifico per un progetto.  
  
 [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un editor standard.  
  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)  
 Fornisce i collegamenti agli argomenti concettuali sottotipo del progetto. Sottotipi di progetto estendono esistente [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetti.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.