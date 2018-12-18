---
title: Creazione di un progetto personalizzato e modelli di elemento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc866c9a0cd5f3aaaa06e5bc59ea2427cc86268a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-custom-project-and-item-templates"></a>Creazione di un progetto personalizzato e modelli di elemento

Visual Studio SDK include modelli di progetto che creano un modello di progetto personalizzato e un modello di elemento personalizzati. Questi modelli includono alcune sostituzioni di parametro comune e compilare come file zip. Non vengono distribuiti automaticamente e non sono disponibili nell'istanza sperimentale. È necessario copiare il file zip generati alla directory di modello di utente.
  
I modelli di creazione del modello consentono di includere modelli nelle estensioni di dimensioni maggiori. Ciò consente di implementare il controllo della versione nel file di origine e creare un gruppo di progetti di modello in un pacchetto VSIX.  
  
È anche possibile configurare un modello per installare i pacchetti NuGet. Per ulteriori informazioni, vedere [pacchetti NuGet in modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Per gli scenari di creazione di modelli di base, è necessario utilizzare il **Esporta modello** guidata, l'output in un file compresso. Per ulteriori informazioni sulla creazione di modelli di base, vedere [creazione Project and Item Templates](../ide/creating-project-and-item-templates.md).  

> [!NOTE]
> A partire da Visual Studio 2017, l'analisi per un progetto personalizzato e modelli di elementi verrà non verrà eseguita. Al contrario, l'estensione è necessario fornire file manifesto che descrivono il percorso di installazione di questi modelli. Per aggiornare le estensioni VSIX, è possibile utilizzare Visual Studio 2017. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per ulteriori informazioni, vedere [aggiornamento progetto personalizzato e i modelli di Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schema del modello di manifesto è documentato [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="creating-a-project-template"></a>Creazione di un modello di progetto  
  
1.  Creare un progetto di modello di progetto. È possibile trovare il modello di progetto di **nuovo progetto** finestra di dialogo, in Visual Basic o Visual c# **estendibilità** cartella.  
  
     Il modello genera un file di classe, un'icona, un file con estensione vstemplate, un file di progetto modificabile denominato ProjectTemplate o csproj e alcuni file che in genere vengono generati in altri tipi di progetto, tali un file resx, un AssemblyInfo file e un file. Settings. Ogni file di codice contiene le sostituzioni di parametro comune dove appropriato.  
  
2.  Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto. Non rimuovere il file di progetto modificabile, il file AssemblyInfo o del file. vstemplate.  
  
3.  Aggiornare il file con estensione vstemplate per riflettere le aggiunte ed eliminazioni. Il [progetto](../extensibility/project-element-visual-studio-templates.md) elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elemento per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altri contenuti rivolta all'utente e aggiungere le sostituzioni di parametro appropriato.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea un file con estensione zip che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="creating-an-item-template"></a>Creazione di un modello di elemento  
  
1.  Creare un progetto di modello di elemento.  
  
     Il modello genera un file di classe, un'icona, un file con estensione vstemplate e un file AssemblyInfo. Il file di classe contiene alcune sostituzioni di parametro comune.  
  
2.  Aggiungere e rimuovere elementi dal progetto come richiesto per il progetto.  
  
3.  Aggiornare il file con estensione vstemplate per riflettere le aggiunte ed eliminazioni. Il [progetto](../extensibility/project-element-visual-studio-templates.md) elemento deve contenere un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elemento per ogni file da includere nel modello.  
  
4.  Modificare i file del codice e altri contenuti rivolta all'utente e aggiungere le sostituzioni di parametro appropriato.  
  
5.  Modificare il contenuto generato in base alle esigenze.  
  
6.  Compilare il progetto.  
  
     Visual Studio crea un file compresso che contiene il modello. Non è stato distribuito e non è disponibile nell'istanza sperimentale.  
  
## <a name="deployment"></a>Distribuzione  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Per distribuire il modello di progetto o un elemento  
  
1.  Creare un progetto VSIX. Per ulteriori informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
2.  Impostare il progetto VSIX come progetto di avvio. Nel **Esplora**, selezionare il nodo del progetto VSIX, pulsante destro del mouse e selezionare **imposta come progetto di avvio**.  
  
3.  Impostare il progetto di modello di progetto come un asset del progetto VSIX. Aprire il file con estensione vsixmanifest. Passare al **asset** scheda e fare clic su **New**.  
  
    1.  Impostare il **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Per origine, selezionare il **un progetto nella soluzione corrente** opzione e quindi selezionare il progetto che contiene il modello.  
  
4.  Compilare la soluzione, quindi premere F5. Viene visualizzata l'istanza sperimentale.  
  
5.  Per un progetto di modello di progetto, si dovrebbe vedere il modello di progetto elencato nel **nuovo progetto** finestra di dialogo (**File > Nuovo > progetto**), nel nodo Visual Basic o Visual c#. Per un progetto di modello di elemento, verrà visualizzato il modello di elemento elencato nella finestra di dialogo Aggiungi nuovo elemento (nel **Esplora**, selezionare il nodo del progetto e scegliere **Aggiungi / nuovo elemento**).  
  
## <a name="see-also"></a>Vedere anche

[Riferimenti di modelli di Visual Studio](../ide/visual-studio-template-reference.md)  
[Pacchetti NuGet in modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)