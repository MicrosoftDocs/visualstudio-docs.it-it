---
title: Le voci del Registro di sistema per i componenti aggiuntivi VSTO | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5e4c410a6f934c7b4fe4c6239bdfe07364af3152
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="registry-entries-for-vsto-add-ins"></a>Voci del Registro di sistema per i componenti aggiuntivi VSTO
  È necessario creare un set specifico di voci del Registro di sistema quando si distribuiscono componenti aggiuntivi VSTO creati con Visual Studio. Queste voci del Registro di sistema forniscono informazioni che consentono all'applicazione di Microsoft Office di individuare e caricare il componente aggiuntivo VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Quando si compila il progetto, Visual Studio crea queste voci del Registro di sistema nel computer di sviluppo, in modo che sia possibile eseguire il componente aggiuntivo VSTO ed effettuarne il debug con facilità. Se si usa ClickOnce per distribuire il componente aggiuntivo VSTO, le voci del Registro di sistema vengono create automaticamente nel computer dell'utente finale. Se invece si usa Windows Installer, è necessario configurare il progetto InstallShield Limited Edition per creare le voci del Registro di sistema nel computer dell'utente finale.  
  
 Per altre informazioni sull'uso delle voci del Registro di sistema durante il processo di caricamento per i componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  In questo argomento la dicitura *ID componente aggiuntivo* rappresenta l'identificatore univoco del componente aggiuntivo VSTO. Per impostazione predefinita, l'ID è il nome dell'assembly del componente aggiuntivo VSTO.  
  
## <a name="registering-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrazione di componenti aggiuntivi VSTO per l'utente corrente e per Tutti gli utenti  
 Un componente aggiuntivo VSTO installato può essere registrato in due modi diversi:  
  
-   Solo per l'utente corrente (ovvero risulta disponibile solo per l'utente che è connesso al computer durante l'installazione del componente aggiuntivo VSTO). In questo caso le voci del Registro di sistema vengono create nella chiave HKEY_CURRENT_USER.  
  
-   Per tutti gli utenti (ovvero qualsiasi utente che si connette al computer può usare il componente aggiuntivo VSTO). In questo caso le voci del Registro di sistema vengono create nella chiave HKEY_LOCAL_MACHINE.  
  
 Tutti i componenti aggiuntivi VSTO creati con Visual Studio possono essere registrati per l'utente corrente. Tuttavia, i componenti aggiuntivi VSTO possono essere registrati per tutti gli utenti solo in determinati scenari. Questi scenari dipendono dalla versione di Microsoft Office installata nel computer e dal modo in cui è stato distribuito il componente aggiuntivo VSTO.  
  
### <a name="microsoft-office-version"></a>Versione di Microsoft Office  
 Le applicazioni di Office possono caricare i componenti aggiuntivi VSTO registrati in HKEY_LOCAL_MACHINE o HKEY_CURRENT_USER.  
  
 Per caricare componenti aggiuntivi VSTO registrati in HKEY_LOCAL_MACHINE, nei computer deve essere installato il pacchetto di aggiornamenti 976477. Per altre informazioni, vedere [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### <a name="deployment-type"></a>Tipo distribuzione  
 Se si usa ClickOnce per distribuire un componente aggiuntivo VSTO, quest'ultimo può essere registrato solo per l'utente corrente. ClickOnce supporta infatti la creazione di chiavi solo in HKEY_CURRENT_USER. Se si vuole registrare un componente aggiuntivo VSTO per tutti gli utenti di un computer, è necessario distribuirlo tramite Windows Installer. Per ulteriori informazioni su questi tipi di distribuzione, vedere [distribuisce una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) e [distribuisce una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="registry-entries"></a>Voci del Registro di sistema  
 Le voci del Registro di sistema necessarie per i componenti aggiuntivi VSTO si trovano nella seguente chiave del Registro di sistema per tutte le applicazioni ad eccezione di Visio, dove *Radice* corrisponde a HKEY_CURRENT_USER o HKEY_LOCAL_MACHINE.  
  
 **Tutte le applicazioni ad eccezione di Visio**  
  
|Versione di Office|Percorso di configurazione|  
|--------------------|------------------------|  
|32 bit|*Radice*\Software\Microsoft\Office\\*nome dell'applicazione*\Addins\\*ID componente aggiuntivo*|  
|64 bit|*Radice*\Software\Wow6432Node\Microsoft\Office\\*nome dell'applicazione*\Addins\\*ID componente aggiuntivo*|  
  
 **Visio**  
  
|Versione di Office|Percorso di configurazione|  
|--------------------|------------------------|  
|32 bit|*Radice*\Software\Microsoft\Visio\Addins\\*ID componente aggiuntivo*|  
|64 bit|*Radice*\Software\Wow6432Node\Visio\Addins\\*ID componente aggiuntivo*|  
  
 Nella tabella seguente sono elencate le voci presenti in questa chiave del Registro di sistema.  
  
|Voce|Tipo|Valore|  
|-----------|----------|-----------|  
|**Descrizione**|REG_SZ|Obbligatorio. Breve descrizione del componente aggiuntivo VSTO.<br /><br /> Questa descrizione viene visualizzata quando l'utente seleziona il componente aggiuntivo VSTO nel riquadro **Componenti aggiuntivi** della finestra di dialogo **Opzioni** nell'applicazione di Microsoft Office.|  
|**FriendlyName**|REG_SZ|Obbligatorio. Nome descrittivo del componente aggiuntivo VSTO visualizzato nella finestra di dialogo **Componenti aggiuntivi COM** dell'applicazione di Microsoft Office. Il valore predefinito è l'ID del componente aggiuntivo VSTO.|  
|**LoadBehavior**|REG_DWORD|Obbligatorio. Valore che specifica quando l'applicazione tenta di caricare il componente aggiuntivo VSTO e lo stato corrente del componente aggiuntivo VSTO (caricato o scaricato).<br /><br /> Per impostazione predefinita, questo valore è impostato su 3, a indicare che il componente aggiuntivo VSTO viene caricato all'avvio. Per altre informazioni, vedere [Valori di LoadBehavior](#LoadBehavior). **Nota:** se un utente disabilita il componente aggiuntivo VSTO, tale azione Modifica **LoadBehavior** valore nell'hive del Registro di sistema HKEY_CURRENT_USER. Per ogni utente il valore di **LoadBehavior** nell'hive HKEY_CURRENT_USER ha la precedenza sul valore di **LoadBehavior** predefinito specificato nell'hive HKEY_LOCAL_MACHINE.|  
|**Manifest**|REG_SZ|Obbligatorio. Percorso completo del manifesto della distribuzione del componente aggiuntivo VSTO. Può essere un percorso contenuto nel computer locale, una condivisione di rete (UNC) o un server Web (HTTP).<br /><br /> Se si usa Windows Installer per distribuire la soluzione, è necessario aggiungere il prefisso **file:///** al percorso di **manifesto** . È anche necessario accodare la stringa  **&#124;vstolocal** (ovvero, il carattere di barra verticale **&#124;** seguito da **vstolocal**) alla fine di questo percorso. Il suffisso garantisce che la soluzione venga caricata dalla cartella di installazione e non dalla cache ClickOnce. Per altre informazioni, vedere [Distribuzione di una soluzione Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Nota:** quando si compila un componente aggiuntivo VSTO nel computer di sviluppo, Visual Studio aggiunge automaticamente il  **&#124;vstolocal** stringa per questa voce del Registro di sistema.|  
  
###  <a name="OutlookEntries"></a> Voci del Registro di sistema per le aree del modulo di Outlook  
 Se si crea un'area del modulo personalizzata in un componente aggiuntivo VSTO per Outlook, vengono usate voci aggiuntive del Registro di sistema per registrare l'area con Outlook. Queste voci vengono create in una chiave del Registro di sistema diversa per ogni classe di messaggio supportata dall'area. Le voci vengono salvate nel percorso seguente, dove *Radice* corrisponde a HKEY_CURRENT_USER o HKEY_LOCAL_MACHINE.  
  
 *Radice*\Software\Microsoft\Office\Outlook\FormRegions\\*classe message*  
  
 Analogamente alle altre voci del Registro di sistema condivise da tutti i componenti aggiuntivi VSTO, Visual Studio crea le voci relative all'area del modulo nel computer di sviluppo durante la compilazione del progetto. Se si usa ClickOnce per distribuire il componente aggiuntivo VSTO, le voci del Registro di sistema vengono create automaticamente nel computer dell'utente finale. Se invece si usa Windows Installer, è necessario configurare il progetto InstallShield Limited Edition per creare le voci del Registro di sistema nel computer dell'utente finale.  
  
 Per ulteriori informazioni sulle voci del Registro di sistema di area del modulo, vedere [specificare il percorso di un'area del modulo in un modulo personalizzato](http://msdn.microsoft.com/library/office/ff868998.aspx). Per altre informazioni sulle aree del modulo di Outlook, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> Valori di LoadBehavior  
 Il **LoadBehavior** voce sotto il *radice*\Software\Microsoft\Office\\*nome applicazione*\Addins\\*aggiuntivo ID* chiave contiene una combinazione bit per bit dei valori che specificano il comportamento della fase di esecuzione del componente aggiuntivo VSTO. Il bit di ordine più basso (valori 0 e 1) indica se il componente aggiuntivo VSTO è attualmente caricato o scaricato. Gli altri bit indicano quando l'applicazione tenta di caricare il componente aggiuntivo VSTO.  
  
 In genere, la voce **LoadBehavior** deve essere impostata su 0, 3 o 16 (in numero decimale) quando il componente aggiuntivo VSTO viene installato nei computer degli utenti finali. Per impostazione predefinita, Visual Studio imposta la voce **LoadBehavior** del componente aggiuntivo VSTO su 3 quando questo viene compilato o pubblicato.  
  
 Nella tabella seguente sono elencati tutti i valori possibili della voce **LoadBehavior** . Alcune descrizioni in questa tabella si riferiscono al caricamento di un componente aggiuntivo VSTO manualmente o a livello di codice. Per caricare un componente aggiuntivo VSTO manualmente, selezionare la casella di controllo accanto al componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** nell'applicazione. Per caricare un componente aggiuntivo VSTO a livello di codice, impostare la proprietà <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> dell'oggetto <xref:Microsoft.Office.Core.COMAddIn> che rappresenta il componente aggiuntivo VSTO su **true**.  
  
|Valore decimale|Stato del componente aggiuntivo VSTO|Comportamento di caricamento del componente aggiuntivo VSTO|Descrizione|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|Scaricato|Non viene caricato automaticamente|L'applicazione non tenta mai di caricare il componente aggiuntivo VSTO automaticamente. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se il componente aggiuntivo VSTO viene caricato correttamente, il valore di **LoadBehavior** rimane impostato su 0, ma lo stato del componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** viene aggiornato per indicare che il componente aggiuntivo VSTO è caricato.|  
|1|Caricato|Non viene caricato automaticamente|L'applicazione non tenta mai di caricare il componente aggiuntivo VSTO automaticamente. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Anche se nella finestra di dialogo **Componenti aggiuntivi COM** è indicato che il componente aggiuntivo VSTO viene caricato dopo l'avvio dell'applicazione, il componente aggiuntivo VSTO non risulta effettivamente caricato finché non viene caricato manualmente o a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 0 e rimane tale dopo la chiusura dell'applicazione.|  
|2|Scaricato|Viene caricato all'avvio|L'applicazione non tenta di caricare automaticamente il componente aggiuntivo VSTO. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 3 e rimane tale dopo la chiusura dell'applicazione.|  
|3|Caricato|Viene caricato all'avvio|L'applicazione tenta di caricare il componente aggiuntivo VSTO all'avvio. Questo è il valore predefinito quando si compila o si pubblica un componente aggiuntivo VSTO in Visual Studio.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** rimane impostato su 3. Se si verifica un errore durante il caricamento del componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 2 e rimane tale dopo la chiusura dell'applicazione.|  
|8|Scaricato|Viene caricato su richiesta|L'applicazione non tenta di caricare automaticamente il componente aggiuntivo VSTO. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 9.|  
|9|Caricato|Viene caricato su richiesta|Il componente aggiuntivo VSTO verrà caricato solo quando richiesto dall'applicazione, ad esempio quando un utente fa clic su un elemento dell'interfaccia utente che usa la funzionalità del componente aggiuntivo VSTO, come un pulsante personalizzato della barra multifunzione.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** rimane impostato su 9, ma lo stato del componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** viene aggiornato per indicare che il componente aggiuntivo VSTO è attualmente caricato. Se si verifica un errore durante il caricamento del componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 8.|  
|16|Caricato|Viene caricato la prima volta e successivamente su richiesta|Impostare questo valore se si vuole che il componente aggiuntivo VSTO venga caricato su richiesta. L'applicazione carica il componente aggiuntivo VSTO quando viene eseguita dall'utente per la prima volta. Alla successiva esecuzione dell'applicazione, verranno caricati tutti gli elementi dell'interfaccia utente definiti dal componente aggiuntivo VSTO, ma quest'ultimo non verrà caricato finché l'utente non fa clic su un elemento dell'interfaccia utente associato al componente aggiuntivo VSTO.<br /><br /> Quando l'applicazione carica correttamente il componente aggiuntivo VSTO per la prima volta, il valore di **LoadBehavior** rimane impostato su 16 mentre il componente aggiuntivo VSTO è caricato. Dopo la chiusura dell'applicazione, il valore di **LoadBehavior** viene impostato su 9.|  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  