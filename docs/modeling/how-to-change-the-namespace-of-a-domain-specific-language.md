---
title: 'Procedura: modificare lo spazio dei nomi di un linguaggio specifico di dominio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1963502f3940fd0d17c770f111e07de14207e687
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948262"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedura: modificare lo spazio dei nomi di un linguaggio specifico di dominio
È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio. È necessario apportare la modifica di **Esplora DSL**, nelle proprietà del progetto Dsl pacchetto e le informazioni sull'assembly.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Per modificare lo spazio dei nomi di un linguaggio specifico di dominio

1.  In **Esplora DSL**, fare clic su di **Dsl** nodo.

2.  Nel **proprietà** finestra, modifica il **Namespace** proprietà.

3.  Salvare la soluzione e trasformare i modelli.

4.  Nel **progetto** menu, fare clic su **proprietà Dsl**.

     Vengono visualizzate le proprietà per il progetto.

5.  Fare clic sulla scheda **Applicazione** .

6.  Modifica il **spazio dei nomi predefinito** proprietà per il nuovo nome dello spazio dei nomi.

7.  Se si desidera modificare il nome dell'assembly, modificare il **proprietà nome Assembly.**

8.  Se è stato modificato il nome dell'Assembly, aprire DslPackage\Package.tt e aggiornare questa riga:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se si scrive codice personalizzato, assicurarsi di modificare i riferimenti di classe e spazio dei nomi nei file di codice.

10. Reimpostare l'istanza sperimentale di Visual Studio.

    1.  Eliminare **\Users\\ ***{nome}*** \AppData\Local\Microsoft\VisualStudio\\\*Exp**

    2.  Di Windows **avviare** menu, scegliere **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**, **reimpostare il Istanza sperimentale**.

11. Nel **compilare** menu, scegliere **Ricompila soluzione**.

## <a name="see-also"></a>Vedere anche

- [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)