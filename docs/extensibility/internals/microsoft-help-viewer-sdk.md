---
title: Microsoft Help Viewer SDK | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c15956bc861f9eb20267dc97446cf5ea49cae31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK
Questo articolo sono contenute le attività seguenti per integratori di Visualizzatore della Guida di Visual Studio:  
  
-   Creazione di un argomento (il tasto F1)  
  
-   Creazione di un pacchetto di branding contenuto visualizzatore della Guida  
  
-   Distribuzione di una serie di articoli  
  
-   Aggiunta della Guida per la shell di Visual Studio (integrato o isolato)  
  
-   Risorse aggiuntive  
  
### <a name="creating-a-topic-f1-support"></a>Creazione di un argomento (il tasto F1)  
In questa sezione viene fornita una panoramica dei componenti di un argomento presentato, requisiti di argomento, una breve descrizione di come creare un argomento (inclusi i requisiti di supporto F1) e, infine, un argomento di esempio con il risultato del rendering.  
  
**Panoramica di argomento visualizzatore della Guida**  
  
Quando un argomento è stato chiamato per il rendering, il Visualizzatore della Guida ottiene gli elementi di pacchetto personalizzazione che sono associati all'argomento al momento dell'installazione o l'ultimo aggiornamento, con l'argomento XHTML e unisce i due per garantire la visualizzazione contenuto presentata (dati di branding + dati dell'argomento).  Il pacchetto di personalizzazione contiene logo, il supporto per i comportamenti del contenuto e personalizzazione di testo (copyright, ecc.).  Per ulteriori informazioni sugli elementi del pacchetto di personalizzazione, vedere "Creazione pacchetto di Branding" di seguito.  Nel caso in cui non è presente alcun pacchetto di personalizzazione associato all'argomento, il Visualizzatore della Guida verrà utilizzato il pacchetto di personalizzazione fallback situato nella radice dell'applicazione del Visualizzatore della Guida (Branding_en US.mshc).  
  
**Guida del Visualizzatore argomento requisiti**  
  
Per eseguire il rendering correttamente all'interno del Visualizzatore della Guida, il contenuto di un argomento non elaborato deve essere XHTML 1.1 base di W3C.  
  
In genere, un argomento contiene due sezioni:  
  
-   Metadati (vedere riferimento ai metadati del contenuto): padre dati sullo stesso argomento, ad esempio, l'ID univoco di argomento, valore (parola chiave), l'argomento del sommario ID, ID di nodo e così via.  
  
-   Contenuto del corpo: conforme a XHTML 1.1 base W3C che include supportato comportamenti del contenuto (area comprimibile, frammento di codice e così via. Un elenco completo è illustrato di seguito).  
  
Pacchetto di personalizzazione di Visual Studio supportati controlli:  
  
-   Collegamenti  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Membro ereditato  
  
-   LanguageSpecificText  
  
Stringhe lingua supportate (non maiuscole / minuscole):  
  
-   JavaScript  
  
-   CSharp o c#  
  
-   cplusplus o Visual c++ o c + +  
  
-   JScript  
  
-   Visual Basic o Visual Basic  
  
-   f # o fsharp o ADFS  
  
-   altro - stringa che rappresenta un nome di lingua  
  
**Creazione di un argomento di Help Viewer**  
  
Creare un nuovo documento XHTML denominato ContosoTopic4.htm e includere il tag del titolo (sotto).  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
Successivamente, aggiungere dati per definire come argomento è presentate (self marchio o No), la modalità di riferimento in questo argomento per F1, in cui è presente in questo argomento nel sommario, l'ID (per il riferimento di collegamento da altri argomenti), e così via.  Vedere la tabella "Dei metadati di contenuto" di seguito per un elenco completo di metadati supportati.  
  
-   In questo caso, si utilizzerà un pacchetto di personalizzazione, una variante del pacchetto di personalizzazione di Visualizzatore della Guida di Visual Studio.  
  
-   Aggiungere il nome di metadati F1 e il valore (contenuto "Microsoft.Help.F1" = "ContosoTopic4") che corrisponderà al valore di F1 fornito nell'elenco di proprietà IDE.  (Vedere la sezione supporto F1 per ulteriori informazioni).   Questo è il valore che corrisponde a F1 chiamare dall'interno dell'IDE da visualizzare in questo argomento quando viene scelto F1 nell'IDE.  
  
-   Aggiungere l'ID di argomento. Questa è la stringa che viene utilizzata da altri argomenti per il collegamento a questo argomento.  È l'ID di Visualizzatore della Guida per questo argomento.  
  
-   Per il sommario, aggiungere il nodo padre di questo argomento per definire in cui viene visualizzato il nodo del sommario di argomento.  
  
-   Per il sommario, aggiungere l'ordine dei nodi di questo argomento. Quando il nodo padre è n. numero di nodi figlio, definire il percorso di questo argomento nell'ordine dei nodi figlio. Ad esempio, in questo argomento è la numero 4 di 4 argomenti figlio.)  
  
Sezione di metadati di esempio:  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
<meta name="SelfBranded" content="false" />     
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
**Corpo dell'argomento**  
  
Il corpo (senza includere l'intestazione e piè di pagina) dell'argomento contiene collegamenti alle pagine, una sezione nota, un'area comprimibile, un frammento di codice e una sezione di testo specifico della lingua.  Vedere la sezione personalizzazione per informazioni su tali aree dell'argomento presentato.  
  
1.  Aggiungere un tag del titolo dell'argomento:`<div class="title">Contoso Topic 4</div>`  
  
2.  Aggiungere una nota di sezione:`<div class="alert"> add your table tag and text </div>`  
  
3.  Aggiungere un'area comprimibile:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Aggiungere un frammento di codice:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Aggiungere testo specifico del linguaggio del codice: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` si noti che devLangnu = consente di immettere altri linguaggi. Ad esempio, devLangnu = "Fortran" visualizzerà Fortran quando il frammento di codice DisplayLanguage = Fortran  
  
6.  Aggiungere collegamenti alle pagine:`<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Nota: per non supportati nuovo "lingua di visualizzazione" (ad esempio, F #, Cobol, Fortran) colori del codice nel frammento di codice sarà monocromatico.  
  
**Argomento visualizzatore della Guida di esempio** il codice viene illustrato come definire i metadati, un frammento di codice, un'area comprimibile e testo specifico della lingua.  
  
```html
<?xml version="1.0" encoding="utf-8"?>  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
<meta name="SelfBranded" content="false" />     
</head>  
  
<body>  
<div class="title">Contoso Topic 4</div>  
  
  <div id="header">  
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">  
        <tr id="headerTableRow2"><td align="left">  
            <span id="nsrTitle">Contoso Topic 1</span>  
          </td>  
<td align="right">  
</td></tr>  
<tr id="headerTableRow1"><td align="left">  
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>  
          </td></tr>  
      </table>  
</div>  
  
<h2>Table of Contents</h2>  
  
<ul class="toc">  
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>  
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>  
</ul>  
  
<div class="topic">  
  
<div id="mainSection">  
<div id="mainBody">  
  
<a name="introduction"></a>  
<h2>1.0 Introduction</h2>  
<p>[This documentation is for sample purposes only.]</p>  
  
<p>Contoso Topic 1 contains examples of:  
<ul>  
<li>Collapsible Area</li>  
<li>Bookmark ("See also")</li>  
<li>Code Snippets from Branding Package</li>  
</ul>  
 </p>  
<div class="alert"><table><tr><th>  
<strong>Note </strong></th></tr>  
<tr><td>  
<p>This is an example of a <span class="label">Note </span>section.    
Call out important items for your reader in this <span class="label">Note </span>box.  
</p></td></tr>  
</table>  
</div>  
</div>  
  
<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">  
  
            <a id="sectionToggle0"><!----></a>  
  
<div>  
Example of Collapsible Area  
<br/>  
Lorem ipsum dolor sit amet...  
</div>  
</CollapsibleArea>  
  
<div id="snippetGroup" >  
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >  
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip  
Dim messageBoxVB as New System.Text.StringBuilder()  
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)  
    messageBoxVB.AppendLine()  
 ...  
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")  
End Sub  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >  
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)   
{   
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();  
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );  
messageBoxCS.AppendLine();  
...  
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );  
}  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >  
some F# code  
</CodeSnippet>  
</div>  
  
<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />  
  
<a name="seealso"></a>  
<h1 class="heading">See Also</h1>  
  
    <div id="seeAlsoSection" class="section">   
    <div class="seeAlsoStyle">  
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Il tasto F1**  
  
In Visual Studio, selezionare F1 genera i valori forniti dalla posizione del cursore all'interno dell'IDE e popola un "elenco di proprietà" con i valori forniti (in base alla posizione del cursore. Quando il cursore è posizionato funzionalità x, x di funzionalità in attivo/attivo e popola l'elenco di proprietà con valori.  Quando si seleziona F1 viene popolato l'elenco delle proprietà e il codice di Visual Studio F1 controlla se l'origine della Guida di clienti predefinita è locale o in linea (online è quella predefinita), quindi crea la stringa appropriata basata sugli utenti, l'impostazione (online è quella predefinita) - esecuzione della shell (vedere la Guida dell'amministratore per exe parametri di avvio) con i parametri per il Visualizzatore della Guida locale + parole chiave dall'elenco di proprietà se la Guida locale è il valore predefinito o l'URL MSDN con la parola chiave nell'elenco di parametri.  
  
Se le tre stringhe vengono restituite per F1, noto per come stringa con più valori, eseguire il primo termine, cercare un riscontro, e se viene trovato, abbiamo terminato; in caso contrario, spostare la stringa successiva.  Ordine è importante. Presentazione delle parole chiave multivalore deve essere più lunga stringa alla stringa più corta.  Per effettuare questa verifica nel caso delle parole chiave con più valori, esaminare la stringa URL F1 online, che include la parola chiave scelta.  
  
In Visual Studio 2012, è reso intenzionalmente una divisione più forte tra online e offline, in modo che se l'impostazione dell'utente per Online, quindi viene semplicemente passato la richiesta F1 direttamente al servizio online query MSDN anziché routing tramite l'agente di raccolta della Guida che si è verificato in Visual Studio 2010. È quindi basarsi su uno stato di "contenuto fornitore installato = true" per determinare se qualcosa di diverso in tale contesto. Se true, è quindi possibile eseguire la logica di analisi e il routing a seconda di ciò che si desidera supportare i clienti. Se false, quindi è sufficiente passare a MSDN. Se l'impostazione dell'utente è locale, tutte le chiamate semplicemente passare al motore di Guida locale.  
  
F1 diagramma di flusso:  
  
![Flusso F1](../../extensibility/internals/media/f1flow.png "F1flow")  
  
Quando l'origine del contenuto della Guida in linea predefinito del Visualizzatore della Guida è impostata su online (avvio nel browser):  
  
-   Le funzionalità di Visual Studio Partner (VSP) creare un valore per il contenitore delle proprietà F1 (prefix.keyword contenitore delle proprietà e URL online per il prefisso trovato nel Registro di sistema): F1 invia un URL VSP + parametri per il browser.  
  
-   Funzionalità di Visual Studio (editor di linguaggio, voci di menu specifiche di Visual Studio, e così via): F1 inviata al browser un URL di Visual Studio.  
  
Quando l'origine del contenuto della Guida in linea predefinito del Visualizzatore della Guida è impostata su Guida locale (avvio in Help Viewer):  
  
-   Funzionalità VSP in (parola chiave) corrispondono tra il contenitore di proprietà F1 e indice dell'archivio locale (vale a dire il prefix.keyword contenitore delle proprietà = valore trovato nell'indice archivio locale): F1 esegue il rendering di argomento nel Visualizzatore della Guida.  
  
-   Funzionalità di Visual Studio (nessuna opzione per sovrascrivere l'elenco delle proprietà generato dalla funzionalità di Visual Studio VSP): F1 esegue il rendering di un argomento di Visual Studio nel Visualizzatore della Guida.  
  
Impostare i valori del Registro di sistema seguente per abilitare F1 Fallback per il contenuto della Guida del fornitore. Fallback F1 significa che il Visualizzatore della Guida è impostato per cercare di F1 Guida in linea contenuto in linea e il contenuto del fornitore è installato localmente sul disco rigido degli utenti. Anche se l'impostazione predefinita è per la Guida in linea Guida locale per il contenuto necessario controllare il Visualizzatore della Guida.  
  
1.  Impostare il **VendorContent** valore sotto la chiave del Registro di sistema di Guida 2.3:  
  
    -   Per i sistemi operativi a 32 bit:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = DWORD: 00000001  
  
    -   Per i sistemi operativi a 64 bit:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = DWORD: 00000001  
  
2.  Registra lo spazio dei nomi partner sotto la chiave del Registro di sistema di Guida 2.3:  
  
    -   Per i sistemi operativi a 32 bit:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< spazio dei nomi\>*  
  
         "percorso"="offline"  
  
    -   Per i sistemi operativi a 64 bit:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< spazio dei nomi\>*  
  
         "percorso"="offline"  
  
**Namespace Native durante l'analisi di base**  
  
Per attivare l'analisi di base spazio dei nomi nativo, nel Registro di sistema aggiungendo un nuovo valore DWORD il nome del: BaseNativeNamespaces e impostarne il valore su 1 (sotto la chiave di catalogo che si desidera supportare).  Ad esempio, se si desidera utilizzare il catalogo di Visual Studio, è possibile aggiungere la chiave nel percorso:  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
Quando una parola chiave F1 nel formato di CHE INTESTAZIONE o un metodo viene rilevato, il carattere '/' verrà analizzato, determinando il costrutto seguente:  
  
-   INTESTAZIONE: sarà lo spazio dei nomi che può essere utilizzato per registrare nel Registro di sistema  
  
-   METODO: diventerà la parola chiave che viene passata tramite.  
  
Si consideri ad esempio una raccolta personalizzata denominata CustomLibrary e un metodo denominato MyTestMethod, quando un F1 arriva richiesta verrà formattato come `CustomLibrary/MyTestMethod`.  
  
Un utente può quindi, registrare CustomLibrary come spazio dei nomi di hive partner e specificare qualsiasi percorso di chiave desiderano e la parola chiave passata alla query sarà MyTestMethod.  
  
**Attivare la Guida nell'IDE di strumento di debug**  
  
Aggiungere la seguente chiave del Registro di sistema e il valore:  
  
Tasto Guida HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic: Output di Debug visualizzato nel valore delle vendite al dettaglio: Sì  
  
Nell'IDE, sotto la voce di menu della Guida, selezionare "Debug il contesto della Guida"  
  
**Metadati di contenuto**  
  
Nella tabella seguente, qualsiasi stringa che viene visualizzato tra parentesi quadre è un segnaposto che deve essere sostituito da un valore riconosciuto. Ad esempio, in \<name="Microsoft.Help.Locale meta" contenuto = "[codice lingua]" / >, "[codice lingua]" deve essere sostituito da un valore, ad esempio "en-us".  
  
|Proprietà (rappresentazione HTML)|Descrizione|  
|--------------------------------------|-----------------|  
|\<contenuto name="Microsoft.Help.Locale META" = "[codice della lingua]" / >|Imposta delle impostazioni locali per questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta e deve essere inserito sopra degli altri tag di Microsoft Help. Se non viene utilizzato questo tag, il testo del corpo dell'argomento è stato indicizzato con word breaker è associato con le impostazioni locali del prodotto, se è specificata; in caso contrario, en-us word breaker viene utilizzato. Questo tag è conforme a ISOC RFC 4646. Per garantire il corretto funzionamento di Microsoft Help, usare questa proprietà invece l'attributo di linguaggio generale.|  
|\<contenuto name="Microsoft.Help.TopicLocale META" = "[codice della lingua]" / >|Imposta delle impostazioni locali per questo argomento quando vengono utilizzate anche altre impostazioni locali. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Utilizzare questo tag quando il catalogo contiene contenuto in più lingue. Più argomenti in un catalogo possono avere lo stesso ID, ma ognuno deve specificare un TopicLocale univoco. L'argomento che specifica un TopicLocale che corrisponde alle impostazioni locali del catalogo è l'argomento che viene visualizzato nel sommario. Tuttavia, tutte le versioni localizzate dell'argomento vengono visualizzate nei risultati della ricerca.|  
|\<titolo > [Title] \< /title >|Specifica il titolo di questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Se il corpo dell'argomento non contiene un titolo \<div > sezione, il titolo viene visualizzata nell'argomento e il sommario.|  
|\<nome di metadati = "Microsoft.Help.Keywords" contenuto = "[aKeywordPhrase]" / >|Specifica il testo di un collegamento che viene visualizzato nel riquadro di indice del Visualizzatore della Guida. Quando si fa clic sul collegamento, viene visualizzato l'argomento. È possibile specificare più parole chiave di indice per un argomento, o se non si desidera che i collegamenti a questo argomento per cui vengono visualizzati in corrispondenza dell'indice, è possibile omettere questo tag. Parole chiave "K" da versioni precedenti della Guida in linea possono essere convertite in questa proprietà.|  
|\<contenuto name="Microsoft.Help.Id META" = "[TopicID]" / >|Imposta l'identificatore di questo argomento. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. L'ID deve essere univoco tra gli argomenti nel catalogo che hanno le stesse impostazioni internazionali. In un altro argomento, è possibile creare un collegamento a questo argomento utilizzando questo ID.|  
|\<meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Specifica la parola chiave F1 per questo argomento. È possibile specificare più parole chiave F1 per un argomento, o se non si desidera che in questo argomento deve essere visualizzato quando un utente dell'applicazione preme F1, è possibile omettere questo tag. In genere, per un argomento è specificata una sola parola chiave F1. Parole chiave "F" da versioni precedenti della Guida in linea possono essere convertite in questa proprietà.|  
|\<nome di metadati = "Description" content = "[argomento description]" / >|Fornisce un breve riepilogo del contenuto in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Questa proprietà è accessibile direttamente dalla libreria di query. non vengono memorizzate nel file di indice.|  
 contenuto name="Microsoft.Help.TocParent META" = "[parent_Id]" / >|Specifica l'argomento padre di questo argomento nel sommario. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è Microsoft.Help.Id dell'elemento padre. Un argomento può avere un'unica posizione nella tabella del contenuto. "-1" viene considerato l'ID di argomento per la radice del sommario. In [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], tale pagina è home page del Visualizzatore della Guida. Questo è lo stesso motivo che aggiungiamo specificamente TocParent =-1 per alcuni argomenti per garantire che vengono visualizzati nella parte superiore livello. Home page del Visualizzatore della Guida è una pagina di sistema e pertanto non sostituibili. Se un VSP tenta di aggiungere una pagina con un ID -1, potrebbe ottenere aggiunto al set di contenuto, ma il Visualizzatore della Guida verrà sempre utilizzare la pagina di sistema - pagina iniziale di Visualizzatore della Guida|  
|\<contenuto name="Microsoft.Help.TocOrder META" = "[numero intero positivo]" / >|Specifica in cui nella tabella del contenuto di questo argomento viene visualizzato relativo relativi argomenti. Questo tag è obbligatorio e deve essere usato una sola volta in un argomento. Il valore è un numero intero. Un argomento che specifica un valore minore di integer viene visualizzato di sopra di un argomento che specifica un valore più alto numero intero.|  
|\<contenuto name="Microsoft.Help.Product META" = "[product code]" / >|Specifica il prodotto descritti in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Queste informazioni possono inoltre essere specificate come un parametro che viene passato all'indicizzatore Guida in linea.|  
|\<contenuto name="Microsoft.Help.ProductVersion META" = "[versione]" / >|Specifica la versione del prodotto descritti in questo argomento. Se questo tag viene usato in un argomento, deve essere utilizzato una sola volta. Queste informazioni possono inoltre essere specificate come un parametro che viene passato all'indicizzatore Guida in linea.|  
|\<contenuto name="Microsoft.Help.Category META" = "[stringa]" / >|Utilizzato dai prodotti per identificare le sezioni di contenuto. È possibile identificare più sottosezioni per un argomento, o se non si desidera che i collegamenti per identificare qualsiasi sottosezioni, è possibile omettere questo tag. Questo tag viene usato per archiviare gli attributi per TargetOS e TargetFrameworkMoniker quando un argomento viene convertito da una versione precedente della Guida in linea. Il formato del contenuto è AttributeName:AttributeValue.|  
|\<contenuto name="Microsoft.Help.TopicVersion META ="[argomento numero di versione]"/ >|Specifica la versione dell'argomento quando sono presenti più versioni in un catalogo. Poiché Microsoft.Help.Id non è garantito che sia univoco, questo tag è obbligatorio quando più di una versione di un argomento esiste in un catalogo, ad esempio, quando un catalogo contiene un argomento per .NET Framework 3.5 e un argomento per .NET Framework 4 e hanno la stessa Micro software. Help.Id.|  
|\<nome di metadati = "SelfBranded" content = "[TRUE o FALSE]" / >|Specifica se questo argomento viene utilizzato il pacchetto di personalizzazione di avvio di gestione librerie della Guida o un pacchetto di personalizzazione è specifico per l'argomento. Questo tag deve essere TRUE o FALSE. Se è TRUE, il pacchetto di personalizzazione per l'argomento associato sostituisce il pacchetto di personalizzazione che viene impostato all'avvio di gestione librerie della Guida in modo che l'argomento viene eseguito il rendering come previsto anche se differisce dal rendering di altro contenuto. Se è FALSE, l'argomento corrente viene eseguito il rendering in base al pacchetto di personalizzazione che viene impostato all'avvio di gestione librerie della Guida. Per impostazione predefinita, Gestione librerie della Guida si presuppone self-personalizzazione su false, a meno che la variabile SelfBranded è dichiarata come TRUE. Pertanto, non è necessario dichiarare \<nome meta = "SelfBranded" content = "FALSE" / >.|  
  
### <a name="creating-a-branding-package"></a>Creazione di un pacchetto di personalizzazione  
La versione di Visual Studio include un numero di diversi prodotti di Visual Studio, nonché di Isolated Shell integrata per i partner di Visual Studio.  Ognuno di questi prodotti richiede un certo grado di contenuto della Guida basate su argomenti personalizzazione univoche per il prodotto, il supporto.  Ad esempio, gli argomenti di Visual Studio dovranno disporre una presentazione del marchio coerente, mentre SQL Studio, che esegue il wrapping della Shell di ISO, richiede il proprio univoco della Guida del contenuto per la personalizzazione di ogni argomento.  Un Partner Shell integrata potrebbe essere necessario gli argomenti della Guida all'elemento padre del contenuto della Guida di prodotto di Visual Studio mantenendo le proprie informazioni personalizzate distintive di argomento.  
  
Personalizzazione di pacchetti vengono installati per il prodotto che contiene il Visualizzatore della Guida.  Per i prodotti di Visual Studio:  
  
-   Un pacchetto di personalizzazione di fallback (Branding_\<delle impostazioni locali >. mshc) è installato nella radice di app 2.3 di Visualizzatore della Guida (esempio: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) per il language pack del Visualizzatore della Guida.  Viene utilizzato per i casi in cui non è installato prodotto del pacchetto di personalizzazione (nessun contenuto è stato installato) o in cui il pacchetto di personalizzazione installato è danneggiato.  Si noti che gli elementi di Visual Studio (logo e commenti e suggerimenti) vengono ignorati quando viene utilizzato il fallback radice app personalizzazione del pacchetto.  
  
-   Quando il contenuto di Visual Studio viene installato dal servizio di pacchetto di contenuto, viene installato anche un pacchetto di personalizzazione (per il primo scenario di installazione del contenuto di tempo).  Se è presente un aggiornamento per il pacchetto di personalizzazione, l'aggiornamento viene installato quando si verifica il successivo aggiornamento del contenuto o l'azione di installazione del pacchetto aggiuntivi.  
  
Il Visualizzatore della Guida Microsoft supporta la personalizzazione degli argomenti in base ai metadati di argomento.  
  
-   In cui i metadati di argomento definiscono self marchio = true, l'argomento è di eseguire il rendering, non eseguire alcuna operazione (concerne personalizzazione).  
  
-   In cui i metadati di argomento definiscono self marchio = false, utilizzare il pacchetto di personalizzazione associato al valore dei metadati TopicVendor.  
  
-   Contenuto in cui i metadati di argomento definiscono name="Microsoft.Help.TopicVendor" =\< nome pacchetto personalizzazione in fornitore MSHA >, utilizzare il pacchetto di personalizzazione definito nel valore del contenuto.  
  
-   Si noti che all'interno del catalogo di Visual Studio, un'applicazione di priorità di Branding pacchetti.  Branding predefinito prima Visual Studio viene applicato e quindi, se definito nei metadati dell'argomento e supportato con la personalizzazione associate del pacchetto (come definito in msha l'installazione), il fornitore definito personalizzazione viene applicato come una sostituzione.  
  
Elementi di personalizzazione rientrano in genere in tre categorie principali:  
  
-   Elementi di intestazione (esempi collegamento commenti e suggerimenti, responsabilità condizionale, logo)  
  
-   Contenuto comportamenti (ad esempio elementi di testo controllo di espansione/compressione e gli elementi di frammento di codice)  
  
-   Elementi di un piè di pagina (ad esempio Copyright)  
  
Gli elementi considerati come includono elementi personalizzati (descritti in dettaglio in questa specifica):  
  
-   Logo di catalogo/prodotto (ad esempio, Visual Studio)  
  
-   Elementi di posta elettronica e il collegamento commenti e suggerimenti  
  
-   Dichiarazione di non responsabilità  
  
-   Testo di copyright  
  
I file di supporto nel pacchetto di personalizzazione di Visualizzatore della Guida di Visual Studio includono:  
  
-   Grafica (logo, icone e così via)  
  
-   Branding.js - supporto comportamenti del contenuto di file di script  
  
-   Branding.XML - stringhe che vengono usate in modo coerente tra il contenuto del catalogo.  Nota: per gli elementi di testo di localizzazione Visual Studio in branding.xml, includono locid = "\<valore univoco >"  
  
-   Branding.CSS - definizioni di stile per la coerenza di presentazione  
  
-   Printing.CSS - definizioni di stile per la presentazione stampata coerente  
  
Come indicato in precedenza, pacchetti di Branding sono associati all'argomento:  
  
-   Quando SelfBranded = false è definita nei metadati, l'argomento eredita il catalogo di branding pacchetto  
  
-   O quando SelfBranded = false e non esiste un pacchetto di Branding univoco definito nel MSHA e disponibile quando è installato il contenuto  
  
Per l'implementazione di pacchetti di branding personalizzati vsp (contenuto VSP, SelfBranded = True), per continuare è possibile iniziare con il pacchetto di personalizzazione fallback (installato con il Visualizzatore della Guida) e modificare il nome del file come appropriato.  Il Branding_\<internazionali > file di estensione è un file zip con l'estensione del file è diventato. mshc, sufficiente modificare l'estensione da estensione in zip ed estrarre il contenuto.  Vedere di seguito per la personalizzazione di elementi del pacchetto e modificare a seconda dei casi (ad esempio, cambiare il logo per il logo VSP e il riferimento al logo nel file Branding.xml, aggiornare Branding.xml per specifiche VSP e così via).  
  
Al termine di tutte le modifiche, creare un file zip contenente gli elementi di personalizzazione desiderati e modificare l'estensione per l'estensione.  
  
Per associare il pacchetto di branding personalizzato, creare MSHA che contiene il riferimento al file di personalizzazione mshc insieme il contenuto mshc (contenente gli argomenti).  Vedere di seguito "MSHA" per la creazione di una base MSHA.  
  
Il file Branding.xml contiene un elenco di elementi utilizzato per il rendering in modo coerente di elementi specifici in un argomento quando l'argomento contiene \<name="Microsoft.Help.SelfBranded meta" contenuto = "false" / >.  Elenco di elementi nel file Branding.xml Visual Studio è elencato di seguito.  Si noti che questo elenco deve essere utilizzato come modello per adottato ISO Shell, in cui modificare questi elementi (ad esempio logo, commenti e suggerimenti e Copyright) per soddisfare le proprie esigenze di branding di prodotto.  
  
Nota: le variabili indicate da "{n}" necessario dipendenze del codice, rimuovere o modificare questi valori causerà errori ed eventualmente l'arresto anomalo dell'applicazione. Gli identificatori di localizzazione (esempio _locID="codesnippet.n") sono inclusi nel pacchetto di personalizzazione di Visual Studio.  
  
**Branding.Xml**  
  
|||  
|-|-|  
|Funzionalità:|**CollapsibleArea**|  
|Utilizza:|Espandere il testo di un controllo contenuto viene compressa|  
|**Elemento**|**Valore**|  
|ExpandText|Expand|  
|CollapseText|Comprimi|  
|Funzionalità:|**CodeSnippet**|  
|Utilizza:|Testo del frammento di codice.  Nota: Verrà modificato il contenuto di frammento di codice con spazio "Unificatore" nello spazio.|  
|**Elemento**|**Valore**|  
|CopyToClipboard|Copia negli Appunti|  
|ViewColorizedText|Visualizzazione colorati|  
|CombinedVBTabDisplayLanguage|Visual Basic (esempio)|  
|VBDeclaration|Dichiarazione|  
|VBUsage|Utilizzo|  
|Funzionalità:|**Commenti e suggerimenti, piè di pagina e Logo**|  
|Utilizza:|Fornire un controllo di commenti e suggerimenti per cliente per fornire commenti e suggerimenti per l'argomento corrente tramite posta elettronica.  Testo di copyright per il contenuto.  Definizione del logo.|  
|**Elemento**|**Valore (queste stringhe possono essere modificate per soddisfare le necessità adopter contenuto).**|  
|CopyRight|© 2013 Microsoft Corporation. Tutti i diritti sono riservati.|  
|SendFeedback|\<href = "{0}" \\{1 \\} > Invia commenti e suggerimenti\</a > in questo argomento a Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|Funzionalità:|**Dichiarazione di non responsabilità**|  
|Utilizza:|Un set di case specifici dichiarazioni di non responsabilità per la macchina contenuti tradotti.|  
|**Elemento**|**Valore**|  
|MT_Editable|In questo articolo è stato tradotto. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto originale in lingua inglese nello stesso momento.|  
|MT_NonEditable|In questo articolo è stato tradotto. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto originale in lingua inglese nello stesso momento.|  
|MT_QualityEditable|In questo articolo è stato tradotto manualmente. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto originale in lingua inglese nello stesso momento.|  
|MT_QualityNonEditable|In questo articolo è stato tradotto manualmente. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto originale in lingua inglese nello stesso momento.|  
|MT_BetaContents|Questo articolo è stato tradotto automaticamente per una versione preliminare. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto originale in lingua inglese nello stesso momento.|  
|MT_BetaRecycledContents|In questo articolo è stato tradotto manualmente per una versione preliminare. Se si dispone di una connessione a Internet, selezionare "Visualizza questo argomento online" per visualizzare la pagina in modalità di modifica con il contenuto originale in lingua inglese nello stesso momento.|  
|Funzionalità:|**LinkTable**|  
|Utilizza:|Supporto per i collegamenti in linea|  
|**Elemento**|**Valore**|  
|LinkTableTitle|Tabella di collegamento|  
|TopicEnuLinkText|Visualizzare la versione in lingua inglese\</a > di questo argomento è disponibile nel computer in uso.|  
|TopicOnlineLinkText|Visualizza questo argomento \<href = "{0}" \\{1 \\} > online\</a >|  
|OnlineText|Online|  
|Funzionalità:|**Controllo Audio video**|  
|Utilizza:|Visualizzare elementi e il testo del contenuto del video|  
|**Elemento**|**Valore**|  
|MultiMediaNotSupported|Per supportare il contenuto di {0}, è necessario installare Internet Explorer 9 o versione successiva.|  
|VideoText|Visualizza video|  
|AudioText|flusso audio|  
|OnlineVideoLinkText|\<p > per visualizzare il video associato a questo argomento, fare clic su {0}\<href = "\ {1 \}" > {2}here\</a >.\< / p >|  
|OnlineAudioLinkText|\<p > per ascoltare l'audio associato a questo argomento, fare clic su {0}\<href = "\ {1 \}" > {2}here\</a >.\< / p >|  
|Funzionalità:|**Controllo del contenuto non installato**|  
|Utilizza:|Elementi di testo (stringhe) utilizzati per il rendering di contentnotinstalled.htm|  
|**Elemento**|**Valore**|  
|ContentNotInstalledTitle|Nessun contenuto è stato trovato nel computer in uso.|  
|ContentNotInstalledDownloadContentText|\<p > per scaricare il contenuto nel computer, \<href = "{0}" \\{1 \\} > fare clic sulla scheda Gestisci\</a >.\< / p >|  
|ContentNotInstalledText|\<p > non è installato nel computer. Consultare l'amministratore per l'installazione del contenuto della Guida locale.  \< /p >|  
|Funzionalità:|**Controllo di argomento non trovato**|  
|Utilizza:|Elementi di testo (stringhe) utilizzati per il rendering di topicnotfound.htm|  
|**Elemento**|**Valore**|  
|TopicNotFoundTitle|Impossibile trovare l'argomento richiesto nel computer in uso.|  
|TopicNotFoundViewOnlineText|\<p > l'argomento richiesto non è stato trovato nel computer in uso, ma è possibile \<href = "{0}" \\{1 \\} > visualizzare l'argomento online\</a >.\< / p >|  
|TopicNotFoundDownloadContentText|\<p > vedere il riquadro di spostamento per i collegamenti ad argomenti simili o \<href = "{0}" \\{1 \\} > fare clic sulla scheda Gestisci\</a > per scaricare il contenuto nel computer.\< / p >|  
|TopicNotFoundText|\<p > l'argomento richiesto non è stato trovato nel computer in uso.  \< /p >|  
|Funzionalità:|**Argomento danneggiato controllo**|  
|Utilizza:|Elementi di testo (stringhe) utilizzati per il rendering di topiccorrupted.htm|  
|**Elemento**|**Valore**|  
|TopicCorruptedTitle|Non è possibile visualizzare l'argomento richiesto.|  
|TopicCorruptedViewOnlineText|\<p > Help Viewer non è possibile visualizzare l'argomento richiesto. Potrebbe esserci un errore nel contenuto dell'argomento o una dipendenza di sistema sottostante.  \< /p >|  
|Funzionalità:|**Controllo Home Page**|  
|Utilizza:|Testo che supporta la visualizzazione del contenuto del nodo di livello superiore del Visualizzatore della Guida.|  
|**Elemento**|**Valore**|  
|HomePageTitle|Home page di Visualizzatore della Guida|  
|HomePageIntroduction|\<p > Introduzione a Microsoft Help Viewer, un'origine essenziale di informazioni per tutti gli utenti degli strumenti, prodotti, tecnologie e servizi Microsoft. Il Visualizzatore della Guida consente di accedere a informazioni di riferimento e sulle procedure, codice di esempio, articoli tecnici e altro ancora. Per individuare il contenuto che è necessario, esplorare il sommario, utilizzare la ricerca full-text oppure scorrere il contenuto utilizzando l'indice delle parole chiave.  \< /p >|  
|HomePageContentInstallText|\<p >\<br / > usare il \<href = "{0}" \\{1 \\} > Gestisci contenuto\</a > scheda eseguire le operazioni seguenti:\<ul >\<li > aggiungere contenuto al computer.\< / li >\<li > cercare gli aggiornamenti per il contenuto locale.\< / li >\<li > rimuovere contenuto dal computer.\< / li >\</ul > \< /p >|  
|HomePageInstalledBooks|Libri installati|  
|HomePageNoBooksInstalled|Nessun contenuto è stato trovato nel computer in uso.|  
|HomePageHelpSettings|Impostazioni per il contenuto della Guida|  
|HomePageHelpSettingsText|\<p > l'impostazione corrente è la Guida locale. Il Visualizzatore della Guida consente di visualizzare il contenuto installato nel computer in uso. \<br / > per modificare l'origine del contenuto della Guida, nella barra dei menu di Visual Studio, scegliere \<span style = "{0}" > Guida in linea, Imposta preferenza Guida\</span >.\< br / > \< /p >|  
|MegaByte|MB|  
  
**Branding.js**  
  
Il file branding.js contiene codice JavaScript usati dagli elementi di personalizzazione del Visualizzatore della Guida di Visual Studio.  Di seguito è riportato un elenco degli elementi di personalizzazione e la funzione di supporto JavaScript.  Tutte le stringhe devono essere localizzate per questo file sono definite nella sezione "Stringhe localizzabili" nella parte superiore di questo file.  Si noti che il file ICL sia stato creato per le stringhe di percorso all'interno del file branding.js.  
  
||||  
|-|-|-|  
|**Personalizzazione delle funzionalità**|**Funzione JavaScript**|**Descrizione**|  
|Var...||Definire le variabili|  
|Ottenere il linguaggio del codice utente|setUserPreferenceLang|esegue il mapping di un indice # per linguaggio del codice|  
|Impostare e ottenere i valori dei cookie|getCookie, setCookie||  
|Membro ereditato|changeMembersLabel|Espandi/Comprimi membro ereditato|  
|Quando SelfBranded = False|onLoad|Leggere la stringa di query per verificare se si tratta di una richiesta di stampa.  Impostare tutte le codesnippets di concentrarsi sulla scheda Preferiti utente.  Se è una stampa isPrinterFriendly richiesta quindi imposta su true. Verificare la modalità a contrasto elevato.|  
|Frammento di codice|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Scheda Modifica vengono||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|scrivere tutti gli oggetti di controllo comprimibile nell'elenco.|  
||CA_Click|in base allo stato dell'area comprimibile, che definisce quali immagini e testo per presentare|  
|Supporto del contrasto per Logo|isBlackBackground()|Chiamato per determinare se in background è nero.  Solo quando accurata in modalità a contrasto elevato.|  
||isHighContrast()|Utilizzare un intervallo di colorato per rilevare la modalità contrasto elevato|  
||onHighContrast(black)|Chiamato quando viene rilevato contrasto elevato|  
|Funzionalità LST|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|Funzionalità multimediali|didascalia (inizio, fine, testo, stile)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (styleName, styleValue)||  
||showCC(id)||  
||SUBTITLE(ID)||  
  
**FILE HTM**  
  
Il pacchetto di personalizzazione contiene un set di file HTM che supportano scenari per la comunicazione di informazioni sulla chiave agli utenti di contenuto della Guida, ad esempio una home page che contiene una sezione che descrive il set di contenuti vengono installati e le pagine che indica all'utente quando non sono di argomenti vedere il set di argomenti locale. Si noti che è possono modificare questi file HTM per prodotto.  I fornitori di Shell di ISO sono in grado di eseguire il pacchetto di personalizzazione predefinito e modificare il comportamento e il contenuto di queste pagine a suite alla rispettiva necessità.  Questi file, consultare i rispettivi pacchetti personalizzazione affinché i tag di personalizzazione ottenere il contenuto corrispondente dal file branding.xml.  
  
||||  
|-|-|-|  
|**File**|**Utilizzo**|**Origine del contenuto visualizzato**|  
|Homepage|Si tratta di una pagina che visualizza contenuto attualmente installato e qualsiasi altro messaggio appropriato per presentare all'utente il relativo contenuto.  Questo file contiene il contenuto di altri metadati dati attributo "Microsoft.Help.Id" = "-1" che inserisce questo contenuto all'inizio del sommario del contenuto locale.||  
||< META_HOME_PAGE_TITLE_ADD / >|Branding.XML, tag \<HomePageTitle >|  
||< HOME_PAGE_INTRODUCTION_SECTION_ADD / >|Branding.XML, tag \<HomePageIntroduction >|  
||< HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / >|Branding.XML, tag \<HomePageContentInstallText >|  
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / >|Titolo sezione tag Branding.xml\<HomePageInstalledBooks >, i dati generati dall'applicazione, \<HomePageNoBooksInstalled > Se non sono installata i alcuna documentazione.|  
||< HOME_PAGE_SETTINGS_SECTION_ADD / >|Titolo sezione tag Branding.xml \<HomePageHelpSettings >, sezione testo \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Quando un argomento esiste nel set di locale, ma per qualche motivo non può essere visualizzato (contenuto danneggiati).||  
||< META_TOPIC_CORRUPTED_TITLE_ADD / >|Branding.XML, tag \<TopicCorruptedTitle >|  
||< TOPIC_CORRUPTED_SECTION_ADD / >|Branding.XML, tag \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Quando un argomento non viene trovato nel contenuto locale impostato, né è disponibile online||  
||< META_TOPIC_NOT_FOUND_TITLE_ADD / >|Branding.XML, tag \<TopicNotFoundTitle >|  
||< META_TOPIC_NOT_FOUND_ID_ADD / >|Branding.XML, tag \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||< TOPIC_NOT_FOUND_SECTION_ADD / >|Branding.XML, tag \<TopicNotFoundText >|  
|contentnotinstalled.htm|Quando non è disponibile contenuto locale per il prodotto installato.||  
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD / >|Branding.XML, tag \<ContentNotInstalledTitle >|  
||< META_CONTENT_NOT_INSTALLED_ID_ADD / >|Branding.XML, tag \<ContentNotInstalledDownloadContentText >|  
||< CONTENT_NOT_INSTALLED_SECTION_ADD / >|Branding.XML, tag \<ContentNotInstalledText >|  
  
**File CSS**  
  
Il pacchetto Visual Studio Guida Visualizzatore personalizzazione contiene due file css per supportare la presentazione di contenuto della Guida di Visual Studio coerente:  
  
-   Branding.CSS - contiene gli elementi di css per il rendering where SelfBranded = false  
  
-   Printer.CSS - contiene gli elementi di css per il rendering where SelfBranded = false  
  
Branding.CSS file include le definizioni per la presentazione di argomento di Visual Studio (problema è che il branding.css contenuti nel Branding_\<delle impostazioni locali > potrebbe cambiare. mshc dal servizio pacchetto).  
  
**File di immagine**  
  
Il contenuto di Visual Studio consente di visualizzare un logo di Visual Studio, nonché altri elementi grafici.  Di seguito è riportata l'elenco completo dei file di immagine nel pacchetto di personalizzazione di Visualizzatore della Guida di Visual Studio.  
  
||||  
|-|-|-|  
|**File**|**Utilizzo**|**Esempi**|  
|Clear.gif|Usato per il rendering Area comprimibile||  
|footer_slice.gif|Presentazione di piè di pagina||  
|info_icon.gif|Utilizzato per la visualizzazione di informazioni|Dichiarazione di non responsabilità|  
|online_icon.gif|Questa icona viene associata a collegamenti online||  
|tabLeftBD.gif|Usato per il rendering del contenitore di frammento di codice||  
|tabRightBD.gif|Usato per il rendering del contenitore di frammento di codice||  
|vs_logo_bk.gif|Utilizzato per i riferimenti logo contrasto normale come definito nel tag Branding.xml \<LogoFileName >.  Per i prodotti di Visual Studio, nome logo è vs_logo_bk.gif.||  
|vs_logo_wh.gif|Utilizzato per i riferimenti logo elevata normale come definito nel tag Branding.xml \<LogoFileNameHC >.  Per i prodotti di Visual Studio, nome logo è vs_logo_wh.gif.||  
|ccOff.png|Immagine di sottotitoli codificati||  
|ccOn.png|Immagine di sottotitoli codificati||  
|ImageSprite.png|Usato per il rendering Area comprimibile|Espandere o comprimere l'elemento grafico|  
  
### <a name="deploying-a-set-of-topics"></a>Distribuzione di un set di argomenti  
Si tratta di un'esercitazione molto semplice e rapida per la creazione di una distribuzione di contenuto di Help Viewer imposta comprendere un file MSHA e il set di file CAB o MSHC che contiene gli argomenti. Il MSHA è un file XML che descrive un set di file CAB o file MSHC. Il Visualizzatore della Guida può leggere il MSHA per ottenere un elenco di contenuti (il file con estensione File CAB o. File MSHC) disponibili per l'installazione locale.  
  
Si tratta solo nozioni di base che descrive lo schema XML di base per MSHA di Visualizzatore della Guida.  Si noti che è un'implementazione di esempio di sotto di questa breve panoramica ed esempio HelpContentSetup. msha.  
  
Il nome del MSHA, ai fini di questa panoramica, è HelpContentSetup. msha (il nome del file può essere qualsiasi tipo, con l'estensione. MSHA). HelpContentSetup. msha (ad esempio riportato di seguito) deve contenere un elenco dei file CAB o MSHCs disponibili.  Si noti che il tipo di file deve essere coerenza all'interno di MSHA (non supporta una combinazione di tipi di file MSHA e CAB). Per ogni file CAB o MSHC, deve essere presente un \<div classe = "pacchetto" >... \</div > (vedere l'esempio riportato di seguito).  
  
Nota: nell'esempio di implementazione seguente, è stato incluso il pacchetto di personalizzazione. Questo è importante includere per ottenere le necessarie degli elementi di rendering del contenuto di Visual Studio e i comportamenti del contenuto.  
  
File helpcontentsetup. msha di esempio: (sostituire "nome 1 set di contenuto" e "2" e così via. con i nomi dei file set nome contenuto.)  
  
```html
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>.  
  
```  
  
1.  Creare una cartella locale, è simile a "C:\SampleContent"  
  
2.  In questo esempio utilizzeremo file MSHC per contenere gli argomenti.  Un MSHC è un file zip con l'estensione del file modificato da ZIP a. MSHC.  
  
3.  Creare il seguito HelpContentSetup. msha come file di testo (blocco note è stato utilizzato per creare il file) e salvarlo nella cartella indicato sopra (vedere il passaggio 1).  
  
Si noti che la classe "Branding" esista e che sia univoco. Mshc di Branding è incluso in questo nozioni di base in modo che il contenuto installato disporrà di branding e i comportamenti di contenuto che sono contenuti nel MSHCs avrà gli elementi di supporto appropriato contenuti nel pacchetto di personalizzazione. In caso contrario, si verificheranno degli errori quando il sistema cerca elementi di supporto che non fanno parte di copiati (installato) del contenuto.  
  
Per ottenere il pacchetto di personalizzazione di Visual Studio, copiare il file di Branding_en US.mshc in C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ nella cartella di lavoro.  
  
```html  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>  
<div class="package">  
<span class="packageType">branding</span>  
<span class="name">Branding_en-US</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Riepilogo**  
  
Utilizzo ed estensione i passaggi precedenti consentirà vsp distribuire i relativi set di contenuto per il Visualizzatore della Guida di Visual Studio.  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Aggiunta della Guida di Visual Studio Shell (modalità integrata e isolata)  
**Introduzione**  
  
Questa procedura dettagliata viene illustrato come incorporare il contenuto della Guida in un'applicazione di Visual Studio Shell e distribuirlo.  
  
**Requisiti**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Isolamento di Visual Studio 2013 Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**Panoramica**  
  
Il [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell è una versione di [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE in cui è possibile basare un'applicazione. Tali applicazioni contengono la Shell isolata con estensioni creati. Utilizzare i modelli di progetto Shell isolata, che sono inclusi nel [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, per creare estensioni.  
  
I passaggi di base per la creazione di un'applicazione basata su Shell isolata e la relativa Guida:  
  
1.  Ottenere il [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistributable (download di Microsoft).  
  
2.  In Visual Studio, creare un'estensione della Guida basata su Shell isolata, ad esempio, l'estensione della Guida di Contoso è descritta più avanti in questa procedura dettagliata.  
  
3.  Eseguire il wrapping dell'estensione e la Shell di ISO redistributable in una distribuzione MSI (un programma di installazione dell'applicazione). Questa procedura dettagliata non include un passaggio di installazione.  
  
Creare un archivio di contenuto Visual Studio. Per lo scenario Integrated Shell, modificare Visual Studio12 per il nome del catalogo prodotti, come segue:  
  
-   Creare cartella C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.  
  
-   Creare un file denominato CatalogType.xml e aggiungerlo alla cartella. Il file deve contenere le righe di codice seguente:  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
Definire l'archivio del contenuto nel Registro di sistema. Per la Shell integrata, modificare VisualStudio15 per il nome del catalogo prodotti:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     Chiave: Valore di stringa LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-us  
  
     Chiave: Valore di stringa CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentazione  
  
**Creare il progetto**  
  
Per creare un'estensione della Shell isolata:  
  
1.  In Visual Studio, in **File**, scegliere **nuovo progetto**in **altri tipi di progetto** scegliere **estendibilità**, quindi scegliere  **Visual Studio isolata Shell**. Denominare il progetto `ContosoHelpShell`) per creare un progetto di estendibilità in base al modello di Visual Studio Isolated Shell.  
  
2.  In Esplora soluzioni, nel progetto ContosoHelpShellUI, nella cartella file di risorse, aprire ApplicationCommands.vsct. Verificare che questa riga viene impostata come commento (ricerca di "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  Premere il tasto F5 per compilare ed eseguire **Debug**. Nell'istanza sperimentale dell'IDE Shell isolata, scegliere il **Guida** menu. Assicurarsi che il **Visualizza Guida**, **Aggiungi e Rimuovi contenuto della Guida**, e **Imposta preferenza Guida** i comandi vengono visualizzati.  
  
4.  In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella Shell Customization, aprire ContosoHelpShell.pkgdef. Per definire il catalogo della Guida di Contoso, aggiungere le righe seguenti:  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  In Esplora soluzioni, nel progetto ContosHelpShell, nella cartella Shell Customization, aprire ContosoHelpShell.Application.pkgdef. Per abilitare F1 Guida in linea, aggiungere le righe seguenti:  
  
    ```  
    // F1 Help Provider  
  
    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="13407"  
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"  
    @="Help3 Provider"  
    [$RootKey$\HelpProviders]  
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"  
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="Help3 Provider"  
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  In Esplora soluzioni, nel menu di scelta rapida della soluzione ContosoHelpShell, scegliere il **proprietà** voce di menu. In **le proprietà di configurazione**selezionare **Configuration Manager**. Nel **configurazione** colonna, modificare ogni valore di "Debug" in "Rilascio".  
  
7.  Compilare la soluzione. Verrà creato un set di file in una cartella di rilascio, che verrà utilizzata nella sezione successiva.  
  
Per testare questo come se distribuita:  
  
1.  Si distribuiscono Contoso per installare la Shell di ISO (di sopra) scaricato nel computer.  
  
2.  Creare una cartella in \\file \Programmi (x86)\\e denominarla `Contoso`.  
  
3.  Copiare il contenuto dalla cartella versione ContosoHelpShell \\(x86) \Contoso\ cartella \Programmi.  
  
4.  Avviare l'Editor del Registro di sistema scegliendo **eseguire** nel **avviare** menu e l'immissione di `Regedit`. Nell'editor del Registro di sistema, scegliere **File**e quindi **importazione**. Individuare la cartella di progetto ContosoHelpShell. Nella sottocartella ContosoHelpShell, scegliere ContosoHelpShell.reg.  
  
5.  Creare un archivio del contenuto:  
  
     Per la Shell ISO - creare un archivio contenuti a Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     Per [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrated Shell, creare una cartella C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  Creare CatalogType.xml e aggiungere al contenitore dell'archivio del contenuto (passaggio precedente):  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Aggiungere le chiavi del Registro di sistema seguenti:  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Valore stringa LocationPath:  
  
     Per ISO Shell:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell integrata:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-Stati Uniti  
  
     Chiave: Valore di stringa CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentazione. Per ISO Shell, questo è il nome del catalogo.  
  
8.  Copiare il contenuto (cabine o MSHC e MSHA) in una cartella locale.  
  
9. Shell integrata riga di comando per il test dell'archivio del contenuto. Per ISO Shell, modificare i valori di catalogo e launchingApp come appropriato per la corrispondenza del prodotto.  
  
     Metodo di /helpQuery /catalogName VisualStudio15 "C:\Programmi\Microsoft file (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" = "pagina & id = ContosoTopic0" /launchingApp Microsoft Visual Studio, 12.0  
  
10. Avviare l'applicazione Contoso (dalla radice di app di Contoso). All'interno della Shell di ISO, scegliere il **Guida** voce di menu e modificare il **Imposta preferenza Guida** a **Guida locale usare**.  
  
11. All'interno della shell, scegliere il **Guida** voce di menu, quindi **Visualizza Guida**. Deve essere avviato il Visualizzatore della Guida locale. Scegliere la scheda **Gestisci contenuto**. In **origine dell'installazione**, scegliere il **disco** pulsante di opzione. Scegliere il **...**  pulsante e passare alla cartella locale contenente il contenuto di Contoso (copiato nella cartella locale nel passaggio precedente). Scegliere il HelpContentSetup. msha. Contoso dovrebbe essere visualizzati come un libro nelle selezioni delle libro. Scegliere **Aggiungi**, quindi scegliere il **aggiornamento** pulsante (nell'angolo inferiore destro).  
  
12. All'interno dell'IDE di Contoso, premere il tasto F1 per testare la funzionalità F1.  
  
### <a name="additional-resources"></a>Risorse aggiuntive  
Per l'API di Runtime, vedere [API Guida di Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
Per ulteriori informazioni su come usare l'API della Guida, vedere [esempi di codice il Visualizzatore della Guida](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
Per fornire commenti e suggerimenti relativi questi componenti, utilizzare [Microsoft Connect](http://connect.microsoft.com/).  
  
Inviare suggerimenti sulle funzionalità di [voce utente Microsoft](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
Per ottenere informazioni aggiuntive, provare il [forum di documentazione per sviluppatori MSDN e sistema di Guida](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
Aggiornamenti sulle importanti problema, consultare il [file Leggimi di Visualizzatore della Guida](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
Per contattare direttamente il team PM di Visualizzatore della Guida, inviare messaggi di posta elettronicahlpfdbk@microsoft.com