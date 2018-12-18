---
title: 'Procedura: specificare i file da pubblicare mediante ClickOnce | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: eee0e88b23a26ae7a89005ff304b565dd3d84c34
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Procedura: specificare i file da pubblicare mediante ClickOnce
Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i file dell'applicazione, tutti non di codice nel progetto vengono distribuiti insieme all'applicazione. In alcuni casi, non si desidera oppure la pubblicazione di determinati file o che si desidera installare determinati file in base alle condizioni. Visual Studio fornisce le funzionalità per escludere i file, contrassegnare i file come file di dati o i prerequisiti e creare gruppi di file per l'installazione condizionale.  
  
 I file per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione vengono gestite nel **file dell'applicazione** la finestra di dialogo, accessibile dal **pubblica** pagina del **Progettazione progetti**.  
  
 Inizialmente, è presente un unico gruppo di file denominato **(obbligatorio)**. È possibile creare gruppi di file aggiuntive e assegnare loro i file. Non è possibile modificare il **gruppo di Download** per i file necessari per eseguire l'applicazione. Ad esempio, .exe dell'applicazione o file contrassegnato come file di dati devono appartenere al **(obbligatorio)** gruppo.  
  
 Il valore predefinito di stato di pubblicazione valore di un file è contrassegnato con **(Auto)**. Ad esempio, .exe dell'applicazione ha lo stato di pubblicazione **Includi (automatico)** per impostazione predefinita.  
  
 I file con il **azione di compilazione** proprietà impostata su **contenuto** sono designati come file dell'applicazione e verrà contrassegnato come inclusi per impostazione predefinita. Possono essere inclusi, esclusi o contrassegnati come file di dati. Le eccezioni sono i seguenti:  
  
-   File di dati, ad esempio file XML e file di Database SQL (con estensione mdf e mdb) verranno contrassegnati come file di dati per impostazione predefinita.  
  
-   I riferimenti agli assembly (file con estensione dll) vengono designati come indicato di seguito quando si aggiunge il riferimento: se **Copia localmente** è **False**, è contrassegnato per impostazione predefinita come assembly prerequisiti (**(prerequisiti Auto)**) che deve essere presente nella Global Assembly Cache prima di installare l'applicazione. Se **Copia localmente** è **True**, l'assembly viene contrassegnato per impostazione predefinita come assembly dell'applicazione (**Includi (automatico)**) e verrà copiato nella cartella dell'applicazione al momento dell'installazione. Un riferimento COM verrà visualizzato nel **file dell'applicazione** finestra di dialogo casella (come file ocx) solo se il relativo **Isolated** è impostata su **True**. Per impostazione predefinita, verrà incluso.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Per aggiungere i file nella finestra di dialogo file applicazione  
  
1.  Selezionare un file di dati in **Esplora**.  
  
2.  Nella finestra Proprietà modificare il **azione di compilazione** proprietà per il **contenuto** valore.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Consente di escludere file dalla pubblicazione ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **file dell'applicazione** pulsante per aprire la **file dell'applicazione** la finestra di dialogo.  
  
4.  Nel **file dell'applicazione** finestra di dialogo, selezionare il file che si desidera escludere.  
  
5.  Nel **stato pubblicazione** campi, selezionare **escludere** dall'elenco a discesa.  
  
### <a name="to-mark-files-as-data-files"></a>Per contrassegnare i file come file di dati  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **file dell'applicazione** pulsante per aprire la **file dell'applicazione** la finestra di dialogo.  
  
4.  Nel **file dell'applicazione** finestra di dialogo, selezionare il file che si desidera contrassegnare come dati.  
  
5.  Nel **stato pubblicazione** campi, selezionare **File di dati** dall'elenco a discesa.  
  
### <a name="to-mark-files-as-prerequisites"></a>Per contrassegnare i file come prerequisiti  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **file dell'applicazione** pulsante per aprire la **file dell'applicazione** la finestra di dialogo.  
  
4.  Nel **file dell'applicazione** finestra di dialogo, selezionare l'assembly dell'applicazione (file con estensione dll) che si desidera contrassegnare come prerequisito. Si noti che l'applicazione deve includere un riferimento all'assembly dell'applicazione affinché venga visualizzato nell'elenco.  
  
5.  Nel **stato pubblicazione** campi, selezionare **prerequisiti** dall'elenco a discesa.  
  
### <a name="to-add-a-new-file-group"></a>Per aggiungere un nuovo gruppo di file  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **file dell'applicazione** pulsante per aprire la **file dell'applicazione** la finestra di dialogo.  
  
4.  Nel **file dell'applicazione** la finestra di dialogo, seleziona il **gruppo** field per un file che si desidera includere nel nuovo gruppo.  
  
    > [!NOTE]
    >  I file devono avere la **azione di compilazione** proprietà impostata su **contenuto** prima che i nomi di file visualizzati nel **file dell'applicazione** la finestra di dialogo.  
  
5.  Nel **gruppo di Download** campi, selezionare  **\<nuovo … >** dall'elenco a discesa.  
  
6.  Nel **nuovo gruppo** nella finestra di dialogo immettere un nome per il gruppo e quindi fare clic su **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>Per aggiungere un file a un gruppo  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **file dell'applicazione** pulsante per aprire la **file dell'applicazione** la finestra di dialogo.  
  
4.  Nel **file dell'applicazione** la finestra di dialogo, seleziona il **gruppo** field per un file che si desidera includere nel nuovo gruppo.  
  
5.  Nel **gruppo di Download** campo, selezionare un gruppo dall'elenco a discesa.  
  
    > [!NOTE]
    >  Non è possibile modificare il **gruppo di Download** per i file necessari per eseguire l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)