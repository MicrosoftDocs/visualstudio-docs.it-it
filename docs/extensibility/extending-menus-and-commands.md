---
title: Estensione di menu e comandi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 830748be6f2cedf57b94a9824bc0912820067718
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="extending-menus-and-commands"></a>Estensione di menu e comandi
I comandi sono la procedura per aggiungere le azioni e i processi per Visual Studio. Nella maggior parte dei casi i comandi vengono visualizzati nei menu o barre degli strumenti. Il modello di progetto VSPackage viene illustrato come implementare un comando di base. Per un'implementazione più lente ma ancora base, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Per ulteriori informazioni sui comandi, menu e barre degli strumenti di Visual Studio, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 I comandi, menu e barre degli strumenti sono definiti nel file vsct che fa parte di progetti di VSPackage. È possibile trovare informazioni sull'IDE di Visual Studio e il file con estensione vsct in [come VSPackage aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Gli argomenti seguenti illustrano come aggiungere diversi tipi di comandi, menu e barre degli strumenti.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Aggiunta di un menu alla barra dei menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Viene illustrato come aggiungere un menu in alto barra dei menu di Visual Studio.  
  
 [Associazione di scelte rapide da tastiera a voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Viene illustrato come aggiungere un tasto di scelta rapida (ad esempio CTRL + 3) a una voce di menu.  
  
 [Aggiunta di un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Viene illustrato come aggiungere un sottomenu al menu principale.  
  
 [Aggiunta di un elenco usato più di recente a un sottomenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Viene illustrato come aggiungere un elenco di usati di recente.  
  
 [Creazione di gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md)  
 Viene descritto come raggruppare gli elementi di comando in modo che possono essere inclusi in più menu.  
  
 [Aggiunta di icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md)  
 Viene descritto come aggiungere un'icona per un comando su una barra degli strumenti sia un menu.  
  
 [Modifica del testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Viene descritto come utilizzare il `TextChanges` flag per abilitare una voce di menu da modificare in modo dinamico.  
  
 [Modifica dell'aspetto di un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Viene descritto come abilitare o disabilitare un comando dinamicamente.  
  
 [Aggiornamento dell'interfaccia utente](../extensibility/updating-the-user-interface.md)  
 Viene descritto come forzare un aggiornamento dell'interfaccia utente in modo da riflettere le modifiche recenti.  
  
 [Localizzazione dei comandi di menu](../extensibility/localizing-menu-commands.md)  
 Viene illustrato come localizzare i comandi di menu.  
  
## <a name="related-sections"></a>Sezioni correlate