---
title: 'Procedura: Eseguire la ricerca a livello di codice di un contatto specifico'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: feff583d28bf53f4bffc9b425d52902688b80a4b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607161"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Procedura: Eseguire la ricerca a livello di codice di un contatto specifico
  Questo esempio cerca una cartella Contatti di Outlook per un contatto specifico in base al nome e al cognome. L'esempio presuppone che un contatto denominato **John Evans** esista nella cartella Contatti.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Vedere anche
- [Lavorare con gli elementi di contatto](../vsto/working-with-contact-items.md)
- [Introduzione a programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
