---
title: 'Procedura: riabilitare un componente aggiuntivo VSTO che è stato disabilitato | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25344d23e0c9f1d6d237d008b0f6b18372490d04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Procedura: Riattivare un componente aggiuntivo VSTO disattivato
  Le applicazioni di Microsoft Office possono disabilitare i componenti aggiuntivi VSTO che si comportano in modo imprevisto. Se un'applicazione non carica un componente aggiuntivo VSTO quando si tenta di eseguirne il debug, il componente aggiuntivo VSTO potrebbe essere stato disabilitato dall'applicazione in seguito alla chiusura dell'applicazione (disabilitazione di tipo "hard") o a un errore del componente (disabilitazione di tipo "soft").  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Componenti aggiuntivi VSTO con disabilitazione di tipo "hard"  
 Questo tipo di disabilitazione può verificarsi quando un componente aggiuntivo VSTO causa la chiusura imprevista dell'applicazione. Si potrebbe verificare anche nel computer di sviluppo se si arresta il debugger durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> nel componente aggiuntivo VSTO.  
  
#### <a name="to-re-enable-a-vsto-add-in"></a>Per riabilitare un componente aggiuntivo VSTO  
  
1.  Nell'applicazione fare clic sulla scheda **File** .  
  
2.  Fare clic su di *ApplicationName* **opzioni** pulsante.  
  
3.  Nel riquadro delle categorie fare clic su **Componenti aggiuntivi**.  
  
4.  Nel riquadro dei dettagli verificare che il componente aggiuntivo VSTO sia visualizzato nell'elenco **Componenti aggiuntivi di applicazioni disattivati** .  
  
     La colonna **Nome** specifica il nome dell'assembly e la colonna **Percorso** specifica il percorso completo del manifesto dell'applicazione.  
  
5.  Nella casella **Gestione** fare clic su **Elementi disattivati**e quindi su **Vai**.  
  
6.  Selezionare il componente aggiuntivo VSTO e fare clic su **Attiva**.  
  
7.  Fare clic su **Chiudi**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Componenti aggiuntivi VSTO con disabilitazione di tipo "soft"  
 La disabilitazione di tipo "soft" può verificarsi quando un componente aggiuntivo VSTO genera un errore che non causa la chiusura imprevista dell'applicazione. Ad esempio, un'applicazione potrebbe eseguire la disabilitazione di tipo "soft" di un componente aggiuntivo VSTO se viene generata un'eccezione non gestita durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> .  
  
> [!NOTE]  
>  Quando si riabilita un componente aggiuntivo VSTO dopo la disabilitazione di tipo "soft", l'applicazione tenta immediatamente di caricare il componente aggiuntivo VSTO. Se il problema che ha inizialmente causato la disabilitazione di tipo "soft" del componente aggiuntivo VSTO non è stato risolto, l'applicazione ne eseguirà di nuovo la disabilitazione di tipo "soft".  
  
#### <a name="to-re-enable-an-vsto-add-in"></a>Per riabilitare un componente aggiuntivo VSTO  
  
1.  Nell'applicazione fare clic sulla scheda **File** .  
  
2.  Fare clic su di *ApplicationName* **opzioni** pulsante.  
  
3.  Nel riquadro delle categorie fare clic su **Componenti aggiuntivi**.  
  
4.  Nel riquadro dei dettagli verificare che il componente aggiuntivo VSTO sia visualizzato nell'elenco **Componenti aggiuntivi di applicazioni inattivi** .  
  
     La colonna **Nome** specifica il nome dell'assembly e la colonna **Percorso** specifica il percorso completo del manifesto dell'applicazione.  
  
5.  Nella casella **Gestione** fare clic su **Componenti aggiuntivi COM**e quindi su **Vai**.  
  
6.  Nella finestra di dialogo **Componenti aggiuntivi COM** selezionare la casella di controllo accanto al componente aggiuntivo VSTO disabilitato.  
  
7.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Debug di progetti di Office](../vsto/debugging-office-projects.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  