---
title: La finestra di dialogo delle opzioni della tastiera di Microsoft Office Word, impostazioni della tastiera di Microsoft Office, | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d8747485ced6309bf9e63ecf864c67a111ce6c47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Tastiera di Microsoft Office Word, impostazioni della tastiera di Microsoft Office, finestra di dialogo Opzioni
  Microsoft Office Word e Visual Studio sia di tasti di scelta rapida. La combinazione di tasti di scelta rapida può attivare comandi diversi in Word e in Visual Studio. Quando Word è aperto in un progetto a livello di documento in Visual Studio, solo un'applicazione in un momento riceve i comandi dei tasti di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile apportare parola riceverli quando il documento ha lo stato attivo selezionando **schema della tastiera dinamico**.  
  
 Se si utilizza un tasto di scelta rapida che non è assegnato a un comando nell'applicazione che sta gestendo i tasti di scelta rapida, tasti di scelta rapida viene passato a altra applicazione.  
  
 L'opzione selezionata verrà rimangono valide per i progetti Word fino a quando non si decida di modificarlo. La selezione non influisce sulla progetti di Microsoft Office Excel. Per apportare eventuali modifiche in Excel è necessario utilizzare le opzioni della tastiera di Microsoft Office Excel.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Schema della tastiera di Visual Studio**  
 Visual Studio riceve tutti i comandi dei tasti di scelta rapida, anche se il documento di Word ha lo stato attivo. Ad esempio, se si preme il tasto funzione F5 quando il documento ha lo stato attivo, Visual Studio avvia il debug della soluzione.  
  
 **Schema della tastiera dinamico**  
 Visual Studio riceve comandi dei tasti di scelta rapida solo quando lo stato attivo. Quando il documento di Word è attiva, riceve tutti i comandi dei tasti di scelta rapida. Ad esempio, se si preme il tasto funzione F5, mentre il documento di Word è attivo, verrà aperto il **Trova e sostituisci** la finestra di dialogo con la **Vai a** scheda selezionata. Se si preme F5, mentre Visual Studio ha lo stato attivo, Visual Studio avvia il debug della soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Tastiera di Microsoft Office Excel, impostazioni della tastiera di Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  