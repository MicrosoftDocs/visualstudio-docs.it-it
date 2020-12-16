---
title: Confronto tra soluzioni VBA e Office in Visual Studio
description: Informazioni sulle differenze tra Microsoft Visual Basic, Applications Edition (VBA) e le soluzioni di Microsoft Office in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d07975061a7b2f5f655bf7f4339671f28fe14c9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526411"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Confronto tra soluzioni VBA e Office in Visual Studio
  In Microsoft Visual Basic, Applications Edition (VBA) viene usato codice non gestito che è strettamente integrato con le applicazioni di Office. I progetti di Microsoft Office creati tramite Visual Studio consentono di sfruttare gli strumenti di progettazione di Visual Studio e .NET Framework.

 Per informazioni sui tipi di soluzioni Office che è possibile creare con Visual Studio, vedere [Cenni preliminari sullo sviluppo di soluzioni office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Confronto
 Nella tabella riportata di seguito viene fornito un confronto di base tra soluzioni VBA e soluzioni Office in Visual Studio.

|Soluzioni VBA|Soluzioni Office in Visual Studio|
|-------------------|---------------------------------------|
|Utilizzano codice connesso al documento specifico e con cui viene conservato.|Usa il codice archiviato separatamente dal documento (per le personalizzazioni a livello di documento) o in un assembly caricato dall'applicazione (per i componenti aggiuntivi VSTO).|
|Funzionano con i modelli a oggetti di Office e con le API di VBA.|Forniscono accesso ai modelli a oggetti di Office e alle API di [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Progettate per la registrazione di macro e per un'esperienza di sviluppo semplificata.|Progettate per garantire sicurezza, una gestione facilitata del codice e la possibilità di usare l'intero ambiente di sviluppo integrato di Visual Studio.|
|Funziona bene per le soluzioni che traggono vantaggio da una stretta integrazione con le applicazioni di Office.|Particolarmente adatte per soluzioni che sfruttano le risorse complete di Visual Studio e [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|
|Presentano funzionalità limitate per le soluzioni aziendali, soprattutto in relazione alla sicurezza e alla distribuzione.|Progettate per le aziende.|

 Alcune operazioni possono essere eseguite rapidamente con maggiore semplicità usando VBA. In particolare, può rivelarsi utile continuare a usare VBA per:

- Funzioni dei fogli di lavoro personalizzate.

- Registrazione di macro.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combinare soluzioni VBA e soluzioni Office create con Visual Studio
 È possibile chiamare codice VBA dalle soluzioni Office create tramite Visual Studio ed è anche possibile chiamare codice delle soluzioni Office create tramite Visual Studio da VBA. La tecnica specifica differisce a seconda del fatto che la soluzione Office sia un componente aggiuntivo VSTO o una personalizzazione a livello di documento. Per altre informazioni, vedere [chiamare il codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) e [combinare VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Chiamata di codice nei componenti aggiuntivi VSTO da altre soluzioni Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Combinare VBA e personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Introduzione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
