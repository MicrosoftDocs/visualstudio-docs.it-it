---
title: Comando, gruppo e il posizionamento della barra degli strumenti predefiniti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0753a29e323f18ad40bcc62a70cf8e9b1123b728
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="default-command-group-and-toolbar-placement"></a>Comando predefinito, gruppo e il posizionamento della barra degli strumenti
Per l'uniformità di prodotto e stabilità, l'interfaccia utente visualizza determinati gruppi di comandi per impostazione predefinita, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce le definizioni per i comandi e i gruppi di comandi. I VSPackage è inoltre possono utilizzare i comandi standard e i gruppi di comandi.  
  
 I gruppi di comandi predefiniti rientrano in tre categorie: IDE comandi, i comandi di prodotto e i comandi dell'editor.  
  
## <a name="default-ide-commands"></a>Comandi IDE predefiniti  
 La barra degli strumenti IDE predefinito include comandi condivisi da tutti i prodotti contenuti nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sono inclusi i comandi relativi alle operazioni del progetto generico, ad esempio il **salvare** comando e **Aggiungi elemento** comando. Pacchetti VSPackage non devono aggiungere o sottrarre questa barra degli strumenti, con una sola eccezione: se il prodotto o un pacchetto VSPackage aggiunge una nuova finestra degli strumenti, quindi la finestra deve essere aggiunto all'elenco di finestre degli strumenti disponibili nel **vista** menu. Nuovi prodotti o i pacchetti VSPackage è possono aggiungere i propri sulla barra degli strumenti.  
  
## <a name="default-product-commands"></a>Comandi di prodotto predefiniti  
 Ogni prodotto può fornire l'IDE con il proprio barra degli strumenti predefinita che contiene importanti e comandi utilizzati di frequente. È consigliabile, tuttavia, per utilizzare esistente menu e barre degli strumenti quando possibile e integrare con altre barre degli strumenti attività specifiche in base alle esigenze.  
  
 Il campo priorità per una barra degli strumenti determina la posizione di riga. Zero priorità posiziona la barra degli strumenti nella terza riga (riga 3), sotto la barra dei menu (riga 1) e **Standard** (riga 2) sulla barra degli strumenti. Pertanto, altre barre degli strumenti vengono visualizzati in una riga (priorità + 3). Barre degli strumenti successive vengono posizionate nella stessa riga, se c'è spazio; in caso contrario, vengono automaticamente spostati alla riga successiva.  
  
## <a name="default-editor-commands"></a>Comandi dell'Editor predefinito  
 Un VSPackage che fornisce un editor personalizzato deve fornire una barra degli strumenti predefinita che contiene più importanti e comandi utilizzati di frequente in tale editor. Editor barra degli strumenti dovrebbe essere visualizzato quando l'editor è attivo e deve essere nascosto quando l'editor non è attivo. È possibile controllare la visibilità nel `VisibilityConstraints Element` del file con estensione vsct.  
  
 Barre degli strumenti Editor deve essere posizionati di sotto di barre degli strumenti IDE e del prodotto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gruppi di menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)