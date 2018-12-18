---
title: Commenti
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: cb44dc755721f6095c9a07ad3e6fec1f6849e149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="comments"></a>Commenti

Durante l'esecuzione del debug o di esperimenti con il codice, può essere utile impostare blocchi di codice come commenti, temporaneamente o a lungo termine. 

Per impostare un intero blocco di codice come commento:

* Selezionare il codice e selezionare **Attiva/Disattiva commento per riga** dal menu di scelta rapida

OR

* Usare il tasto di scelta rapida `cmd + /` sul codice selezionato.

Questi metodi possono essere usati per impostare come commenti una o più sezioni di codice, nonché per annullare questa impostazione. Nei file C# è possibile aggiungere altri livelli di commenti riga. Ciò consente di impostare aree di codice come commenti e di annullare questa impostazione mantenendo comunque i commenti effettivi: 

 ![Commenti a più livelli](media/source-editor-image8.png)

I commenti sono utili anche per la documentazione di codice per gli sviluppatori che potranno interagire con esso in futuro. Tali commenti vengono in genere creati sotto forma di commenti su più righe e per ogni lingua vengono aggiunti nel modo seguente:

**C#**

``` cs
/*
 This is a multi-line
 comment in C#
*/
```
**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```
