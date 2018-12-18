---
title: Opzioni, Editor di testo, C#, Avanzate | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0df7b6b38f8982e92d3b7cdee3165ae19e5567a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-c-advanced"></a>Opzioni, Editor di testo, C#, Avanzate

Usare la pagina di opzioni **Avanzate** per modificare le impostazioni di formattazione dell'editor, di refactoring del codice e dei commenti in formato documentazione XML per C#. Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** e quindi scegliere **Editor di testo** > **C#** > **Avanzate**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="analysis"></a>Analisi

- Abilita analisi della soluzione completa

   Abilita l'analisi del codice per tutti i file nella soluzione e non solo per i file di codice aperti. Per altre informazioni, vedere [Analisi della soluzione completa](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

- Esegui analisi delle funzionalità dell'editor in processo esterno (sperimentale)

## <a name="using-directives"></a>Direttive using

- Inserisci prima le direttive 'System' durante l'ordinamento delle direttive using

- Separa gruppi di direttive using

- Suggerisci le direttive using per i tipi in assembly di riferimento

- Suggerisci le direttive using per i tipi in pacchetti NuGet

## <a name="highlighting"></a>Evidenziazione

- Evidenzia riferimenti a simbolo sotto il cursore

   Quando il cursore viene posizionato all'interno di un simbolo o quando si fa clic su un simbolo, vengono evidenziate tutte le istanze del simbolo nel file di codice.

- Evidenzia parole chiave correlate sotto il cursore

## <a name="outlining"></a>struttura

- Attiva modalità struttura all'apertura del file

   Se selezionata, visualizza automaticamente la struttura del file di codice che consente di creare blocchi comprimibili del codice. Alla prima apertura di un file, i blocchi #regions e i blocchi di codice inattivi vengono compressi.

- Mostra separatori di riga routine

- Mostra la struttura per i costrutti a livello di dichiarazione

- Mostra la struttura per i costrutti a livello di codice

- Mostra la struttura per i commenti e le aree del preprocessore

- Comprimi #regions durante la compressione delle definizioni

## <a name="fading"></a>Dissolvenza

- Applica dissolvenza a direttive using non usate

- Applica dissolvenza a codice non eseguibile

## <a name="block-structure-guides"></a>Guide per strutture a blocchi

- Mostra le guide per i costrutti a livello di dichiarazione

- Mostra le guide per i costrutti a livello di codice

## <a name="editor-help"></a>Guida Editor

- Genera commenti relativi alla documentazione XML per ///

   Se selezionata, questa opzione inserisce elementi XML per i commenti in formato documentazione XML dopo la digitazione dell'introduzione al commento `///`. Per altre informazioni sulla documentazione XML, vedere [Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

- Inserisci \* all'inizio di nuove righe quando si scrivono commenti /\* \*/

- Mostra anteprima per verifica ridenominazione

- Dividi valori letterali stringa dopo INVIO

- Segnala segnaposto non validi in chiamate 'string.Format'

## <a name="extract-method"></a>Estrai metodo

- Non inserire out o ref in struct personalizzato

## <a name="implement-interface-or-abstract-class"></a>Implementa interfaccia o classe astratta

- Posiziona proprietà, eventi e metodi inseriti: con altri membri dello stesso tipo o alla fine

- Durante la generazione di proprietà: preferisci proprietà generate o preferisci proprietà automatiche

## <a name="see-also"></a>Vedere anche

[Procedura: Inserire commenti XML per la generazione di documentazione](../../ide/reference/generate-xml-documentation-comments.md)  
[Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)  
[Documentazione del codice con i commenti XML (Guida per C#)](/dotnet/csharp/codedoc)  
[Impostazione delle opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)  
[IntelliSense per C#](../../ide/visual-csharp-intellisense.md)