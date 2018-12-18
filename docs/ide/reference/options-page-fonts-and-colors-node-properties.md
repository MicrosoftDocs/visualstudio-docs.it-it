---
title: "Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a26dd168e83584b19a9d6ddad37496082c166f2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori
Questo documento descrive le proprietà di tipi di carattere e colori per una finestra degli strumenti registrata per la visualizzazione in **Tipi di carattere e colori** nella categoria **Ambiente** della finestra di dialogo **Opzioni**. Supporta la natura dinamica dei gruppi di elementi colorabili, che possono cambiare se vengono installati o disinstallati pacchetti VSPackage.  
  
 La sezione seguente illustra un esempio di un tipo di finestra registrata e le proprietà disponibili per ogni finestra.  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor di testo o Stampante o Finestre di dialogo e degli strumenti  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 oppure  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 oppure  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|FontFamily|Get/Set (String)|Il tipo di carattere da usare, ad esempio "Courier New".|  
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>) |Valore <xref:EnvDTE.vsFontCharSet> che specifica il tipo di set di caratteri da usare, ad esempio ebraico o russo. |  
|FontSize|Get/Set (Short)|La dimensione del carattere da usare, in punti. Ad esempio, 10 o 12.|  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo delle impostazioni relative alle opzioni](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinazione dei nomi degli elementi delle proprietà nelle pagine delle opzioni](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Pagina delle opzioni, Proprietà del nodo Ambiente](../../ide/reference/options-page-environment-node-properties.md)   
 [Pagina delle opzioni, Proprietà del nodo Editor di testo](../../ide/reference/options-page-text-editor-node-properties.md)