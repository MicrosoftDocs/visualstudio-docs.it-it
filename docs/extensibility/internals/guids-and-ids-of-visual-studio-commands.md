---
title: GUID e ID dei comandi di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1566b7e252867779e2bf7cbf26e2a6cbcb8b009f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e ID dei comandi di Visual Studio
I valori GUID e ID dei comandi inclusi nell'ambiente di sviluppo integrato (IDE) di Visual Studio sono definiti in file con estensione vsct vengono installati come parte di Visual Studio SDK. Per ulteriori informazioni, vedere [IDE-Defined comandi, menu e gruppi](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Per ulteriori informazioni su come usare gli oggetti IDE che sono definiti nel file vsct, vedere [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Ricerca di una definizione di comando  
 Poiché Visual Studio definisce i comandi di più di 1000, non è pratico per elencarli tutti qui. Al contrario, seguire questi passaggi per individuare la definizione di un comando.  
  
#### <a name="to-locate-a-command-definition"></a>Per individuare una definizione di comando  
  
1.  In Visual Studio, aprire i file seguenti nella *il percorso di installazione di Visual Studio SDK*cartella \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     La maggior parte dei comandi di Visual Studio sono definiti in SharedCmdDef.vsct e ShellCmdDef.vsct. VsDbgCmdUsed.vsct definisce i comandi che riguardano il debugger e Venusmenu.vsct definisce i comandi che sono specifici per lo sviluppo Web.  
  
2.  Se il comando è una voce di menu, si noti il testo esatto della voce di menu. Se il comando è un pulsante sulla barra degli strumenti, si noti il testo della descrizione comando visualizzata quando si posiziona su di esso.  
  
3.  Premere CTRL + F per aprire la **trovare** la finestra di dialogo.  
  
4.  Nel **trova** , digitare il testo annotato nel passaggio 2.  
  
5.  Verificare che **tutti i documenti aperti** viene visualizzato nel **Cerca in** casella.  
  
6.  Fare clic su di **Trova successivo** pulsante fino a quando non viene selezionato il testo nel `<Strings>` sezione di un [elemento Button](../../extensibility/button-element.md).  
  
     Il `<Button>` elemento presente il comando è la definizione di comando.  
  
 Quando è stato possibile trovare la definizione di comando, è possibile inserire una copia del comando in un altro menu o sulla barra degli strumenti mediante la creazione di un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) che ha lo stesso `guid` e `id` valori come il comando. Per ulteriori informazioni, vedere [creazione riutilizzabile gruppi di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Casi speciali  
 Nei casi seguenti, il testo del menu o il testo della descrizione comandi potrebbe non corrispondere esattamente novità nella definizione del comando.  
  
-   Voci di menu che includono un carattere sottolineato, ad esempio il **stampa** comando il **File** menu, in cui il P è sottolineato.  
  
     I caratteri che sono preceduti dal carattere '&' nei nomi di voce di menu vengono visualizzati come sottolineato. Tuttavia, i file con estensione vsct vengono scritti in XML, che utilizza il carattere '&' per indicare i caratteri speciali e richiede che deve essere digitata una e commerciale che deve essere visualizzato nome&amp;'. Pertanto, in un file con estensione vsct, il **P**rint comando visualizzato come "&amp;stampa '.  
  
-   I comandi che presentano un testo dinamico, ad esempio **salvare** *nome file corrente*e generate in modo dinamico le voci di menu, ad esempio gli elementi nel **file recenti** elenco.  
  
     Non è affidabile per cercare testo dinamico. In alternativa, trovare un gruppo che contiene il comando desiderato consultando [GUID e ID di Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e ID di Visual Studio le barre degli strumenti](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e cercare l'ID di tale gruppo. Se la definizione di comando non è un gruppo come relativo [elemento padre](../../extensibility/parent-element.md), cercare SharedCmdPlace.vsct e ShellCmdPlace.vsct (o VsDbgCmdPlace.vsct per i comandi del debugger) un `<CommandPlacement>` imposta l'elemento padre dell'elemento di comando. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, sono presenti il *il percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ cartella.  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto tra oggetti MenuCommand e OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)