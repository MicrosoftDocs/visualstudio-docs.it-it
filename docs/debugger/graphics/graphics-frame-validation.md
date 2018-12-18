---
title: Frame di grafica convalida | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9732cd3f3440448e5096e71f838d8ebcf20fb13
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-frame-validation"></a>Convalida di Frame di grafica
<!-- VERSIONLESS -->
Visual Studio 2017 e maggiore supporto di **convalida Frame** strumento.  Nella finestra cornice convalida gli errori e avvisi associati all'elenco di eventi.  Per visualizzare questa finestra, selezionare il **Vista > convalida Frame** menu.

![Convalida di frame](media/gfx_diag_frame_validation.png)

Fare clic su di **Esegui convalida** pulsante nell'angolo superiore sinistro per avviare l'analisi.  Potrebbe richiedere alcuni minuti a seconda della complessità del frame.  I dati che viene visualizzato di seguito è una combinazione di due origini: i messaggi che D3D stesso genera quando [livelli SDK](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx) è abilitata e i dati raccolti dallo stato interno dello strumento di rilevamento. Al termine dell'operazione, si noterà diverse colonne di dati:

**Colonna**|**Descrizione**
---|---
ID evento | ID che viene eseguito il mapping a una voce di [elenco eventi](graphics-event-list.md) finestra.
Gravità | Danneggiamento, errore, avviso, informazioni o messaggio.
Category | Applicazione definito, varie, l'inizializzazione, pulizia, compilazione, creazione dello stato, impostazione dello stato, recupero dello stato, esecuzione, la modifica di risorse, Shader, ridondanti e inutilizzate.
Messaggio | Il messaggio associato all'evento.
event | L'evento associato a errore o dell'avviso.

## <a name="see-also"></a>Vedere anche  
[Diagnostica della grafica (debug grafica DirectX)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->