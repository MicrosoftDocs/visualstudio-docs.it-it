---
title: 'Procedura: visualizzare la scheda sviluppatore nella barra multifunzione | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9921c10d8a886eb4051b3d5f3d8392ddc77c2da7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Procedura: visualizzare la scheda Sviluppo nella barra multifunzione
  Per l'accesso di **Developer** scheda della barra multifunzione di un'applicazione di Office, è necessario configurare in modo da visualizzare tale scheda, appare per impostazione predefinita. Ad esempio, è necessario visualizzare tale scheda per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalizzazione a livello di documento per Word.  
  
> [!NOTE]  
>  Questo materiale sussidiario si applica solo alle applicazioni di Office 2010 o versioni successive. Se si desidera visualizzare questa scheda in Microsoft Office System 2007, vedere la seguente versione di questo argomento [procedura: visualizzare la scheda sviluppatore nella barra multifunzione](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Access non ha un **Developer** scheda.  
  
### <a name="to-show-the-developer-tab"></a>Per visualizzare la scheda Sviluppo  
  
1.  Avviare un'applicazione Office supportata da questo argomento. Vedere il **si applica a:** nota in precedenza in questo argomento.  
  
2.  Nel **File** scheda, scegliere il **opzioni** pulsante.  
  
     La figura seguente mostra il **File** scheda e **opzioni** pulsante in Office 2010.  
  
     ![Scegliere File, le opzioni di Outlook 2010](../vsto/media/vsto-office-file-tab.png "scegliere File, le opzioni di Outlook 2010")  
  
     La figura seguente mostra il **File** scheda in Office 2013.  
  
     ![Scheda File in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "scheda del File in Outlook 2013")  
  
     La figura seguente mostra il **opzioni** pulsante in Office 2013.  
  
     ![Pulsante Opzioni di Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "pulsante Opzioni di Outlook 2013 Preview")  
  
3.  Nel *ApplicationName * * * le opzioni** finestra di dialogo, scegliere il **Personalizzazione barra multifunzione** pulsante.  
  
     La figura seguente mostra il **opzioni** la finestra di dialogo e **Personalizzazione barra multifunzione** pulsante in Excel 2010. La posizione di questo pulsante è simile in tutte le altre applicazioni elencate nella sezione "Applica a" quasi all'inizio di questo argomento.  
  
     ![Pulsante Personalizzazione barra multifunzione](../vsto/media/vsto-office2010-customizeribbonbutton.png "pulsante di personalizzazione barra multifunzione")  
  
4.  Nell'elenco di schede principali selezionare la **Developer** casella di controllo.  
  
     La figura seguente mostra il **Developer** casella di controllo in Word 2010 e [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. La posizione di questa casella di controllo è simile in tutte le altre applicazioni elencate nella sezione "Si applica a" quasi all'inizio di questo argomento.  
  
     ![La casella di controllo sviluppatore nella finestra di dialogo Opzioni di Word](../vsto/media/vsto-office2010-developercheckbox.png "Developer la casella di controllo nella finestra di dialogo Opzioni di Word")  
  
5.  Scegliere il **OK** per chiudere la **opzioni** la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)  
  
  