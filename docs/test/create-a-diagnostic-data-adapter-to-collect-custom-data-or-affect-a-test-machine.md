---
title: Creare un adattatore dati di diagnostica per l'esecuzione di test in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 0410fd52e115e2c2c257811e088c46a831d0082d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Creare un adattatore dati di diagnostica per raccogliere dati personalizzati o influire su un computer di test

È possibile creare un adattatore dati di diagnostica personalizzato per raccogliere dati durante un test oppure per influire sul computer di test come parte del test. Potrebbe essere necessario, ad esempio, raccogliere i file di log creati dall'applicazione sottoposta a test e allegarli ai risultati del test oppure eseguire i test quando lo spazio su disco sul computer è insufficiente. Usando le API disponibili in Visual Studio Enterprise, è possibile scrivere codice per eseguire attività in punti specifici dell'esecuzione dei test. È possibile, ad esempio, eseguire le attività prima di iniziare a eseguire i test, dopo il completamento dei test, prima o dopo l'esecuzione di ogni singolo test.

È possibile fornire input predefinito all'adattatore dati di diagnostica personalizzato tramite un file delle impostazioni di configurazione. È possibile, ad esempio, fornire informazioni sulla posizione del file che si desidera raccogliere e allegare ai risultati del test o su quanto spazio su disco si desidera lasciare nel sistema. È possibile configurare questi dati per ciascuna impostazione di test creata. Possono essere visualizzati e modificati tramite l'editor predefinito disponibile in Microsoft test Manager oppure è possibile creare un controllo utente personalizzato da usare come editor. Qualsiasi modifica apportata alla configurazione dell'adattatore nell'editor viene archiviata con le impostazioni di test.

Se i test vengono eseguiti da Visual Studio, è necessario impostare come attive queste impostazioni di test. Per altre informazioni sulle impostazioni test, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

## <a name="tasks"></a>Attività

 Utilizzare gli argomenti seguenti per creare adattatori dati di diagnostica:

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Creazione di un adattatore dati di diagnostica:** si crea un adattatore dati di diagnostica creando una libreria di classi, quindi si usano le API dell'adattatore dati di diagnostica per raccogliere le informazioni necessarie o per influire su un sistema di test usato per eseguire i test.|-   [Procedura: Creare un adattatore dati di diagnostica](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Installazione di un adattatore dati di diagnostica personalizzato:** è possibile installare l'adattatore dati di diagnostica o un adattatore di un altro utente, copiandolo nella directory corretta.|-   [Procedura: Installare un adattatore dati di diagnostica personalizzato](../test/how-to-install-a-custom-diagnostic-data-adapter.md)|
|**Selezione di un adattatore dati di diagnostica personalizzato da usare durante l'esecuzione dei test:** è possibile stabilire quale adattatore dati di diagnostica usare per le impostazioni test, in modo che venga usato quando si eseguono i test.|-   [Raccogliere dati di diagnostica durante i test (VSTS)](/vsts/manual-test/collect-diagnostic-data)<br />-   [Raccogliere dati di diagnostica nei test manuali (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|
|**Configurazione delle operazioni eseguite da un adattatore dati di diagnostica:** è possibile configurare le impostazioni per controllare le azioni dell'adattatore dati di diagnostica nelle impostazioni di test specifiche.|-   [Procedura: Creare un editor personalizzato di dati per l'adattatore dati di diagnostica](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)|

## <a name="see-also"></a>Vedere anche

- [Esempio di progetto per creare un adattatore dati di diagnostica](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Raccogliere dati di diagnostica tramite impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)