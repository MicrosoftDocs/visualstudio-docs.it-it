---
title: Decisioni di progettazione di tipo di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6649bd45aba299514b40e74b5683368bfd92b41
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="project-type-design-decisions"></a>Decisioni di progettazione di tipo di progetto
Prima di creare un nuovo tipo di progetto, è necessario prendere decisioni di progettazione diverse per quanto riguarda il tipo di progetto. È necessario decidere quali tipi di elementi che contengono i progetti, come i file di progetto verranno resi persistenti e il modello di impegno verrà utilizzato.  
  
## <a name="project-items"></a>Elementi di progetto  
 Il progetto utilizzerà i file o oggetti astratti? Se si utilizzano file, sarà sono file basati su directory o riferimento? Sono il file o oggetti astratti accade sia locale o remoto?  
  
 Gli elementi in un progetto possono essere file, o possono essere oggetti più astratti, ad esempio gli oggetti in un database repository o le connessioni dati attraverso la rete Internet. Se gli elementi sono file, il progetto può essere basato sul riferimento o un progetto basato su directory.  
  
 Nei progetti di riferimento basati su elementi possono comparire in più di un progetto. Tuttavia, il file effettivo che rappresenta un elemento si trova in una directory solo. Nei progetti di directory basato su tutti gli elementi di progetto esistono nella struttura di directory.  
  
 Gli elementi locali vengono archiviati nello stesso computer in cui è installata l'applicazione. Elementi remoti possono essere archiviati in un server separato in una rete locale o in un' posizione su Internet.  
  
## <a name="project-file-persistence"></a>Persistenza del File di progetto  
 Dati verranno archiviati in file flat System comuni o nell'archiviazione strutturata? Sarà possibile aprire i file utilizzando un editor standard o un editor specifico del progetto?  
  
 Per mantenere i propri dati, la maggior parte delle applicazioni salvare i dati in un file e quindi leggerlo quando un utente deve rivedere o modificare le informazioni.  
  
 Archiviazione strutturata, denominato anche file compositi, è in genere utilizzata quando diversi oggetti modello COM (Component Object) necessario archiviare i dati persistenti in un singolo file. Con archiviazione strutturata, diversi componenti software diversi possono condividere un singolo file su disco.  
  
 Sono disponibili diverse opzioni per tenere in considerazione per la persistenza per gli elementi del progetto. È possibile eseguire una delle opzioni seguenti:  
  
-   Salvare singolarmente ogni file quando è stato modificato.  
  
-   Numero di transazioni in un'unica acquisire **salvare** operazione.  
  
-   Salvare file in locale, quindi pubblicare in un server o utilizzare un altro approccio per il salvataggio di elementi di progetto quando l'elemento rappresenta una connessione dati a un oggetto remoto.  
  
 Per ulteriori informazioni sulla persistenza, vedere [persistenza del progetto](../../extensibility/internals/project-persistence.md) e [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modello di progetto impegno  
 Oggetti dati persistenti da aprire in modalità diretta o in modalità transazionale?  
  
 Quando gli oggetti dati vengono aperti in modalità diretto, sono state incorporate le modifiche apportate ai dati immediatamente o quando l'utente salva manualmente il file.  
  
 Quando gli oggetti dati vengono aperti con modalità di transazione, le modifiche vengono salvate in un percorso temporaneo in memoria e non vengono eseguito il commit fino a quando l'utente sceglie manualmente salvare il file. In quel momento, tutte le modifiche devono verificarsi insieme o non verrà apportata alcuna modifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistenza del progetto](../../extensibility/internals/project-persistence.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)