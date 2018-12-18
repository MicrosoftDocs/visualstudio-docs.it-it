---
title: 'Procedura: contrassegnare i controlli come controlli sicuri | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d703beb24821663b08ed69238fcf27e2a752d64b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Procedura: contrassegnare i controlli come controlli sicuri
  Per la sicurezza, SharePoint riconosce la differenza tra i controlli Web protetti dagli attacchi script injection e Web che non sono. Controlli, protetto o *controlli sicuri*, è possibile accedere tramite gli utenti non attendibili. È possibile contrassegnare i controlli come sicuri nella proprietà di un elemento di progetto SharePoint o in voci di controllo sicure di **Progettazione pacchetti** quando si aggiunge un assembly al pacchetto. Per altre informazioni, vedere  
  
 [Modifica delle impostazioni Web. config](http://go.microsoft.com/fwlink/?LinkId=178965) e [prevede la registrazione di un Assembly Web Part come SafeControl](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Queste procedure sono solo a scopo illustrativo. Contrassegnare i controlli sicuri solo se si è certi che siano protetti.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Contrassegnare i controlli sicuri nella proprietà voci di controllo sicure  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Per contrassegnare i controlli come safe o unsafe nella proprietà voci di controllo sicure  
  
1.  Creare una soluzione di SharePoint con un progetto di Web Part visiva.  
  
2.  Aggiungere due controlli alla Web part: una casella di testo e un pulsante. Lasciare i nomi dei valori predefiniti, TextBox1 e Button1, rispettivamente.  
  
3.  Aggiungere due voci per la Web part **voci di controllo sicure** proprietà. A tale scopo, scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) accanto al pulsante il **voci di controllo sicure** proprietà il  **Proprietà** finestra.  
  
     Il **voci di controllo sicure** viene visualizzata la finestra di dialogo.  
  
4.  Nel **voci di controllo sicure** finestra di dialogo scegliere la **Aggiungi** due volte per aggiungere due voci di controllo sicure per il **membri** riquadro: uno per il pulsante e una casella di testo.  
  
5.  Scegliere la prima voce di controllo sicure e quindi modificare il valore della relativa **provvisoria** proprietà **False**, le **nome del tipo** proprietà **Button1**e il relativo **sicurezza Script** proprietà **False**.  
  
     Questo passaggio identifica il controllo pulsante come un controllo non sicuro.  
  
6.  Scegliere la seconda voce di controllo sicura nell'elenco. Lasciare il valore della relativa **sicuro** proprietà come **True** e impostare relativo **nome del tipo** proprietà **TextBox1** e il relativo **sicuro Script** proprietà **True**.  
  
     Il controllo casella di testo è ora contrassegnato come un controllo che può essere sicuro dagli attacchi script injection.  
  
7.  Scegliere il pulsante **OK** per chiudere la finestra di dialogo.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Contrassegnare i controlli sicuri nella finestra di progettazione del pacchetto  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Per contrassegnare i controlli come safe o unsafe nella finestra di progettazione del pacchetto  
  
1.  Creare una soluzione di SharePoint con un progetto di Web Part visiva.  
  
2.  Aggiungere due controlli alla Web part: una casella di testo e un pulsante. Lasciare i nomi dei valori predefiniti, TextBox1 e Button1, rispettivamente.  
  
     Prendere nota dei nomi del controllo perché è utilizzato in un secondo momento.  
  
3.  Nella barra dei menu, scegliere **compilare**, **Compila soluzione** per compilare il progetto.  
  
4.  Creare un'altra soluzione di SharePoint.  
  
5.  In **Esplora**, aprire il menu di scelta rapida per il file package. package e quindi scegliere **aprire** per aprire la **Progettazione pacchetti**.  
  
6.  Nel **Progettazione pacchetti**, scegliere il **avanzate** scheda.  
  
7.  In **assembly aggiuntivi**, scegliere il **Aggiungi** e quindi scegliere **Aggiungi Assembly esistente** dall'elenco.  
  
8.  Nel **Aggiungi Assembly esistente** finestra di dialogo scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) accanto al pulsante  **Percorso di origine**.  
  
9. Scegliere l'assembly dalla soluzione di SharePoint creato nel passaggio 1, quindi il **aprire** pulsante.  
  
10. Per questo esempio, lasciare il **destinazione distribuzione** opzione GlobalAssemblyCache.  
  
     Questo passaggio, l'assembly distribuire il sistema Global Assembly Cache (GAC). Se desideri che l'assembly da distribuire nella cartella Web dell'applicazione (. Bin), è possibile selezionare tale opzione. Per ulteriori informazioni, vedere [distribuzione di Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. Nel **controlli sicuri** scegliere il **fare clic qui per aggiungere un nuovo elemento** pulsante.  
  
12. Immettere i valori per le proprietà contenute nella tabella seguente.  
  
    |Nome proprietà|Valore|  
    |-------------------|-----------|  
    |Spazio dei nomi|Il nome completo dello spazio dei nomi per il controllo, ad esempio **BdcModelProject1.VisualWebPart1**.|  
    |Nome tipo|Button1|  
    |Nome assembly|Nome di assembly sicuro, ad esempio: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Cancella il **provvisoria** casella di controllo.|  
    |Sicurezza script|Lasciare il **sicurezza Script** casella di controllo.|  
  
    > [!NOTE]  
    >  Il **nome dell'Assembly** valore degli assembly aggiunti tramite il **avanzate** scheda della finestra il **Progettazione pacchetti** non è un token, deve essere un assembly con nome sicuro. Per altre informazioni, vedere [Creazione e utilizzo degli assembly con nome sicuro](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Scegliere il tasto TAB per creare un'altra voce di controllo sicura.  
  
14. Scegliere il **fare clic qui per aggiungere un nuovo elemento** nuovamente clic sul pulsante.  
  
15. Immettere i valori per le proprietà contenute nella tabella seguente.  
  
    |Nome proprietà|Valore|  
    |-------------------|-----------|  
    |Spazio dei nomi|Il nome completo dello spazio dei nomi per il controllo, ad esempio **BdcModelProject1.VisualWebPart1**.|  
    |Nome tipo|TextBox1|  
    |Nome assembly|Nome di assembly sicuro, ad esempio: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Selezionare il **provvisoria** casella di controllo.|  
    |Sicurezza script|Selezionare il **sicurezza Script** casella di controllo.|  
  
16. Scegliere il tasto Tab e quindi scegliere il **OK** per chiudere la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica sui pacchetti e informazioni sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  