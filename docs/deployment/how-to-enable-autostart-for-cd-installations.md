---
title: Abilitare l'avvio automatico per le installazioni di CD | Microsoft Docs
description: Informazioni su come abilitare l'avvio automatico quando si distribuisce un'applicazione ClickOnce per mezzo di supporti rimovibili, ad esempio CD-ROM o DVD-ROM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b157df8666223e72a1e36d58505a5c087b0351bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900687"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Procedura: Attivare l'avvio automatico per le installazioni da CD
Quando si distribuisce un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione per mezzo di supporti rimovibili, ad esempio CD-ROM o DVD-ROM, è possibile abilitare in `AutoStart` modo che l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione venga avviata automaticamente al momento dell'inserimento del supporto.

 `AutoStart` può essere abilitato nella pagina **pubblica** di **Progettazione progetti**.

### <a name="to-enable-autostart"></a>Per abilitare l'avvio automatico

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **proprietà** dal menu **progetto** .

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **Opzioni** .

     Verrà visualizzata la finestra di dialogo **Opzioni di pubblicazione** .

4. Fare clic su **Distribuzione**.

5. Selezionare la casella **di controllo per le installazioni CD, avvia automaticamente il programma di installazione quando viene inserito CD** .

     Un file *Autorun. inf* verrà copiato nel percorso di pubblicazione quando viene pubblicata l'applicazione.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)