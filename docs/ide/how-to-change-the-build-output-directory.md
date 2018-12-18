---
title: 'Procedura: Modificare la directory di output della compilazione | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 14aad8b82a3757fecb1d449a671fc07c2582bb5f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-change-the-build-output-directory"></a>Procedura: modificare la directory dell'output compilato
Il percorso dell'output generato dal progetto può essere specificato a livello di singole configurazioni (per debug e/o rilascio).  
  
> [!NOTE]
>  Se si ha un progetto **Installazione** , vedere la nota alla fine di questo articolo.  
  
## <a name="changing-the-build-output-directory"></a>Modifica della directory dell'output di compilazione  
  
#### <a name="to-change-the-build-output-directory"></a>Per modificare la directory dell'output di compilazione  
  
1.  Nella barra dei menu scegliere **Progetto**, *NomeApp* **Proprietà**. In alternativa, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.  
  
2.  Per i progetti Basic, selezionare la scheda **Compilazione** . Per i progetti C#, selezionare la scheda **Compilazione**. Per un progetto C++ o JavaScript, selezionare la scheda **Generale** .  
  
3.  Nell'elenco a discesa della configurazione nella parte superiore, scegliere la configurazione per cui si vuole modificare il percorso di output (debug, rilascio o tutte).  
  
     Individuare la voce relativa al percorso di output (**Percorso dell'output di compilazione** in Visual Basic **Directory di output** in Visual C++, **Percorso di Output** in JavaScript e C#). Specificare una nuova directory dell'output di compilazione relativa alla directory del progetto.  
  
> [!NOTE]
>  In un progetto di installazione, la casella **Nome file di output** modifica solo il percorso del file Setup.exe file, non il percorso dei file di progetto. Per ulteriori informazioni, vedere **Compilazione, proprietà di configurazione, finestra di dialogo delle proprietà del progetto di distribuzione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md)  (Pagina Compilazione, Progettazione progetti (C#))  
 [General Property Page (Project)](/cpp/ide/general-property-page-project)  (Pagina delle proprietà Generale (Progetto))  
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)