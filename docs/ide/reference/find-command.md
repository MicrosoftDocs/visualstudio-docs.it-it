---
title: Comando Find | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4f20be9aafaa6002ba329b7dd14c132dbfcab70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="find-command"></a>Comando Trova
Esegue la ricerca di testo nei file usando un subset delle opzioni disponibili nella scheda **Cerca nei file** della finestra **Trova e sostituisci**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## <a name="arguments"></a>Argomenti  
 `findwhat`  
 Obbligatorio. Testo da cercare.  
  
## <a name="switches"></a>Opzioni  
 /case o /c  
 Facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.  
  
 /doc o /d  
 Facoltativo. Cerca solo nel documento corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /markall o /m  
 Facoltativo. Inserisce un grafo per ogni riga che contiene una corrispondenza della ricerca all'interno del documento corrente.  
  
 /open o /o  
 Facoltativo. Cerca in tutti i documenti aperti come se fossero un unico documento. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /options o /t  
 Facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.  
  
 /proc o /p  
 Facoltativo. Cerca solo nella routine corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /reset o /e  
 Facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.  
  
 /sel o /s  
 Facoltativo. Cerca solo nella selezione corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /up o /u  
 Facoltativo. Esegue la ricerca dalla posizione corrente nel file verso l'inizio del file. Per impostazione predefinita, le ricerche iniziano in corrispondenza della posizione nel file e procedono verso la fine del file.  
  
 /regex o /r  
 Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /wild o /l  
 Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.  
  
 /word o /w  
 Facoltativo. Cerca solo parole intere.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene eseguita una ricerca con distinzione tra maiuscole e minuscole della parola "string" nella sezione di codice attualmente selezionata.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md) (Alias di comandi di Visual Studio)