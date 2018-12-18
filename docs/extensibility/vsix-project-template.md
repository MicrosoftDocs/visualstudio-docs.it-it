---
title: Modello di progetto VSIX | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: de8de116a9853391249a7a37a35bd54d0a6946d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-project-template"></a>Modello di progetto VSIX
È possibile utilizzare il modello di progetto VSIX per eseguire il wrapping di uno o più estensioni di Visual Studio in un progetto VSIX e quindi pubblicare il pacchetto nel [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web.  
  
 Distribuzione VSIX supporta VSPackage, assembly, MEF componenti, i modelli di progetto, modelli di elemento, i controlli della casella degli strumenti e tipi di estensione personalizzati.  
  
> [!NOTE]
>  Per utilizzare progetti VSIX, è necessario installare Visual Studio SDK. Per ulteriori informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Dove trovare il modello di progetto VSIX  
 Il modello di progetto VSIX è disponibile nel **nuovo progetto** la finestra di dialogo. Espandere il **Visual Basic** nodo o **Visual c#** nodo e quindi scegliere **estendibilità**.  
  
> [!TIP]
>  È necessario assicurarsi che .NET Framework 4.5 o successiva viene specificato nell'elenco a discesa nella parte superiore del **nuovo progetto** la finestra di dialogo.  
  
## <a name="uses-of-the-vsix-project-template"></a>Utilizzi del modello di progetto VSIX  
 Il modello di progetto VSIX ha due utilizzi principali:  
  
-   Per distribuire modelli di progetto, modelli di elementi e altre estensioni che non hanno ancora installato il supporto VSIX.  
  
-   Per eseguire il wrapping gli output di più estensioni di pacchetto di distribuzione.  
  
 Non è necessario utilizzare il modello di progetto VSIX per distribuire i pacchetti VSPackage o altri tipi di estensioni che dispongono di accordi VSIX.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Creazione di pacchetti un'estensione in un progetto VSIX vuoto  
 È possibile creare un pacchetto, un'estensione esistente o un'estensione che non dispongono di accordi VSIX, mediante il wrapping in un progetto VSIX vuoto. L'estensione di cui eseguire il wrapping deve essere di un tipo supportato dal [schema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Per creare un pacchetto di un'estensione tramite un progetto VSIX  
  
1.  Compilare i progetti che costituiscono l'estensione.  
  
2.  Creare un progetto VSIX usando il **progetto VSIX** modello.  
  
     Vsixmanifest viene aperto in **progettazione manifesto**.  
  
3.  Nel **asset** scheda, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
4.  Nel **tipo** elenco, scegliere il tipo di estensione da aggiungere.  
  
5.  Per aggiungere un elemento di estensione o il contenuto che è incluso nella soluzione corrente (ad esempio, un modello di elemento o un assembly compilato), eseguire la procedura seguente:  
  
    1.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
    2.  Nel **progetto** elenco, scegliere il nome dell'estensione.  
  
    3.  Nel **incorpora in questa cartella** , immettere il nome di una cartella in cui si desidera incorporare la risorsa e quindi scegliere il **OK** pulsante.  
  
6.  Per aggiungere un'estensione o un elemento di contenuto che non è incluso nella soluzione corrente, eseguire la procedura seguente:  
  
    1.  Nel **origine** nella casella di riepilogo, scegliere **File in filesystem**.  
  
    2.  Nel **percorso** campo, immettere il percorso completo del file di estensione compilato o compresso oppure utilizzare il **Sfoglia** pulsante per selezionare il file.  
  
    3.  Nel **incorpora in questa cartella** , immettere il nome di una cartella in cui si desidera incorporare la risorsa e quindi scegliere il **OK** pulsante.  
  
7.  Se si vuole includere estensioni aggiuntive il pacchetto, è necessario aggiungerli allo stesso modo.  
  
8.  Compilare la soluzione.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Compila un file con estensione VSIX che contiene un file manifesto VSIX, un file [Content_Types] XML e tutti gli asset di estensione che è stato aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento di Schema 2.0 estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)