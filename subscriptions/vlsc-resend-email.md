---
title: Sottoscrizioni di Visual Studio - Inviare d nuovo i messaggi di posta elettronica di assegnazione da VLSC
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend subscription assignment emails from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 338ae08ee1f3e6a819a1faea7bd095c9acd8ecd2
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/16/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-within-volume-license-service-center-vlsc"></a>Come inviare di nuovo i messaggi di posta elettronica di assegnazione delle sottoscrizioni da Volume License Service Center (VLSC)

In alcuni casi, un sottoscrittore a cui è stata assegnata una sottoscrizione potrebbe chiedere all'amministratore di inviare di nuovo il messaggio di posta elettronica di notifica dell'assegnazione della sottoscrizione.  Nel nuovo portale di gestione delle sottoscrizioni, https://manage.visualstudio.com, il processo è semplice.  Tuttavia, se l'organizzazione usa ancora Volume License Service Center (VLSC) non è disponibile una funzionalità per inviare di nuovo automaticamente il messaggio di posta elettronica di notifica.  

Per inviare di nuovo il messaggio di posta elettronica di notifica da VLSC, un amministratore deve usare la soluzione seguente:

## <a name="resending-the-assignment-email"></a>Nuovo invio del messaggio di posta elettronica di assegnazione:

Perché VLSC possa generare una nuova notifica, è necessario modificare le informazioni di posta elettronica del sottoscrittore una volta e quindi ripristinare i dati di posta elettronica originali nella stessa transazione. In questo modo VLSC reagisce come se fosse stata assegnata una nuova sottoscrizione e invia di nuovo il messaggio di posta elettronica di assegnazione.

1.  Visitare [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e accedere.
2.  Fare clic sulla scheda **Sottoscrizioni** e scegliere **Sottoscrizioni di Visual Studio**.
3.  Fare clic sul **numero di contratto** associato alla sottoscrizione di Visual Studio.
4.  Fare clic sulla freccia in giù nella barra di ricerca. 
5.  Cercare il sottoscrittore usando il campo dell'**indirizzo di posta elettronica**.
6.  Individuare il sottoscrittore nei risultati della ricerca e fare clic sul cognome. 
7.  Fare clic su **Modifica**.
8.  Apportare una modifica alla sottoscrizione. Ad esempio, è possibile rimuovere un carattere dall'indirizzo di posta elettronica del sottoscrittore. Fare clic sul pulsante **Salva**.
9.  Dopo avere salvato le informazioni, fare di nuovo clic su **Modifica**, annullare la modifica appena apportata e fare clic su **Salva**.  

La sottoscrizione verrà così considerata una nuova assegnazione e verrà inviato di nuovo il messaggio di posta elettronica di notifica dell'assegnazione al sottoscrittore.  