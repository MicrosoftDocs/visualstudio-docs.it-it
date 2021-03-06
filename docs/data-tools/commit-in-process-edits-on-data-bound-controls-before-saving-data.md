---
title: Modifiche di cui non è stato eseguito il commit
description: Eseguire il commit delle modifiche in-process sui controlli Windows Form associati ai dati prima di salvare i dati. Chiamare EndEdit per tutti i componenti BindingSource in un form.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 53101505230a51f109ace904c2f8322659733b4b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216319"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati

Quando si modificano i valori nei controlli associati a dati, gli utenti devono passare al record corrente per eseguire il commit del valore aggiornato nell'origine dati sottostante a cui è associato il controllo. Quando si trascinano elementi dalla [finestra Origini dati](add-new-data-sources.md) in un form, il primo elemento che si rilascia genera il codice nell'evento click del pulsante **Salva** di <xref:System.Windows.Forms.BindingNavigator> . Questo codice chiama il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo di <xref:System.Windows.Forms.BindingSource> . La chiamata al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo viene pertanto generata solo per la prima <xref:System.Windows.Forms.BindingSource> aggiunta al modulo.

La chiamata di <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli associati a dati che si stanno modificando. Pertanto, se un controllo associato a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo (metodo `TableAdapterManager.UpdateAll`).

È possibile configurare l'applicazione in modo da eseguire automaticamente il commit delle modifiche, anche se un utente tenta di salvare i dati senza eseguire il commit delle modifiche, come parte del processo di salvataggio.

> [!NOTE]
> La finestra di progettazione aggiunge il `BindingSource.EndEdit` codice solo per il primo elemento rilasciato in un modulo. Pertanto, è necessario aggiungere una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource> nel form. È possibile aggiungere manualmente una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource> . In alternativa, è possibile aggiungere il `EndEditOnAllBindingSources` metodo al form e chiamarlo prima di eseguire un salvataggio.

Il codice seguente usa una query [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) per eseguire l'iterazione di tutti i <xref:System.Windows.Forms.BindingSource> componenti e chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource> in un form.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Per chiamare EndEdit per tutti i componenti BindingSource in un form

1. Aggiungere il codice seguente al modulo che contiene i <xref:System.Windows.Forms.BindingSource> componenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Aggiungere la riga di codice seguente immediatamente prima di qualsiasi chiamata per salvare i dati del modulo ( `TableAdapterManager.UpdateAll()` metodo):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Vedi anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
