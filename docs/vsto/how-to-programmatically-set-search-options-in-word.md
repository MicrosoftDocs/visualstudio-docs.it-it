---
title: 'Procedura: impostare a livello di codice le opzioni di ricerca in Word | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3be8d12f18e4ea0b6d05cbad92c08c7b5427315c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Procedura: impostare opzioni di ricerca in Word a livello di codice
  Esistono due modi per impostare le opzioni di ricerca delle selezioni in documenti di Microsoft Office Word:  
  
-   Impostare singole proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto.  
  
-   Utilizzare gli argomenti del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un <xref:Microsoft.Office.Interop.Word.Find> oggetto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>Utilizzando le proprietà di un oggetto Find  
 Il codice seguente imposta proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per cercare testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, ritorno a capo e testo da cercare, sono proprietà del <xref:Microsoft.Office.Interop.Word.Find> oggetto.  
  
 L'impostazione delle proprietà di singole il <xref:Microsoft.Office.Interop.Word.Find> oggetto non è utile quando si scrive codice c#, perché è necessario specificare le stesse proprietà come parametri in di <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo. In questo esempio contiene pertanto solo Visual Basic (codice).  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Per impostare le opzioni di ricerca mediante un oggetto Find  
  
1.  Impostare le proprietà di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per eseguire la ricerca tramite una selezione per il testo **trovare me**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>Utilizzo dell'istruzione Execute gli argomenti del metodo  
 Il codice seguente usa il <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo di un <xref:Microsoft.Office.Interop.Word.Find> oggetto per cercare testo all'interno della selezione corrente. Si noti che i criteri di ricerca, ad esempio la ricerca in avanti, ritorno a capo e testo da cercare, vengono passati come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo.  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Per impostare le opzioni di ricerca utilizzando gli argomenti del metodo Execute  
  
1.  Passare ai criteri di ricerca come parametri del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodo per eseguire la ricerca tramite una selezione per il testo **trovare me**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: cercare a livello di codice e sostituire testo nei documenti](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Procedura: scorrere gli elementi trovati nei documenti a livello di codice in ciclo](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Procedura: Ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  