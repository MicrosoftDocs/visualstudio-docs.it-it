---
title: 'Procedura: eseguire la ricerca a livello di codice per un indirizzo di posta elettronica nei contatti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 16b79f5f14f1e0d8c5c82a00f5f2ccf2412b991b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Procedura: Eseguire la ricerca di un indirizzo di posta elettronica nei contatti a livello di codice
  Questo esempio cerca una cartella Contatti per i contatti con il nome dominio **example.com** nei relativi indirizzi di posta elettronica.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Contatti con il nome dominio **example.com** nei relativi indirizzi di posta elettronica (ad esempio, `somebody@example.com`) e con il nome e il cognome.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei contatti](../vsto/working-with-contact-items.md)   
 [Procedura: invio di posta elettronica a livello di codice](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Procedura: accedere a livello di codice ai contatti di Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Procedura: Aggiungere una voce ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  