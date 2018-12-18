---
title: 'Procedura dettagliata: Creazione di una Web Part per SharePoint | Documenti Microsoft'
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
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e0659c354980eb302beb903d0107024882c6b160
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint"></a>Procedura dettagliata: creazione di una web part per SharePoint

Le Web part consentono agli utenti di modificare direttamente il contenuto, l'aspetto e comportamento delle pagine del sito di SharePoint utilizzando un browser. Questa procedura dettagliata viene illustrato come creare una Web Part tramite il **Web Part** modello di elemento in Visual Studio 2010.

La Web Part Mostra i dipendenti in una griglia dati. L'utente specifica il percorso del file che contiene i dati del dipendente. L'utente può anche filtrare la griglia dei dati in modo che i dipendenti che sono responsabili vengono visualizzati solo nell'elenco.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di una Web Part tramite Visual Studio **Web Part** modello di elemento.

- Creazione di una proprietà che può essere impostata dall'utente della Web Part. Questa proprietà specifica il percorso del file di dati dipendente.

- Insieme di controlli per il rendering di contenuto in una Web Part tramite l'aggiunta di controlli per la Web Part.

- Creazione di una nuova voce di menu, definito come un *verbo,* che viene visualizzato nel menu dei verbi della Web part viene eseguito il rendering. I verbi consentono all'utente di modificare i dati visualizzati nella Web Part.

- Test della Web Part in SharePoint.

    > [!NOTE]
    > I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio 2017 o un'edizione di Visual Studio Application Lifecycle Management (ALM).

## <a name="creating-an-empty-sharepoint-project"></a>Creazione di un progetto SharePoint vuoto

Innanzitutto, creare un progetto SharePoint vuoto. In un secondo momento, si aggiungerà una Web Part per il progetto utilizzando il **Web Part** modello di elemento.

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizzando il **Esegui come amministratore** opzione.

2. Sulla barra dei menu, scegliere **File**, **New**, **progetto**.

3. Nel **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo sotto il linguaggio che si desidera utilizzare e quindi scegliere il **2010** nodo.

4. Nel **modelli** riquadro scegliere **progetto SharePoint 2010**, quindi scegliere il **OK** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzato. Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

5. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.

## <a name="adding-a-web-part-to-the-project"></a>Aggiunta di una Web Part al progetto

Aggiungere un **Web Part** elemento al progetto. Il **Web Part** elemento aggiunge file di codice della Web Part. In un secondo momento, si aggiungerà codice al file di codice di Web Part per il rendering del contenuto della Web Part.

1. Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.

2. Nel **Aggiungi nuovo elemento** della finestra di dialogo di **modelli installati** riquadro espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.

3. Nell'elenco dei modelli di SharePoint, scegliere il **Web Part** modello, quindi scegliere il **Aggiungi** pulsante.

     Il **Web Part** elemento viene visualizzato **Esplora**.

## <a name="rendering-content-in-the-web-part"></a>Il rendering del contenuto in una Web Part

È possibile specificare i controlli che si desidera visualizzare nella Web Part aggiungendoli alla raccolta di controlli della classe di Web Part.

1. In **Esplora**, aprire WebPart1. vb (in Visual Basic) o WebPart1.cs (in c#).

     File di codice della Web Part verrà visualizzata nell'Editor di codice.

2. Aggiungere le istruzioni seguenti all'inizio del file di codice della Web Part.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Aggiungere il codice seguente alla classe `WebPart1`. Questo codice dichiara i campi seguenti:

    - Griglia di dati per visualizzare i dipendenti nella Web Part.

    - Testo visualizzato sul controllo che viene utilizzato per filtrare la griglia dei dati.

    - Un'etichetta che viene visualizzato un errore se la griglia dati è in grado di visualizzare i dati.

    - Stringa che contiene il percorso del file di dati dipendente.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Aggiungere il codice seguente alla classe `WebPart1`. Questo codice aggiunge una proprietà personalizzata denominata `DataFilePath` alla Web Part. Una proprietà personalizzata è una proprietà che possa essere impostata dall'utente in SharePoint. Questa proprietà ottiene e imposta il percorso di un file di dati XML che viene utilizzato per popolare la griglia dei dati.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Sostituire il metodo `CreateChildControls` con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

    - Aggiunge la griglia dati e l'etichetta che è stato dichiarato nel passaggio precedente.

    - Associa la griglia dei dati in un file XML che contiene i dati dei dipendenti.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Aggiungere il metodo seguente alla classe `WebPart1`. Mediante il codice vengono effettuate le seguenti attività:

    - Crea un verbo visualizzato nel menu dei verbi Web Part della Web part viene eseguito il rendering.

    - Gestione dell'evento generato quando l'utente sceglie il verbo nel relativo menu. Questo codice consente di filtrare l'elenco dei dipendenti che viene visualizzato nella griglia dei dati.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="testing-the-web-part"></a>Test della Web Part

Quando si esegue il progetto, viene aperto il sito di SharePoint. La Web Part viene automaticamente aggiunto alla raccolta Web Part in SharePoint. È possibile aggiungere la Web Part a una pagina Web Part.

1. Incollare il seguente codice XML in un file di blocco note. Questo file XML contiene i dati di esempio che verranno visualizzato nella Web Part.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. Nel blocco note, sulla barra dei menu, scegliere **File**, **Salva con nome**.

3. Nel **Salva con nome** della finestra di dialogo di **Salva come** scegliere **tutti i file**.

4. Nel **nome File** immettere **data.xml**.

5. Scegliere una cartella qualsiasi tramite il **Sfoglia cartelle** e quindi scegliere il **salvare** pulsante.

6. In Visual Studio, scegliere il **F5** chiave.

     Apre il sito di SharePoint.

7. Nel **Azioni sito** menu, scegliere **altre opzioni**.

8. Nel **crea** pagina, scegliere il **pagina Web Part** digitare, quindi scegliere il **crea** pulsante.

9. Nel **nuova pagina Web Part** pagina, denominare la pagina **SampleWebPartPage.aspx**, quindi scegliere il **crea** pulsante.

     Verrà visualizzata la pagina Web Part.

10. Selezionare qualsiasi area della pagina Web Part.

11. Nella parte superiore della pagina, scegliere il **inserire** scheda e quindi scegliere il **Web Part** pulsante.

12. Nel **categorie** riquadro, scegliere il **personalizzato** cartella, scegliere il **WebPart1** Web Part e quindi scegliere il **Aggiungi** pulsante.

     La Web Part verrà visualizzata la pagina.

## <a name="testing-the-custom-property"></a>Test della proprietà personalizzata

Per popolare la griglia dati che viene visualizzato nella Web Part, specificare il percorso del file XML che contiene dati relativi a ogni dipendente.

1. Scegliere la freccia visualizzata a destra della Web Part, quindi **modifica Web Part** dal menu visualizzato.

     Sul lato destro della pagina viene visualizzato un riquadro che contiene le proprietà per la Web Part.

2. Nel riquadro, espandere il **varie** nodo, immettere il percorso del file XML creato in precedenza, scegliere il **applica** e quindi scegliere il **OK** pulsante.

     Verificare che nella Web Part verrà visualizzato un elenco di dipendenti.

## <a name="testing-the-web-part-verb"></a>Test verbo della Web Part

Visualizzare e nascondere i dipendenti che non sono Manager, fare clic su un elemento visualizzato nel menu dei verbi Web Part.

1. Scegliere la freccia visualizzata a destra della Web Part, quindi **Mostra solo i Manager** dal menu visualizzato.

     Solo i dipendenti che sono Manager vengono visualizzati nella Web Part.

2. Scegliere nuovamente la freccia, quindi **Mostra tutti i dipendenti** dal menu visualizzato.

     Tutti i dipendenti vengono visualizzati nella Web Part.

## <a name="see-also"></a>Vedere anche

[Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Procedura: Creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Procedura: Creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)