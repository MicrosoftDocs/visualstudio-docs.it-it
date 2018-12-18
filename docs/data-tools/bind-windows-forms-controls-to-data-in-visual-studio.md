---
title: Associare controlli Windows Form ai dati in Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 7ade7aa6e103a8637d26b10029faabc434ce3a83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associare controlli Windows Form ai dati in Visual Studio
È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dati a un Windows Form. Per creare questi controlli con associazione a dati, è possibile trascinare elementi dal **origini dati** finestra in Progettazione Windows Form in Visual Studio.
  
![Operazione di trascinamento con origine dati](../data-tools/media/raddata-data-source-drag-operation.png "operazione di trascinamento raddata origine dati")

Prima di trascinare elementi, è possibile impostare il tipo di controllo che si desidera associare. Valori diversi visualizzati a seconda se si scelga la tabella stessa, o una singola colonna.  È inoltre possibile impostare valori personalizzati. Per una tabella, "Dettagli" significa che ogni colonna è associato a un controllo separato.  

![Associare l'origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata origine dati di associazione di DataGridView")  
  
## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource e controlli di BindingNavigator
Il componente <xref:System.Windows.Forms.BindingSource> ha due scopi. Fornisce un livello di astrazione quando i controlli di associazione ai dati. I controlli nel form vengono associati per il <xref:System.Windows.Forms.BindingSource> componente anziché direttamente a un'origine dati. In secondo luogo, è possibile gestire una raccolta di oggetti. Aggiunta di un tipo per il <xref:System.Windows.Forms.BindingSource> crea un elenco di quel tipo.  
  
Per ulteriori informazioni sul <xref:System.Windows.Forms.BindingSource> componente, vedere:  
  
-   [Componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)  
  
-   [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
-   [Architettura del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)  
  
Il [controllo BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) fornisce un'interfaccia utente per l'esplorazione dei dati visualizzati in un'applicazione Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Associazione a dati in un controllo DataGridView  
Per un [controllo DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), l'intera tabella è associato a tale controllo singolo. Quando si trascina un controllo DataGridView al form, uno strumento striscia per l'esplorazione dei record (<xref:System.Windows.Forms.BindingNavigator>) viene inoltre visualizzato. Oggetto [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti. Nella figura seguente, viene inoltre aggiunto un TableAdapterManager perché la tabella Customers è una relazione con la tabella Orders. Queste variabili sono tutti dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per la compilazione di DataGridView si trova nel gestore eventi form_load. Il codice per il salvataggio dei dati per aggiornare il database si trova nel gestore dell'evento Save di BindingNavigator. È possibile spostare o modificare il codice in base alle esigenze.  
  
![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")  
  
È possibile personalizzare il comportamento di DataGridView e BindingNavigator facendo clic sullo smart tag nell'angolo superiore destro di ogni:  
  
![DataGridView e associazione Navigator smart tag](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView e associazione Navigator smart tag")  
  
Se i controlli dell'applicazione è necessario non è disponibile dall'interno di **origini dati** finestra, è possibile aggiungere controlli. Per ulteriori informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
È anche possibile trascinare elementi dal **origini dati** finestra controlli già presenti in un form per associare il controllo ai dati. Un controllo che è già associato a dati con i dati di binding reimpostati sull'elemento trascinato più di recente. Per essere destinazioni di rilascio valide, i controlli devono essere in grado di visualizzare il tipo di dati sottostante dell'elemento trascinato su di esso dal **origini dati** finestra. Ad esempio, non è a trascinare un elemento che ha un tipo di dati <xref:System.DateTime> su un <xref:System.Windows.Forms.CheckBox>, in quanto il <xref:System.Windows.Forms.CheckBox> non è in grado di visualizzare una data.  
  
## <a name="bind-to-data-in-individual-controls"></a>Associazione a dati in singoli controlli  
Quando si associa un'origine dati per "Dettagli", ogni colonna nel set di dati è associato a un controllo separato.  
  
![Associare l'origine dati per i dettagli](../data-tools/media/raddata-bind-data-source-to-details.png "raddata origine dati di associazione per i dettagli")  
  
> [!IMPORTANT]
> Si noti che nella figura precedente, si trascina dalla proprietà ordini della tabella Customers, non dalla tabella Orders. Tramite l'associazione alla proprietà Orders, i comandi di spostamento apportati in DataGridView vengono riflesse immediatamente nei controlli di dettagli. Se è stata trascinata dalla tabella Orders, i controlli sarebbero comunque essere associati al set di dati, ma non potrebbe non essere sincronizzati con il controllo DataGridView.  
  
La figura seguente mostra l'impostazione predefinita i controlli con associazione a dati che vengono aggiunti al modulo dopo che la proprietà di ordini nella tabella Customers è associata a "Dettagli" nel **origini dati** finestra.  
  
![Tabella Orders associata ai dettagli](../data-tools/media/raddata-orders-table-bound-to-details.png "tabella Orders raddata associata ai dettagli")  
  
Si noti inoltre che ogni controllo dispone di uno smart tag. Questo tag consente personalizzazioni che si applicano a solo a tale controllo.
  
## <a name="see-also"></a>Vedere anche
[Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Data binding in Windows Form (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)