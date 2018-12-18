---
title: Eseguire il commit delle modifiche in corso nei controlli associati a dati prima del salvataggio dei dati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a0811ec9338bfb84235679a68d32169435eb57a5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Eseguire il commit delle modifiche in corso nei controlli associati a dati prima del salvataggio dei dati

Quando si modificano i valori nei controlli con associazione a dati, è necessario spostarsi dal record corrente per eseguire il commit il valore aggiornato dell'origine dati sottostante che il controllo è associato a. Quando si trascinano elementi dal [finestra Origini dati](add-new-data-sources.md) in un form, il primo elemento che elimina genera il codice nel **salvare** evento click del pulsante di <xref:System.Windows.Forms.BindingNavigator>. Questo codice chiama il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo il <xref:System.Windows.Forms.BindingSource>. Pertanto, la chiamata per il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo viene generato solo per il primo <xref:System.Windows.Forms.BindingSource> che viene aggiunto al form.

Il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> chiamata esegue il commit di tutte le modifiche nel processo, nei controlli con associazione a dati che si stanno modificando. Pertanto, se un controllo con associazione a dati ha lo stato attivo e si sceglie il **salvare** pulsante, tutte le modifiche in sospeso nel controllo viene eseguito il commit prima del salvataggio effettivo (il `TableAdapterManager.UpdateAll` (metodo)).

È possibile configurare l'applicazione di eseguire automaticamente il commit delle modifiche, anche se un utente tenta di salvare i dati senza eseguire il commit delle modifiche, come parte del salvataggio processo.

> [!NOTE]
> La finestra di progettazione aggiunge il `BindingSource.EndEdit` codice solo per il primo elemento rilasciato in un form. Pertanto, è necessario aggiungere una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource> nel form. È possibile aggiungere manualmente una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource>. In alternativa, è possibile aggiungere il `EndEditOnAllBindingSources` metodo al form e chiamarlo prima di eseguire un salvataggio.

Il codice seguente usa un [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) query per eseguire l'iterazione di tutti <xref:System.Windows.Forms.BindingSource> componenti e chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource> in un form.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Per chiamare EndEdit per tutti i componenti di BindingSource in un form

1.  Aggiungere il codice seguente al form che contiene il <xref:System.Windows.Forms.BindingSource> componenti.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Aggiungere la seguente riga di codice immediatamente prima delle chiamate per salvare i dati del modulo (il `TableAdapterManager.UpdateAll()` (metodo)):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)