---
title: Panoramica sull'integrazione di controllo dell'origine | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d75936e21729729dfeafaa041d800acbe01caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-integration-overview"></a>Panoramica sull'integrazione di controllo di origine
Questa sezione vengono confrontate due modi per integrare nel controllo del codice sorgente Visual Studio; un controllo del codice sorgente plug-in e da un VSPackage che offre una soluzione di controllo di origine e vengono evidenziate le nuove funzionalità di controllo di origine. Visual Studio consente di passaggio manuale da controllo del codice sorgente VSPackage e plug-in del controllo codice sorgente, nonché di commutazione automatica basata sulla soluzione.  
  
## <a name="source-control-integration"></a>Integrazione del controllo codice sorgente  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due tipi di opzioni di integrazione di controllo di origine. Tutte le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è comunque possibile integrare un plug-in basata sull'origine controllo plug-in API (in precedenza definita anche come API MSSCCI), che fornisce funzionalità di controllo di origine di base durante l'utilizzo (interfaccia utente di Visual Studio origine controllo INTERFACCIA UTENTE). Un controllo del codice sorgente VSPackage, d'altra parte, fornisce una nuova, integrazione di deep [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] percorso adatto per l'integrazione del controllo codice sorgente che richiede un elevato livello di complessità e autonomia nel modello di controllo di origine.  
  
 ![Cenni preliminari sul controllo di origine](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in controllo del codice sorgente  
 Tutte le versioni di Visual Studio supportano l'API di plug-in controllo di origine specifica versione 1.2 come un percorso di integrazione. Un implementatore di plug-in del controllo origine scrive una DLL che implementa le funzioni API plug-in controllo di origine per l'integrazione del controllo codice sorgente e la registrazione, come descritto in [la creazione di un plug-in controllo origine](../../extensibility/internals/creating-a-source-control-plug-in.md). In questo approccio, l'ambiente di sviluppo integrato (IDE) usa il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per le finestre di dialogo, ad esempio archiviazione, estrazione, pagine delle proprietà di opzioni, barre degli strumenti e icone dei controlli di origine. Una stretta osservanza all'API di plug-in del controllo origine assicura una facile integrazione in Visual Studio e un'esperienza senza problemi per l'utente. Ciò significa che il plug-in controllo del codice sorgente è necessario implementare la maggior parte delle funzioni di callback dettagliate nell'API e viceversa.  
  
 Per implementare un controllo del codice sorgente plug-in tramite l'API plug-in controllo di origine, seguire questi passaggi:  
  
1.  Creare una DLL che implementa le funzioni specificate nel [Plug-in controllo del codice sorgente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrare la DLL apportando le voci del Registro di sistema appropriata (descritto in [procedura: installare un plug-in controllo origine](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Creare un supporto di interfaccia utente e la visualizzazione quando viene richiesto il pacchetto di scheda di controllo di origine (il componente di Visual Studio che gestisce controllo del codice sorgente tramite plug-in del controllo codice sorgente)  
  
 In risposta a un comando di controllo di origine, l'IDE di Visual Studio presenta un'interfaccia utente standard per le operazioni di base e quindi passa le informazioni per il controllo del codice sorgente plug-in tramite le funzioni definite nell'API di plug-in del controllo origine. Per le opzioni avanzate, il plug-in controllo del codice sorgente può essere chiamato su per presentare la propria interfaccia utente, ad esempio, la ricerca di un progetto di controllo del codice sorgente. Ciò significa che l'utente potrebbe essere presentato due probabilmente diversi stili dell'interfaccia utente quando si lavora con controllo del codice sorgente: l'interfaccia utente presentato in Visual Studio e l'interfaccia utente che presenta il plug-in controllo del codice sorgente. Questo è particolarmente evidente con operazioni di controllo avanzati.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Svantaggi di implementazione di un plug-in controllo del codice sorgente  
  
-   Per le funzionalità avanzate, l'utente può visualizzare due diversi stili di interfacce, causando confusione.  
  
-   Il plug-in controllo del codice sorgente è limitata al modello di controllo di origine in cui è inclusa l'API plug-in controllo di origine.  
  
-   L'API plug-in controllo di origine potrebbero essere troppo restrittivo per alcuni scenari di controllo di origine.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantaggi dell'implementazione di un plug-in controllo del codice sorgente  
  
-   Visual Studio fornisce l'interfaccia utente per tutte le operazioni di controllo di origine di base in modo che il plug-in controllo del codice sorgente non è necessario implementare potenzialmente complesse dell'interfaccia utente.  
  
-   A causa di API strict, il plug-in controllo del codice sorgente può interagire facilmente con i programmi di controllo origine esterna per fornire funzionalità più estesa. Visual Studio non è rilevante troppo molto come il controllo del codice sorgente viene eseguita, solo che viene eseguita in base alle API plug-in controllo di origine.  
  
-   Risulta più semplice implementare un controllo del codice sorgente plug-in di un controllo del codice sorgente VSPackage.  
  
## <a name="source-control-vspackage"></a>Origine pacchetto VSPackage di controllo  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Consente l'integrazione completa in Visual Studio con il controllo completo del controllo del codice sorgente e la sostituzione completa dell'interfaccia utente controllo origine fornite da Visual Studio. Un controllo del codice sorgente VSPackage è registrato con Visual Studio e fornisce funzionalità di controllo di origine. Benché il controllo del codice sorgente diversi pacchetti VSPackage può essere registrato con Visual Studio, solo uno di essi può essere attivo in qualsiasi momento. Un controllo del codice sorgente VSPackage dispone del controllo completo sul controllo del codice sorgente e l'aspetto in Visual Studio mentre è attiva. Tutti gli altri controllo del codice sorgente pacchetti VSPackage che possono essere registrati nel sistema sono inattivo e non verrà visualizzata qualsiasi interfaccia utente del tutto.  
  
 L'implementazione di un controllo del codice sorgente VSPackage richiede una strategia di "tutto o niente". L'autore di un controllo del codice sorgente VSPackage necessario investire una quantità significativa di lavoro richiesto nell'implementazione di un numero di interfacce di controllo di origine e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intero di controllo del codice sorgente. Vedere [creando un pacchetto VSPackage controllo origine](../../extensibility/internals/creating-a-source-control-vspackage.md) per altri dettagli.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Svantaggi di implementazione di un VSPackage di controllo di origine  
  
-   Il pacchetto VSPackage deve implementare un numero di interfacce complesse per integrare correttamente con Visual Studio.  
  
-   Il pacchetto VSPackage deve fornire tutte l'interfaccia utente necessaria per controllo del codice sorgente; Visual Studio non assistenza in questa area.  
  
-   Un controllo del codice sorgente VSPackage è strettamente correlati a Visual Studio e non può funzionare con programmi autonomi, funzionalità non è necessario condividere la stessa facilità con una versione del programma di controllo di origine esterna.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantaggi dell'implementazione di un VSPackage di controllo di origine  
  
-   Poiché il pacchetto VSPackage dispone di funzionalità e controllo completo per il controllo del codice sorgente dell'interfaccia utente, viene visualizzato l'utente con un'interfaccia intuitiva per controllo del codice sorgente.  
  
-   Il pacchetto VSPackage non è limitato a un modello di controllo specifico di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)   
 [Creazione di plug-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creazione di un VSPackage di controllo di origine](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Novità del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-source-control.md)