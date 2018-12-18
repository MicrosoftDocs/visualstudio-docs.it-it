---
title: Creazione di istanze di progetto tramite le factory progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3a59eee6701caf0b4d3b56df273b280f8bf6ece
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-project-instances-by-using-project-factories"></a>Creazione di istanze di progetto tramite le factory di progetto
Tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzare un *factory del progetto* per creare istanze di oggetti del progetto. Una factory del progetto è simile a una factory di classe standard per gli oggetti COM cocreatable. Oggetti del progetto non sono tuttavia cocreatable: possono essere creati solo tramite una factory del progetto.  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE chiama la factory del progetto implementata nel pacchetto VSPackage quando un utente carica un progetto esistente o crea un nuovo progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il nuovo oggetto di progetto offre l'IDE con le informazioni necessarie per il popolamento di Esplora soluzioni. Il nuovo oggetto di progetto fornisce inoltre le interfacce necessarie per il supporto di tutte le azioni dell'interfaccia utente rilevanti avviate dall'IDE.  
  
 È possibile implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaccia in una classe nel progetto. In genere, si trova nel proprio modulo.  
  
 Per un esempio di un'implementazione del `IVsProjectFactory` interfaccia, vedere PrjFac.cpp contenuti nel [progetto di base](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) directory di esempio.  
  
 I progetti che supportano l'aggregazione da un proprietario devono mantenere una chiave del proprietario nel proprio file di progetto. Quando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metodo viene chiamato su un progetto con una chiave di proprietario, il progetto proprietà converte la relativa chiave proprietario una factory del progetto GUID chiama quindi il `CreateProject` metodo su questo factory del progetto per eseguire la creazione effettiva.  
  
## <a name="creating-an-owned-project"></a>Creazione di un progetto di proprietà  
 Un proprietario viene creato un progetto di proprietà in due fasi:  
  
1.  Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metodo. In questo modo il proprietà progetto per creare un oggetto di progetto aggregato in base a cui il controllo di input `IUnknown`. Il progetto proprietà passa interna `IUnknown` e l'oggetto aggregato al progetto proprietario. In questo modo il progetto di proprietà per l'archiviazione interna `IUnknown`.  
  
2.  Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metodo. Proprietà progetto esegue tutti relativa istanza quando questo metodo viene chiamato anziché chiamare `IVsProjectFactory::CreateProject` come nel caso per i progetti che non sono di proprietà. L'input `VSOWNEDPROJECTOBJECT` enumerazione è in genere il progetto di proprietà aggregato. Il proprietà di progetto è possibile usare questa variabile per determinare se è già stato creato il relativo oggetto di progetto (cookie diverso da NULL) o deve essere creato (cookie uguale a NULL).  
  
 Tipi di progetto vengono identificati da un GUID, simile al CLSID di un oggetto COM cocreatable univoco del progetto. In genere, gli handle di factory di un progetto creazione di istanze di un singolo tipo di progetto, anche se è possibile disporre di una factory del progetto gestiscono più di un tipo di progetto GUID.  
  
 Tipi di progetto sono associati a un'estensione di file specifico. Quando un utente tenta di aprire un file di progetto esistente o tenta di creare un nuovo progetto tramite la clonazione di un modello, l'IDE Usa l'estensione del file per determinare il GUID di progetto corrispondente.  
  
 Non appena l'IDE determina che se è necessario creare un nuovo progetto o aprire un progetto esistente di un determinato tipo, per individuare l'IDE utilizza le informazioni nel Registro di sistema in [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] Pacchetto VSPackage implementa la factory del progetto richiesto. L'IDE carica il pacchetto VSPackage. Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> (metodo), il pacchetto VSPackage deve registrare la factory del progetto con l'IDE chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metodo.  
  
 Il metodo principale di `IVsProjectFactory` interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> che deve gestire due scenari: apertura di un progetto esistente e creare un nuovo progetto. La maggior parte dei progetti di archiviano il proprio stato di progetto in un file di progetto. In genere, i nuovi progetti vengono creati da rendere una copia del file di modello passata per il `CreateProject` (metodo) e quindi aprire la copia. Progetti esistenti vengono create istanze tramite direttamente l'apertura del file di progetto passato a `CreateProject` metodo. Il `CreateProject` metodo consente di visualizzare altre funzionalità dell'interfaccia utente per l'utente in base alle esigenze.  
  
 Un progetto può inoltre non utilizzare alcun file e, invece di archiviare lo stato del progetto in un meccanismo di archiviazione diverso dal file system, ad esempio un database o un server Web. In questo caso, il parametro di nome file passato al `CreateProject` metodo non è effettivamente un percorso del file system, ma una stringa univoca, ovvero un URL, per identificare i dati del progetto. Non è necessaria copiare i file di modello che vengono passati a `CreateProject` per attivare la sequenza di costruzione appropriata da eseguire.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)