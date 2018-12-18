---
title: Codici di messaggio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b2061d9f20da8e9c4d5b4f9794f400d638260c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="message-codes"></a>Codici di messaggio
Ogni riga del messaggio nel [visualizzazione messaggi](../debugger/messages-view.md) contiene 'P', del,' del,' o 'R' codice. Tali codici hanno i significati seguenti:  
  
|Codice|Significato|  
|----------|-------------|  
|P|Il messaggio è stato inserito nella coda con il **PostMessage** (funzione). Non sono disponibili informazioni sulla disposizione finale del messaggio.|  
|S|Il messaggio è stato inviato con il **SendMessage** (funzione). Ciò significa che il mittente non riprendere il controllo fino a quando il ricevitore elabora e restituisce il messaggio. Il destinatario può, pertanto, passare un valore restituito al mittente.|  
|s|È stato inviato il messaggio, ma che impedisce l'accesso al valore restituito.|  
|R|Ciascuna ' la riga contiene una riga corrispondente di 'R' (return) in cui sono elencati il valore restituito del messaggio. Talvolta le chiamate al messaggio sono annidate, ovvero che un gestore di messaggi invia un altro messaggio.|