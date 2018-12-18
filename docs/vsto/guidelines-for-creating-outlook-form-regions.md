---
title: Linee guida per la creazione di Outlook aree del modulo | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1e82a4428dde7aa25c7e9a3d7d74017b9f2a874f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="guidelines-for-creating-outlook-form-regions"></a>Linee guida per la creazione delle aree di modulo di Outlook
  Le informazioni seguenti consentono di ottimizzare le aree del modulo ed evitare potenziali problemi:  
  
-   [Uso dei nomi delle aree del modulo](#UsingFormRegions).  
  
-   [Disabilitazione dell'ereditarietà dell'area del modulo](#DisablingInheritance).  
  
-   [Informazioni sui tipi e sui nomi delle classi messaggio](#ClassNames).  
  
-   [Progettazione di aree del modulo adiacenti per il riquadro di lettura](#ReadingPane).  
  
-   [Uso di dimensioni dell'icona ottimali](#UsingOptimal).  
  
 Per altre informazioni sulle aree del modulo, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Using Form Region Names  
 Per descrivere l'area del modulo possono essere usati diversi nomi. È importante comprendere la differenza tra questi nomi e gli effetti che hanno sull'area del modulo. La tabella seguente descrive i singoli nomi.  
  
|Nome dell'area del modulo|Descrizione|  
|----------------------|-----------------|  
|Nome dell'elemento dell'area del modulo|Il nome specificato per l'elemento **Area del modulo di Outlook** nella finestra di dialogo **Aggiungi nuovo elemento** . È il nome del file di codice dell'area del modulo visualizzato in **Esplora soluzioni**.|  
|Proprietà<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> |Questo nome viene specificato nella pagina **Fornire un testo descrittivo e selezionare le preferenze di visualizzazione** della procedura guidata **Nuova area del modulo di Outlook** . Questo nome viene visualizzato come proprietà **FormRegionName** nella finestra **Proprietà** .<br /><br /> Usare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> per specificare l'etichetta che identifica l'area del modulo nell'interfaccia utente di Outlook. Per le aree del modulo separate, questo nome viene visualizzato come pulsante nella barra multifunzione dell'elemento di Outlook.<br /><br /> Per le aree del modulo adiacenti, questo nome viene visualizzato come testo di intestazione sopra l'area del modulo.|  
|Attributo Microsoft.Office.Tools.Outlook.FormRegionName|Quando si aggiunge un elemento **Area del modulo di Outlook** al progetto, Visual Studio imposta questa proprietà sul nome completo dell'area del modulo. Il nome completo predefinito è il nome del componente aggiuntivo VSTO connesso al nome dell'area del modulo con un punto, ad esempio `OutlookAddIn1.FormRegion1`.<br /><br /> Questo nome completo viene visualizzato anche come attributo nella parte superiore della classe factory dell'area del modulo.<br /><br /> Utilizzare l'attributo Microsoft.Office.Tools.Outlook.FormRegionName per identificare in modo univoco l'area del modulo tra tutti i componenti aggiuntivi VSTO di Outlook. Non è possibile modificare il valore dell'attributo Microsoft.Office.Tools.Outlook.FormRegionName rinominando l'elemento area del modulo o modificando il <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> proprietà. Per modificare questo nome, è necessario modificare l'attributo Microsoft.Office.Tools.Outlook.FormRegionName nel file di codice di area del modulo.|  
  
##  <a name="DisablingInheritance"></a> Disabling Form Region Inheritance  
 Per impostazione predefinita, una classe messaggio personalizzata eredita tutte le associazioni dell'area del modulo per la classe messaggio di base. Ad esempio, una classe messaggio denominata `IPM.Task.Contoso` deriva da IPM. Attività. Pertanto, `IPM.Task.Contoso` eredita le associazioni di area del modulo di IPM. Attività.  
  
 Per non associare l'area del modulo con classi messaggio derivate, impostare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> dell'area del modulo su **true**. Ad esempio, se si associa un'area del modulo adiacente a IPM. Attività e impostare il <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> proprietà **true**, l'area del modulo verrà aggiunta solo alla fine di un modulo di attività standard. L'area del modulo non verrà aggiunta alla fine di versioni personalizzate di un modulo di attività standard.  
  
##  <a name="ClassNames"></a> Informazioni sui tipi e sui nomi delle classi messaggio  
 Il nome del tipo di un elemento di Outlook è diverso dal nome della classe messaggio di un elemento di Outlook. Ad esempio, il nome del tipo di un elemento RSS è PostItem. Il nome della classe messaggio di un elemento RSS è IPM. Post.RSS.  
  
 Usare il nome del tipo per fare riferimento a un elemento di Outlook nel codice. Per un elenco di nomi dei tipi, vedere [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Usare il nome della classe messaggio degli elementi di Outlook nella procedura guidata **Nuova area del modulo di Outlook** per associare l'elemento all'area del modulo. Per un elenco di nomi validi per la classe messaggio, vedere [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Designing Adjoining Form Regions for the Reading Pane  
 È possibile usare il riquadro di lettura di Outlook per visualizzare l'anteprima di un elemento di Outlook senza aprirlo. Il riquadro di lettura è progettato solo per l'accesso in lettura. Quindi, i controlli di input aggiunti a un'area del modulo adiacente, ad esempio una casella di testo, potrebbero non funzionare come previsto quando l'elemento e l'area del modulo sono aperti nel riquadro di lettura.  
  
 Ad esempio, se un elemento con un'area del modulo adiacente è aperto nel riquadro di lettura, è possibile che si verifichi la situazione seguente:  
  
1.  Selezionare il testo in una casella di testo nell'area del modulo.  
  
2.  Premere CANC.  
  
3.  Non viene eliminato il testo nella casella di testo, ma l'intero elemento di posta elettronica.  
  
 Se si sta progettando un'area del modulo adiacente che contiene controlli di input, testare i controlli nel riquadro di lettura per verificarne il corretto funzionamento. Valutare l'aggiunta di codice personalizzato per disabilitare i controlli che non funzionano come previsto.  
  
 In alternativa, è possibile impostare la proprietà <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> dell'area del modulo su **False**. In questo modo, l'area del modulo non può essere usata nel riquadro di lettura.  
  
##  <a name="UsingOptimal"></a> Using Optimal Icon Sizes  
 Per specificare quali icone visualizzare nell'area del modulo, impostare le proprietà dell'icona nel gruppo di proprietà **Icone** della finestra **Proprietà** . Usare le linee guida seguenti per ottenere la migliore qualità grafica possibile:  
  
-   Per l'icona **Pagina** , usare un file PNG (Portable Network Graphics).  
  
-   Per l'icona**Finestra** si consiglia una dimensione di 32 pixel per 32 pixel.  
  
-   Per tutte le altre icone, le dimensioni consigliate sono 16 pixel per 16 pixel.  
  
 L'icona **Pagina** viene visualizzata nella barra multifunzione di un controllo per gli elementi con aree del modulo separate, di sostituzione o di sostituzione completa.  
  
 L'icona **Finestra** viene visualizzata nell'area di notifica e nella finestra di dialogo ALT+TAB per gli elementi aperti che visualizzano aree del modulo di sostituzione o di sostituzione completa.  
  
## <a name="see-also"></a>Vedere anche  
 [L'accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  