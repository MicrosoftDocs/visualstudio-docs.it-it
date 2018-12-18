---
title: Installare framework di unit test di terze parti in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 93502e0d3a3425c4debcff4f181263dc4e58d9b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="install-third-party-unit-test-frameworks"></a>Installare framework di unit test di terze parti

Esplora test di Visual Studio può eseguire qualsiasi framework di unit test che ha sviluppato un'interfaccia di adattatore per Esplora test. Il programma di installazione del framework installa i file binari e aggiunge modelli di progetto di Visual Studio per i linguaggi supportati. Quando si crea un progetto con il modello, il framework viene registrato con Esplora test. Una soluzione di Visual Studio può includere progetti unit test che usano diversi framework e fanno riferimento a diversi linguaggi. Esplora test li esegue tutti.

## <a name="acquiring-third-party-frameworks"></a>Acquisizione di framework di terze parti

È possibile scaricare e installare molti framework di unit test di terze parti usando Gestione estensioni di Visual Studio o da Visual Studio Marketplace. I framework sono disponibili per il download anche da altri siti, ad esempio il sito Web specifico del framework.

### <a name="installing-from-visual-studio"></a>Installazione da Visual Studio

1. Scegliere **Strumenti** nel menu standard e quindi **Estensioni e aggiornamenti**.

2. Espandere **Online** > **Visual Studio Marketplace** > **Strumenti**. Scegliere **Test**.

3. Cercare il framework nell'elenco.

4. Selezionare il framework e scegliere **Download**.

Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Installazione dal Web

Se si conosce il framework che si vuole usare:

1. Aprire [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Digitare il nome del framework nella casella **Trova**.

3. Scegliere il framework dall'elenco di risultati per passare alla pagina di Visual Studio Marketplace per lo strumento.

Per sfogliare un elenco di framework e di altri strumenti di test:

1. Aprire [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. In **Filtra per categoria/raccolta** scegliere **Visualizza tutto**.

3. Nell'elenco **Categoria** con etichetta **Visualizzazione di**, espandere il nodo **Strumenti** e scegliere **Test**.

4. Scegliere un framework dall'elenco di risultati per passare alla pagina di Visual Studio Marketplace per lo strumento.

## <a name="see-also"></a>Vedere anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
