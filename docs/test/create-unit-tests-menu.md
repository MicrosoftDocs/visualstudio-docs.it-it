---
title: Creare stub di metodo di unit test in Visual Studio | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8a5f33cfc8ebc7a45f02e3626289d496eac66e37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Creare stub di metodo di unit test con il comando Crea unit test

Il comando **Crea unit test** di Visual Studio offre la possibilità di creare stub per il metodo di unit test. Questa funzionalità consente di semplificare la configurazione di un progetto di test, della classe di test e dello stub del metodo di test all'interno di essa.

## <a name="availability-and-extensions"></a>Disponibilità ed estensioni

Il comando **Crea unit test**:

* È disponibile nelle edizioni Community, Professional ed Enterprise di Visual Studio 2015 e versioni successive.

* Supporta solo il codice C# che fa riferimento a .NET Framework.

* È estendibile e supporta l'emissione di test in formato MSTest, MSTest V2, NUnit, xUnit.

## <a name="get-started"></a>Introduzione

Per iniziare, selezionare un metodo, un tipo o uno spazio dei nomi nell'editor di codice nel progetto da testare, aprire il menu di scelta rapida e scegliere **Crea unit test**. Viene visualizzata la finestra di dialogo **Crea unit test** in cui è possibile selezionare le opzioni di creazione per i nuovi unit test.

![Uso del comando Crea unit test](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Impostazione di tratti di unit test

Se si prevede di eseguire questi test come parte del processo di automazione del test, considerare la possibilità di creare il test in un altro progetto di test (la seconda opzione nella finestra di dialogo precedente) e di impostare i tratti di unit test per lo unit test. In questo modo sarà più facile includere o escludere questi test specifici come parte di una pipeline di distribuzione continua o di integrazione continua. I tratti vengono impostati aggiungendo direttamente i metadati allo unit test, come illustrato di seguito.

![Impostazione di tratti di unit test](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>Uso di framework di unit test di terze parti

Con Visual Studio è possibile creare facilmente unit test usando qualsiasi framework di test. Per installare altri framework di test:

1. Scegliere **Strumenti** > **Estensioni e aggiornamenti**.
2. Espandere **Online** > **Visual Studio Marketplace** > **Strumenti** e scegliere **Test**.

![Uso di framework di test di terze parti](media/createunittestfx.png)

Le estensioni del framework di test sono disponibili in Visual Studio Marketplace:

* [NUnit Extension for the Test Generators](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension) (Estensione NUnit per Test Generators)
* [xUnit Extension for the Test Generators](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions) (Estensione xUnit per Test Generators)

## <a name="when-should-i-use-this-feature"></a>Quando si deve usare questa funzionalità?

Usare questa funzionalità ogni volta che è necessario creare unit test, ma in particolare quando si testa un codice esistente con pochissimo o nessun code coverage del test e senza documentazione. In altre parole, dove la specifica del codice è limitata o inesistente. Implementa in modo efficace un approccio simile agli [unit test intelligenti](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) che caratterizzano il comportamento osservato del codice.

Tuttavia, questa funzionalità può essere applicata anche alla situazione in cui lo sviluppatore inizia a scrivere e lo usa per l'avvio automatico della disciplina di unit test. All'interno del flusso di scrittura del codice, lo sviluppatore potrebbe voler creare rapidamente uno stub del metodo di unit test, con una classe di test e un progetto di test appropriati, per una parte specifica di codice.

## <a name="see-also"></a>Vedere anche

- [Creare stub di metodo di unit test con il comando Crea unit test](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Post di blog sul testing unità](https://blogs.msdn.microsoft.com/devops/?s=unit+testing)
