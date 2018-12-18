---
title: Scelta del motore Edge o del motore Legacy come destinazione per le API JsRT | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbc7df6c-0bc9-48f5-b9ad-b9ed31c42f92
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50947cbd619f086daecc1e09f88a4b238a36ee41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="targeting-edge-vs-legacy-engines-in-jsrt-apis"></a>Scelta del motore Edge o del motore Legacy come destinazione per le API JsRT
A partire da Windows 10, una delle modifiche che sono state apportate a Chakra (il motore JavaScript), che è allineato con la strategia di browser di Windows 10 di supportare un nuovo motore di rendering Edge, consiste nel supportare due diversi motori di Chakra:  
  
-   Il motore di Chakra precedente (chiamato anche il *motore legacy* o jscript9.dll riportato di seguito) che viene fornito con e supporta Internet Explorer 11. Questo motore è bloccato nel tempo e rimarrà sostanzialmente invariato dalla versione Win8.1/IE11.  
  
-   Il nuovo motore di Chakra (chiamato anche il *motore Edge* o chakra.dll riportato di seguito) che viene fornito con e supporta il nuovo browser di Windows 10, Microsoft Edge. Questo motore verrà aggiornato continuamente e supporterà un motore [Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx) "dinamico". Un motore Edge dinamico implica che, a differenza del motore legacy, il motore Edge non porterebbe avanti alcuna funzionalità di script del controllo delle versioni a cui acconsentire esplicitamente.  
  
 Quando si crea un'app usando l'API di hosting del runtime di JavaScript (JsRT), è possibile scegliere come destinazione il motore legacy oppure il motore Edge.  
  
-   Se è necessario mettere in evidenza la compatibilità retroattiva delle applicazioni esistenti, scegliere come destinazione il motore legacy.  
  
-   Se si vuole che l'app supporti le nuove funzionalità JavaScript mano a mano che vengono rilasciate (ad esempio, ECMAScript 6), scegliere come destinazione il motore Edge.  
  
 Questo argomento include informazioni dettagliate che descrivono come scegliere come destinazione i motori diversi.  
  
## <a name="target-your-preferred-version"></a>Scegliere come destinazione la versione preferita  
 Quando si crea un'applicazione, è possibile selezionare la versione di JsRT che supporta il motore Edge o il motore legacy. È possibile scegliere la versione JsRT in base alle indicazioni precedenti. Per consentire queste distinzioni, sono state apportate le modifiche seguenti a `JsCreateRuntime`, `JsCreateContext`e `JsStartDebugging`.  
  
 Per `JsCreateRuntime`:  
  
-   Quando la destinazione è il motore legacy, il valore di enumerazione `JsRuntimeVersionEdge` è deprecato e verrà suggerito un messaggio usando invece il valore `JsRuntimeVersionInternetExplorer11` .  
  
-   Quando la destinazione è il motore Edge, il parametro di versione viene omesso dalla funzione `JsCreateRuntime` .  
  
    ```cpp  
    JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
    ```  
  
 Per `JsCreateContext` e `JsStartDebugging`:  
  
-   Quando la destinazione è il motore legacy, viene usata l'interfaccia `IDebugApplication` per fornire i propri metodi di debug non remoti. Per il debugging, le funzioni `JsCreateContext` e `JsStartDebugging` accettano `IDebugApplication` come parametro.  
  
-   Quando la destinazione è il motore Edge, l'interfaccia `IDebugApplication` è deprecata. Il motore Chakra offre funzionalità di debug nativo e di script con il debugger di Visual Studio senza richiedere un'implementazione di `IDebugApplication` da parte dell'utente. Di conseguenza, l'interfaccia non è più un parametro per `JsCreateContext` e `JsStartDebugging` .  
  
 Le firme per le API precedenti nel motore legacy sono le seguenti:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsRuntimeVersion version, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, IDebugApplication *debugApplication, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging(IDebugApplication *debugApplication);  
```  
  
 Le firme per le API precedenti nel motore Edge sono le seguenti:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging();  
```  
  
## <a name="compile-for-your-preferred-version-using-visual-c"></a>Compilare per la versione preferita usando Visual C++  
 Quando si usa Visual C++, importare l'API JsRT includendo l'intestazione jsrt.h e assicurarsi che il file jsrt.lib sia incluso nell'elenco dei file di input del linker:  
  
```cpp  
#include <jsrt.h>  
```  
  
 ![Aggiunta di jsrt.lib come un file di input del linker](../chakra-hosting/media/js-chakra.png "JS_Chakra_")  
  
 Se si vuole scegliere come destinazione i file binari del motore Edge, è necessario definire la macro `USE_EDGEMODE_JSRT` prima di includere jsrt.h e invece di eseguire il collegamento a jsrt.lib, eseguirlo a chakrart.lib:  
  
```cpp  
#define USE_EDGEMODE_JSRT  
#include <jsrt.h>  
```  
  
 ![Aggiunta di chakrart.lib come un file di input del linker](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_")  
  
 Se si inizia con una nuova applicazione, è ora possibile cominciare a scrivere codice sull'API JsRT.  
  
## <a name="compile-for-your-preferred-version-using-net"></a>Compilare per la versione preferita usando .NET  
 Se si usano .NET e P/Invoke, è necessario modificare le dichiarazioni dell'API JsRT [DllImport] in modo da importare chakra.dll invece di jscript9.dll. Modificare anche la definizione di `JsCreateRuntime` in modo da rimuovere il parametro `JsRuntimeVersion` e la definizione di `JsCreateContext` e `JsStartDebugging` in modo da rimuovere il parametro `IDebugApplication` .  
  
 Per il motore legacy, usare il codice seguente.  
  
```c#  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsRuntimeVersion version,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    IDebugApplication debugApplication,  
    out JsContextRef newContext  
);   
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsStartDebugging(  
    IDebugApplication debugApplication,  
);  
```  
  
 Per il motore Edge, usare il codice seguente.  
  
```c#  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    out JsContextRef newContext  
);   
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsStartDebugging();  
```  
  
> [!CAUTION]
>  Se si effettua il marshalling manuale del puntatore funzione (ad esempio con LoadLibrary/GetProcAddress), è di importanza fondamentale non confondere le dichiarazioni del metodo, altrimenti si crea uno squilibrio dello stack, che produrrà un comportamento imprevedibile, ad esempio l'arresto anomalo dell'app. Lo stesso problema si verificherà se si esegue una ricerca e sostituzione globale delle istanze di jscript9.dll nel codice di importazione, perché non verrà trovato il parametro `version` che viene rilasciato.  
  
## <a name="summary"></a>Riepilogo  
 In Windows 10, le API di hosting del runtime di JavaScript si dividono in due. Le API ora supportano un motore Edge "dinamico", le cui capacità di linguaggio verranno allineate con il motore Edge "dinamico" in Microsoft Edge. È possibile sfruttare queste capacità dalle app desktop o di Windows Store per creare nuove ed entusiasmanti modalità di estensione dell'app e sfruttare le moderne competenze Web nella codebase esistente. Tuttavia, siccome ci sono sottili differenze tra le versioni precedenti, è necessario tenere presenti i punti seguenti quando si sceglie come destinazione il motore Edge o legacy.  
  
-   L'app può supportare una sola versione di JsRT per ogni processo.  
  
     Ad esempio, non è possibile creare un runtime del motore Edge e quindi un runtime del motore legacy e aspettarsi che vengano eseguiti correttamente nello stesso processo. Questo funzionamento non è supportato e potrebbe produrre un comportamento non documentato, ad esempio il mancato caricamento della seconda DLL.  
  
-   Quando si sceglie come destinazione il motore Edge, l'app potrebbe inaspettatamente acquisire nuove funzionalità quando la piattaforma sottostante viene aggiornata automaticamente.  
  
     Ad esempio, la modalità Internet Explorer 11 del runtime legacy supporta le dichiarazioni di variabili dell'ambito blocco, come `let` e `const`. Se il comportamento di gestione automatica delle versioni del motore Edge fosse stato standard in precedenza, il codice che aveva funzionato in modalità Internet Explorer 10, che non prevedeva regole dell'ambito blocco, avrebbe potuto cominciare a non funzionare con l'aggiornamento automatico della piattaforma. Questo deve essere un fattore importante nella scelta del modello runtime da usare. Nonostante si ritenga necessario scegliere come destinazione il motore Edge laddove possibile, occorre prestare attenzione all'uso delle strutture di codice JavaScript, che potrebbero non essere più valide in futuro.  
  
-   JsRT per Windows Store supporta solo il motore di Edge (chakra.dll). Le app che provano a collegarsi a qualsiasi API JsRT in jscript9.dll non otterranno la certificazione.  
  
-   È importante non confondere la dichiarazione di `JsCreateRuntime`, `JsCreateContext`e `JsStartDebugging` tra jscript9.dll e chakra.dll, perché comporterà lo squilibrio dello stack.  
  
     Quando si usano C e C++, si riceverà un errore del linker se si prova a usare la dichiarazione non corretta, a meno che non si stia eseguendo un'operazione simile alla chiamata di `LoadLibrary` e quindi di `GetProcAddress`. Gli sviluppatori .NET potrebbero non imbattersi facilmente in questo problema, quindi è necessario verificare attentamente il codice quando si usa questa funzionalità.  
  
## <a name="see-also"></a>Vedere anche  
 [Runtime JavaScript - Hosting](../chakra-hosting/javascript-runtime-hosting.md)