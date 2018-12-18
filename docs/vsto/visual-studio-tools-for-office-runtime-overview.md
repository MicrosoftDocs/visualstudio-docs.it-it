---
title: Visual Studio Tools per Office Runtime Overview | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f357e593c7fe1e3dc5e4803b93ac515911ed9f75
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Panoramica di Visual Studio Tools per Office Runtime
  Per eseguire soluzioni create usando gli strumenti di sviluppo di Microsoft Office in Visual Studio, Visual Studio 2010 Tools per Office Runtime deve essere installato nei computer degli utenti finali. Per altre informazioni, vedere [How to: Install the Visual Studio Tools for Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools per Office Runtime è costituito da due componenti principali:  
  
-   Le estensioni di Office per .NET Framework. Questi componenti sono assembly gestiti che forniscono il livello di comunicazione tra la soluzione e l'applicazione di Microsoft Office. Per altre informazioni, vedere [Estensioni di Office per .NET Framework](#officeextensions).  
  
-   Il caricatore di soluzioni Office. Questo componente è un set di DLL non gestite che le applicazioni di Office usano per caricare il runtime e le soluzioni. Per altre informazioni, vedere [Informazioni sul caricatore di soluzioni Office](#UnmanagedLoader).  
  
 È possibile installare il runtime in numerose modalità diverse. A seconda della configurazione del computer, al momento dell'installazione del runtime vengono installati componenti di runtime diversi. Per altre informazioni, vedere [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a> Estensioni di Office per .NET Framework  
 Visual Studio 2010 Tools per Office Runtime include estensioni Office per .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive. Nelle soluzioni destinate a ciascuna versione di .NET Framework vengono usate le estensioni appropriate per la versione interessata.  
  
 Queste estensioni sono costituite da assembly usati dalle soluzioni per automatizzare ed estendere le applicazioni di Office. Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly usati per il tipo di progetto e .NET Framework di destinazione del progetto. Per altre informazioni sugli assembly nelle estensioni di Office, vedere [Assemblies in the Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### <a name="design-differences-in-the-office-extensions"></a>Differenze di progettazione nelle estensioni di Office  
 La maggior parte dei tipi usati nelle estensioni di Office per .NET Framework 3.5 sono classi. Si tratta delle stesse classi incluse nelle versioni precedenti di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. La maggior parte dei tipi usati nelle estensioni Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive è costituita invece da interfacce. Ad esempio, quando si usa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, i tipi <xref:Microsoft.Office.Tools.Excel.Worksheet> e <xref:Microsoft.Office.Tools.Word.Document> sono interfacce anziché classi.  
  
 Nella maggior parte dei casi, il codice che si scrive nelle soluzioni Office è lo stesso sia che la soluzione venga destinata a .NET Framework 3.5 o a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Tuttavia, alcune funzionalità richiedono codice diverso quando si ha come destinazione versioni diverse di .NET Framework. Per ulteriori informazioni, vedere [migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfacce nelle estensioni Office per .NET Framework 4 o versioni successive  
 La maggior parte delle interfacce nelle estensioni Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive non è studiata per essere implementata dal codice utente. Le uniche interfacce che è possibile implementare direttamente hanno nomi che iniziano con la lettera **I**, ad esempio <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 Tutte le interfacce che non iniziano con la lettera **I** sono implementate internamente da Visual Studio 2010 Tools per Office Runtime; queste interfacce potrebbero cambiare nelle versioni future. Per creare oggetti che implementano tali interfacce, utilizzare i metodi forniti dall'oggetto Globals. factory del progetto. Ad esempio, per ottenere un oggetto che implementa il <xref:Microsoft.Office.Tools.Excel.SmartTag> interfaccia, utilizzare il metodo Globals.Factory.CreateSmartTag. Per ulteriori informazioni su Globals. Factory, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="enabling-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Abilitazione dell'equivalenza dei tipi e dei tipi incorporati in progetti destinati a .NET Framework 4 o versione successiva  
 Poiché il modello a oggetti delle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva è basato su interfacce, è possibile usare la funzionalità di equivalenza dei tipi sia in Visual C# che in Visual Basic in Visual Studio per incorporare nella soluzione informazioni sul tipo da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Questa funzionalità consente alle soluzioni Office e a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] di eseguire il controllo della versione in modo indipendente. Se ad esempio la soluzione usa l'interfaccia <xref:Microsoft.Office.Tools.Word.Document> come tipo incorporato e la versione successiva del runtime aggiunge membri all'interfaccia <xref:Microsoft.Office.Tools.Word.Document> , la soluzione funzionerà comunque con la versione successiva del runtime. Se la soluzione non usa l'interfaccia <xref:Microsoft.Office.Tools.Word.Document> come tipo incorporato, non funzionerà più con la versione successiva del runtime.  
  
 Per impostazione predefinita, la funzionalità di equivalenza dei tipi non è abilitata quando si crea un progetto di Office destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Se si desidera abilitare tale funzionalità, impostare la proprietà **Incorpora tipi di interoperabilità** di uno qualsiasi dei seguenti riferimenti all'assembly nel progetto su **True**:  
  
-   Microsoft.Office.Tools.dll  
  
-   Microsoft.Office.Tools.Common.dll  
  
-   Microsoft.Office.Tools.Excel.dll  
  
-   Microsoft.Office.Tools.Outlook.dll  
  
-   Microsoft.Office.Tools.Word.dll  
  
 Dopo avere effettuato tale modifica, le informazioni sul tipo per tutti i tipi di runtime usati dal progetto vengono incorporate nell'assembly della soluzione quando il progetto viene compilato. In fase di esecuzione, la soluzione usa tali informazioni sul tipo incorporato, anziché le informazioni sui tipi negli assembly a cui si fa riferimento.  
  
##  <a name="UnmanagedLoader"></a> Informazioni sul caricatore di soluzioni Office  
 Il runtime di Visual Studio Tools per Office include molte DLL non gestite che nelle applicazioni di Office servono a caricare il runtime e le soluzioni Office. Anche se non si lavora mai direttamente con queste DLL, conoscerne lo scopo può permettere di comprendere meglio l'architettura delle soluzioni Office.  
  
 Per informazioni sull'uso di questi componenti durante il processo di caricamento, vedere [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md) e [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="vstoeedll"></a>vstoee.dll  
 Quando un utente apre una personalizzazione a livello di documento o avvia un componente aggiuntivo VSTO, l'applicazione di Office effettua la chiamata a VSTOEE.dll per eseguire le attività richieste per caricare [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 VSTOEE.dll verifica che venga caricata la versione corretta di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per la soluzione e la versione installata di Office. Anche se è possibile installare più versioni di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nello stesso computer, viene installata solo un'istanza di VSTOEE.dll alla volta, ossia quella inclusa nella versione più recente del runtime installato nel computer. Per ulteriori informazioni sulle diverse versioni del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che può essere utilizzato per altre soluzioni, vedere [soluzioni in esecuzione in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 Dopo il caricamento da parte di VSTOEE.dll della versione appropriata di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], VSTOLoader.dll esegue la maggior parte delle operazioni necessarie per caricare l'assembly della soluzione. VSTOLoader.dll consente di effettuare quanto riportato di seguito:  
  
-   Creare un dominio dell'applicazione per ogni assembly della soluzione.  
  
-   Eseguire un set di controlli di sicurezza per verificare che l'assembly della soluzione disponga delle autorizzazioni per l'esecuzione.  
  
-   Caricare la versione delle estensioni di Office per .NET Framework richiesta dalla soluzione.  
  
 VSTOLoader.dll consente anche di eseguire alcune operazioni specifiche dei componenti aggiuntivi VSTO:  
  
-   Implementa l'interfaccia <xref:Extensibility.IDTExtensibility2> . <xref:Extensibility.IDTExtensibility2> è un'interfaccia COM che deve essere implementata da tutti i componenti aggiuntivi VSTO per le applicazioni di Microsoft Office. Questa interfaccia definisce i metodi chiamati dall'applicazione per comunicare con il componente aggiuntivo VSTO.  
  
-   Implementa l'interfaccia IManagedAddin. Questa interfaccia viene usata dalle applicazioni di Office per consentire il caricamento di componenti aggiuntivi VSTO. Per altre informazioni, vedere [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
## <a name="understanding-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Informazioni sulle versioni a 32 bit e a 64 bit del runtime  
 Esistono versioni distinte a 64 bit e a 32 bit di Visual Studio 2010 Tools per Office Runtime. Tali versioni del runtime vengono usate per eseguire soluzioni in edizioni di Office a 64 bit e a 32 bit. Nella tabella seguente viene illustrata la versione del runtime richiesta per ogni combinazione di Windows e Office.  
  
|Edizione di Windows|Edizione di Microsoft Office|Versione richiesta del runtime di Visual Studio Tools per Office|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32 bit|32 bit|32 bit|  
|64 bit|32 bit|64 bit|  
|64 bit|64 bit|64 bit|  
  
 Quando si installa Office, la versione richiesta di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene installata insieme a Office. Ad esempio, quando si installa l'edizione a 64 bit di Office in una versione a 64 bit di Windows, viene installata anche la versione a 64 bit di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Per altre informazioni sull'installazione di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] con Office, vedere [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 La versione a 64 bit di Office può eseguire anche soluzioni Office create mediante modelli di progetto per Microsoft Office System 2007 in Visual Studio 2008. Non è tuttavia in grado di eseguire soluzioni Office create mediante modelli di progetto per Microsoft Office 2003 in Visual Studio 2008 né soluzioni Office create usando Visual Studio 2005. Per ulteriori informazioni, vedere [soluzioni in esecuzione in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## <a name="repairing-the-visual-studio-2010-tools-for-office-runtime"></a>Ripristino di Visual Studio 2010 Tools per Office Runtime  
 Se è necessario ripristinare il runtime, aprire **Programmi e funzionalità** o **Installazione applicazioni** nel Pannello di controllo, selezionare **Microsoft Visual Studio 2010 Tools per Office Runtime** nell'elenco di programmi, quindi fare clic su **Disinstalla**. Il programma di installazione che viene eseguito consente di ripristinare il runtime. Se si fa clic su **Cambia**, non viene fornita un'opzione per ripristinare il runtime.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Assembly in Visual Studio Tools per Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Aggiornamento e migrazione delle soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md)  
  
  