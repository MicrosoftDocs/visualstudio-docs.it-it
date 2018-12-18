---
title: 'Procedura: modificare Namespace di un linguaggio specifico di dominio | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 468cf24ccb16452c93583b2aa99af560d920bcf4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
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
  
    1.  Eliminare **\Users\\***{nome}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Di Windows **avviare** menu, scegliere **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**, **reimpostare il Istanza sperimentale**.  
  
11. Nel **compilare** menu, scegliere **Ricompila soluzione**.  
  
## <a name="see-also"></a>Vedere anche

[Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)