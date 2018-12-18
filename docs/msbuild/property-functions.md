---
title: "Funzioni di proprietà | Microsoft Docs"
ms.custom: 
ms.date: 02/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c3bd5d35e3d996a1507a5ce14d40fbb59c24cbdb
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2018
---
# <a name="property-functions"></a>Funzioni delle proprietà
In.NET Framework versioni 4 e 4.5, le funzioni di proprietà possono essere usate per valutare gli script MSBuild. Le funzioni di proprietà possono essere usate ovunque siano presenti le proprietà. A differenza delle attività, le funzioni di proprietà possono essere usate all'esterno delle destinazioni e vengono valutate prima dell'esecuzione delle destinazioni.  

 Senza usare le attività MSBuild, è possibile leggere l'ora di sistema, confrontare stringhe, trovare la corrispondenza per espressioni regolari ed eseguire altre azioni nello script di compilazione. MSBuild tenterà di convertire le stringhe in numeri e i numeri in stringhe nonché di eseguire altre conversioni secondo le esigenze.  

## <a name="property-function-syntax"></a>Sintassi delle funzioni di proprietà  
 Di seguito sono elencati tre tipi di funzioni di proprietà. Ogni funzione presenta una sintassi diversa:  

-   Funzioni di proprietà stringa (istanza)  

-   Funzioni di proprietà statiche  

-   Funzioni di proprietà MSBuild  

### <a name="string-property-functions"></a>Funzioni di proprietà stringa  
 Tutti i valori delle proprietà di compilazione sono soltanto valori stringa. Per agire su qualsiasi valore di proprietà è possibile usare i metodi stringa (istanza). Ad esempio, è possibile estrarre il nome di unità, ovvero i primi tre caratteri, da una proprietà di compilazione che rappresenta un percorso completo con questo codice:  

 `$(ProjectOutputFolder.Substring(0,3))`  

### <a name="static-property-functions"></a>Funzioni di proprietà statiche  
 Nello script di compilazione è possibile accedere alle proprietà e ai metodi statici di molte classi di sistema. Per ottenere il valore di una proprietà statica, usare la sintassi seguente, dove *Class* è il nome della classe di sistema e *Property* è il nome della proprietà.  

 `$([Class]::Property)`  

 Ad esempio, è possibile usare il codice seguente per impostare una proprietà di compilazione sulla data e sull'ora correnti.  

 `<Today>$([System.DateTime]::Now)</Today>`  

 Per chiamare un metodo statico, usare la sintassi seguente, dove *Class* è il nome della classe di sistema, *Method* è il nome del metodo e *(Parameters)* è l'elenco di parametri del metodo:  

 `$([Class]::Method(Parameters))`  

 Ad esempio per impostare una proprietà di compilazione su un nuovo GUID, è possibile usare lo script seguente:  

 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  

 Nelle funzioni di proprietà statiche è possibile usare qualsiasi proprietà o metodo statico delle classi di sistema seguenti:  

-   System.Byte  

-   System.Char  

-   System.Convert  

-   System.DateTime  

-   System.Decimal  

-   System.Double  

-   System.Enum  

-   System.Guid  

-   System.Int16  

-   System.Int32  

-   System.Int64  

-   System.IO.Path  

-   System.Math  

-   System.Runtime.InteropServices.OSPlatform

-   System.Runtime.InteropServices.RuntimeInformation

-   System.UInt16  

-   System.UInt32  

-   System.UInt64  

-   System.SByte  

-   System.Single  

-   System.String  

-   System.StringComparer  

-   System.TimeSpan  

-   System.Text.RegularExpressions.Regex  

-   Microsoft.Build.Utilities.ToolLocationHelper  

 Inoltre, è possibile usare le proprietà e i metodi statici seguenti:  

-   System.Environment::CommandLine  

-   System.Environment::ExpandEnvironmentVariables  

-   System.Environment::GetEnvironmentVariable  

-   System.Environment::GetEnvironmentVariables  

-   System.Environment::GetFolderPath  

-   System.Environment::GetLogicalDrives  

-   System.IO.Directory::GetDirectories  

-   System.IO.Directory::GetFiles  

-   System.IO.Directory::GetLastAccessTime  

-   System.IO.Directory::GetLastWriteTime  

-   System.IO.Directory::GetParent  

-   System.IO.File::Exists  

-   System.IO.File::GetCreationTime  

-   System.IO.File::GetAttributes  

-   System.IO.File::GetLastAccessTime  

-   System.IO.File::GetLastWriteTime  

-   System.IO.File::ReadAllText  

### <a name="calling-instance-methods-on-static-properties"></a>Chiamata di metodi di istanza su proprietà statiche  
 Se si accede a una proprietà statica che restituisce un'istanza di un oggetto, è possibile richiamare i metodi di istanza di tale oggetto. Per richiamare un metodo di istanza usare la sintassi seguente, dove *Class* è il nome della classe di sistema, *Property* è il nome della proprietà, *Method* è il nome del metodo e *(Parameters)* è l'elenco di parametri del metodo:  

 `$([Class]::Property.Method(Parameters))`  

 Il nome della classe deve essere completo con lo spazio dei nomi.  

 Ad esempio, è possibile usare il codice seguente per impostare una proprietà di compilazione sulla data corrente.  

 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  

### <a name="msbuild-property-functions"></a>Funzioni di proprietà MSBuild  
 È possibile accedere a diversi metodi statici nella compilazione per supportare funzionalità aritmetiche, operazioni logiche bit per bit nonché la gestione dei caratteri di escape. Per accedere a questi metodi usare la sintassi seguente, dove *Method* è il nome del metodo e *Parameters* è l'elenco di parametri del metodo.  

 `$([MSBuild]::Method(Parameters))`  

 Ad esempio, per sommare due proprietà che presentano valori numerici, usare il codice seguente.  

 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  

 Di seguito è riportato un elenco di funzioni di proprietà MSBuild:  

|Firma funzione|Descrizione|  
|------------------------|-----------------|  
|double Add(double a, double b)|Esegue l'addizione di due valori Double.|  
|long Add(long a, long b)|Esegue l'addizione di due valori Long.|  
|double Subtract(double a, double b)|Esegue la sottrazione tra due valori Double.|  
|long Subtract(long a, long b)|Esegue la sottrazione tra due valori Long.|  
|double Multiply(double a, double b)|Esegue la moltiplicazione tra due valori Double.|  
|long Multiply(long a, long b)|Esegue la moltiplicazione tra due valori Long.|  
|double Divide(double a, double b)|Esegue la divisione tra due valori Double.|  
|long Divide(long a, long b)|Esegue la divisione tra due valori Long.|  
|double Modulo(double a, double b)|Esegue l'operazione modulo tra due valori Double.|  
|long Modulo(long a, long b)|Esegue l'operazione modulo tra due valori Long.|  
|string Escape(string unescaped)|Aggiunge i caratteri di escape alla stringa in base alle regole di escape di MSBuild.|  
|string Unescape(string escaped)|Rimuove i caratteri di escape dalla stringa in base alle regole di escape di MSBuild.|  
|int BitwiseOr(int first, int second)|Esegue un'operazione `OR` bit per bit tra il primo e il secondo valore (primo &#124; secondo).|  
|int BitwiseAnd(int first, int second)|Esegue un'operazione `AND` bit per bit tra il primo e il secondo valore (primo & secondo).|  
|int BitwiseXor(int first, int second)|Esegue un'operazione `XOR` bit per bit tra il primo e il secondo valore (primo ^ secondo).|  
|int BitwiseNot(int first)|Esegue un'operazione `NOT` bit per bit (~primo).|  
|bool IsOsPlatform(string platformString)|Specifica se la piattaforma del sistema operativo corrente è `platformString`. `platformString` deve essere membro di <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike|True se il sistema operativo corrente è un sistema Unix.|
|string NormalizePath(params string[] path)|Ottiene il percorso completo in forma canonica corrispondente al percorso specificato e garantisce che contenga i separatori di directory corretti per il sistema operativo corrente.|
|string NormalizeDirectory(params string[] path)|Ottiene il percorso completo in forma canonica della directory specificata e garantisce che contenga i separatori di directory corretti per il sistema operativo corrente e una barra rovesciata finale.|
|string EnsureTrailingSlash(string path)|Se il percorso specificato non dispone di una barra rovesciata, la aggiunge al percorso. Se il percorso è una stringa vuota non lo modifica.|
|string GetPathOfFileAbove(string file, string startingDirectory)|Cerca un file in base alla posizione di compilazione corrente del file o a `startingDirectory` se specificato.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Trova un file nella directory specificata o in un percorso nella struttura di directory a monte di tale directory.|
|string MakeRelative(string basePath, string path)|Rende `path` relativo a `basePath`. `basePath` deve essere una directory assoluta. Se `path` non può essere reso relativo, viene restituito letteralmente. Simile a `Uri.MakeRelativeUri`.|
|string ValueOrDefault(string conditionValue, string defaultValue)|Restituisce la stringa nel parametro 'defaultValue' solo se il parametro 'conditionValue' è vuoto. In caso contrario, restituisce il valore conditionValue.|

##  <a name="nested-property-functions"></a>Funzioni di proprietà annidate  
 È possibile combinare le funzioni di proprietà per formare funzioni più complesse, come mostrato nell'esempio seguente.  

 `$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))`  

 Questo esempio restituisce il valore di bit <xref:System.IO.FileAttributes>`Archive` (32 o 0) del file fornito dal percorso `tempFile`. Notare che i valori di dati enumerati non possono essere specificati per nome all'interno delle funzioni di proprietà. È necessario usare invece il valore numerico (32).  

 Nelle funzioni di proprietà annidate è possibile specificare anche i metadati. Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).  

##  <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist  
 La funzione di proprietà `DoesTaskHostExist` in MSBuild restituisce un valore che indica se un host attività è attualmente installato per i valori di architettura e runtime specificati.  

 Questa funzione di proprietà presenta la seguente sintassi:  

```  
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```  

##  <a name="msbuild-ensuretrailingslash"></a>EnsureTrailingSlash di MSBuild  
 La funzione di proprietà `EnsureTrailingSlash` in MSBuild aggiunge una barra finale se non ne esiste già una.  

 Questa funzione di proprietà presenta la seguente sintassi:  

```  
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```  

##  <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove  
 La funzione di proprietà MSBuild `GetDirectoryNameOfFileAbove` cerca un file nelle directory al di sopra della directory corrente nel percorso.  

 Questa funzione di proprietà presenta la seguente sintassi:  

```  
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```  

 Il codice seguente è un esempio di questa sintassi.  

```xml  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  

##  <a name="msbuild-getpathoffileabove"></a>GetPathOfFileAbove di MSBuild  
 La funzione di proprietà `GetPathOfFileAbove` in MSBuild restituisce il percorso del file immediatamente precedente a questo. Dal punto di vista funzionale è equivalente alla chiamata

 ```<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />```

 Questa funzione di proprietà presenta la seguente sintassi:  

```  
$([MSBuild]::GetPathOfFileAbove(dir.props))  
```  

##  <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue  
 La funzione di proprietà MSBuild `GetRegistryValue` restituisce il valore di una chiave del Registro di sistema. Questa funzione accetta due argomenti, il nome della chiave e il nome del valore e restituisce il valore dal Registro di sistema. Se non si specifica un nome del valore, viene restituito il valore predefinito.  

 Gli esempi seguenti mostrano come viene usata questa funzione:  

```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  

```  

##  <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView  
 La funzione di proprietà MSBuild `GetRegistryValueFromView` ottiene i dati del Registro di sistema in base alla chiave e al valore del Registro di sistema forniti, nonché a una o più visualizzazioni ordinate del Registro di sistema. La chiave e il valore vengono cercati in ogni visualizzazione del Registro di sistema in ordine, finché non vengono trovati.  

 Di seguito è indicata la sintassi per la funzione della proprietà:  

 [MSBuild\]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)  

 Il sistema operativo Windows a 64 bit gestisce una chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node che presenta una visualizzazione del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE per le applicazioni a 32 bit.  

 Per impostazione predefinita, un'applicazione a 32 bit in esecuzione su WOW64 accede alla visualizzazione del Registro di sistema a 32 bit e un'applicazione a 64 bit accede alla visualizzazione del Registro di sistema a 64 bit.  

 Sono disponibili le visualizzazioni del Registro di sistema seguenti:  

|Visualizzazione del Registro di sistema|Definizione|  
|-------------------|----------------|  
|RegistryView.Registry32|Visualizzazione del Registro di sistema dell'applicazione a 32 bit.|  
|RegistryView.Registry64|Visualizzazione del Registro di sistema dell'applicazione a 64 bit.|  
|RegistryView.Default|Visualizzazione del Registro di sistema che corrisponde al processo su cui è in esecuzione l'applicazione.|  

 Di seguito è riportato un esempio.  

 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  

 Ottiene i dati SLRuntimeInstallPath della chiave ReferenceAssemblies, cercandoli in primo luogo nella visualizzazione del Registro di sistema a 64 bit, quindi in quella a 32 bit.  

##  <a name="msbuild-makerelative"></a>MSBuild MakeRelative  
 La funzione di proprietà MSBuild `MakeRelative` restituisce il percorso relativo del secondo percorso relativo al primo percorso. Ogni percorso può essere un file o una cartella.  

 Questa funzione di proprietà presenta la seguente sintassi:  

```  
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```  

 Il codice seguente è un esempio di questa sintassi.  

```xml  
<PropertyGroup>  
    <Path1>c:\users\</Path1>  
    <Path2>c:\users\username\</Path2>  
</PropertyGroup>  

<Target Name = "Go">  
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />  
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />  
</Target>  

<!--  
Output:  
   username\  
   ..\  
-->  
```  

##  <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault  
 La funzione di proprietà MSBuild `ValueOrDefault` restituisce il primo argomento, a meno che non sia null o vuoto. Se il primo argomento è null o vuoto, la funzione restituisce il secondo argomento.  

 Gli esempi seguenti mostrano come viene usata questa funzione.  

```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <PropertyGroup>  
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>  
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>  
    </PropertyGroup>  

    <Target Name="MyTarget">  
        <Message Text="Value1 = $(Value1)" />  
        <Message Text="Value2 = $(Value2)" />  
    </Target>  
</Project>  

<!--  
Output:   
  Value1 = a  
  Value2 = b  
-->  
```

## <a name="see-also"></a>Vedere anche
[Proprietà di MSBuild](../msbuild/msbuild-properties.md)   
[Panoramica di MSBuild](../msbuild/msbuild.md)
