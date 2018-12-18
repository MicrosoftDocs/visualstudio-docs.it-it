---
title: Opzioni, Editor di testo, XAML, Formattazione | Microsoft Docs
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: 2ba33419f0d1d69a65b494149798fefc8a7dcb6d
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="options-text-editor-xaml-formatting"></a>Opzioni, Editor di testo, XAML, Formattazione
Usare la pagina delle proprietà **Formattazione** per specificare la formattazione di elementi e attributi nei documenti XAML. Per aprire la finestra di dialogo **Opzioni**, fare clic sul menu **Strumenti** e quindi su **Opzioni**. Per accedere alla finestra delle proprietà **Formattazione**, espandere **Editor di testo**, **XAML** e il nodo **Formattazione**.  

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="auto-formatting-events"></a>Eventi di formattazione automatica  
 La formattazione automatica può verificarsi quando vengono rilevati gli eventi seguenti.  

-   Completamento di un tag di fine o un tag semplice.  

-   Completamento di un tag di inizio.  

-   Inserimento degli Appunti.  

-   Formattazione di comandi da tastiera.  

È possibile specificare gli eventi che causano la formattazione automatica.  

|||  
|-|-|  
|**Al completamento del tag di fine o del tag semplice**|La formattazione automatica si verifica quando si finisce di digitare un tag di fine o un tag semplice. Un tag semplice non include attributi, ad esempio `<Button />`.|  
|**Al completamento del tag di inizio**|La formattazione automatica si verifica quando si finisce di digitare un tag di inizio.|  
|**All'inserimento degli Appunti**|La formattazione automatica si verifica quando si incolla XAML dagli Appunti nella visualizzazione XAML.|  

## <a name="quotation-mark-style"></a>Stile virgolette  
 Questa impostazione indica se i valori di attributo sono racchiusi tra virgolette singole o doppie. Il formattatore automatico e il completamento automatico IntelliSense usano questa impostazione.  

 Dopo l'impostazione, questa opzione viene applicata solo agli attributi aggiunti successivamente usando la finestra di progettazione o manualmente nella visualizzazione XAML.  

|||  
|-|-|  
|**Virgolette doppie (")**|I valori di attributo sono racchiusi tra virgolette doppie.<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**Virgolette singole (')**|I valori di attributo sono racchiusi tra virgolette singole.<br /><br /> `<Button Name='button1'>Hello</Button>`|  

## <a name="tag-wrapping"></a>Ritorno a capo dei tag  
 È possibile specificare una lunghezza di riga per il ritorno a capo dei tag. Quando il ritorno a capo dei tag è abilitato, verrà applicato il ritorno a capo appropriato a qualsiasi XAML aggiunto successivamente usando la finestra di progettazione.  

|||  
|-|-|  
|**Testo a capo per i tag che eccedono la lunghezza specificata**|Specifica se il ritorno a capo viene applicato alle righe alla lunghezza di riga specificata da **Lunghezza**.|  
|**Lunghezza**|Il numero di caratteri che una riga può contenere. Se necessario, alcune righe XAML possono superare la lunghezza di riga specificata.|  

## <a name="attribute-spacing"></a>Spaziatura attributi  
 Usare questa impostazione per controllare la disposizione degli attributi nel documento XAML  

|||  
|-|-|  
|**Conserva i caratteri di fine riga e gli spazi tra gli attributi**|La formattazione automatica non viene applicata ai caratteri di fine riga e agli spazi tra gli attributi.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Inserisci uno spazio singolo tra gli attributi**|Gli attributi occupano una riga, con uno spazio che separa gli attributi adiacenti. Vengono applicate le impostazioni di ritorno a capo dei tag.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**Posiziona ogni attributo su una riga diversa**|Ogni attributo occupa una riga. Ciò è utile quando presenti molti attributi.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Posiziona il primo attributo sulla stessa riga del tag di inizio**|Se questa opzione è selezionata, il primo attributo viene visualizzato sulla stessa riga del tag di inizio dell'elemento.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  

## <a name="element-spacing"></a>Spaziatura elementi  
 Usare questa impostazione per controllare la disposizione degli elementi nel documento XAML  

|||  
|-|-|  
|**Conserva i caratteri di fine riga nel contenuto**|Le righe vuote nel contenuto dell'elemento non vengono rimosse.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Comprimi più righe vuote nel contenuto in una sola riga**|Le righe vuote nel contenuto dell'elemento vengono compresse in una singola riga.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Rimuovi le righe vuote nel contenuto**|Tutte le righe vuote nel contenuto dell'elemento vengono rimosse.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|  

## <a name="miscellaneous-section-auto-insert"></a>Sezione Varie, Inserimento automatico  
 Usare questa impostazione per controllare la generazione automatica di tag e virgolette.  

|||  
|-|-|  
|**Tag di chiusura**|Specifica se il tag di chiusura di un elemento viene generato automaticamente quando si chiude il tag di apertura con il carattere maggiore di (>).|  
|**Virgolette per gli attributi**|Specifica se vengono generate le virgolette quando un valore di attributo viene selezionato dall'elenco a discesa Completamento istruzioni.|  
|**Parentesi graffe di chiusura per MarkupExtensions**|Specifica se una parentesi graffa di chiusura dell'estensione del markup (}) viene generata automaticamente quando si digita il carattere di parentesi graffa di apertura ({).|  
|**Virgole per separare i parametri di MarkupExtension**|Specifica se vengono generate le virgole quando si digita più di un parametro in un'estensione di markup.|  

## <a name="see-also"></a>Vedere anche

[XAML in WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
