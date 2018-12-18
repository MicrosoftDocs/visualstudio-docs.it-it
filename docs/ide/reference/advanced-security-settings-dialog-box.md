---
title: Finestra di dialogo Impostazioni di sicurezza avanzate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1dad7843d42aeaf0c2871f8b76c840a12cd4186
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-security-settings-dialog-box"></a>Finestra di dialogo Impostazioni di sicurezza avanzate
Questa finestra di dialogo consente di specificare le impostazioni di sicurezza correlate al debug nell'area di sicurezza.  
  
 Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Sicurezza**. Nella pagina **Sicurezza** selezionare **Abilita impostazioni di sicurezza ClickOnce**, fare clic su **È un'applicazione con attendibilità parziale**, quindi fare clic su **Avanzate**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Esegui debug dell'applicazione con il set di autorizzazioni selezionato**  
 Se si seleziona questa casella di controllo, durante il debug verrà usato il set di autorizzazioni selezionato nella pagina **Sicurezza**. Questa opzione è selezionata per impostazione predefinita.  
  
 Per il corretto funzionamento del debug in un'area di sicurezza è necessario abilitare questa opzione e l'opzione **Abilita processo di hosting di Visual Studio**, disponibile nella pagina **Debug** di **Creazione progetti**.  
  
 Per i progetti Applicazione Web browser WPF, l'opzione **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** è selezionata e disabilitata.  
  
 **Concedi all'applicazione accesso al proprio sito di origine**  
 Se si seleziona questa casella di controllo, l'applicazione può accedere al sito Web o alla condivisione server in cui è pubblicata. Questa opzione è selezionata per impostazione predefinita.  
  
 **Esegui debug dell'applicazione come se fosse stata scaricata dal seguente URL**  
 Se è necessario consentire all'applicazione di accedere al sito Web o alla condivisione server corrispondente all'**URL di installazione** specificato nella pagina **Pubblica**, digitare qui l'URL. Questa opzione è disponibile solo se la casella di controllo **Concedi all'applicazione accesso al proprio sito di origine** è selezionata.  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina Sicurezza, Creazione progetti](../../ide/reference/security-page-project-designer.md)