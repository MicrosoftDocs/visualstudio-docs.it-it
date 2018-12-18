---
title: Generazione del codice, compilazione e convenzioni di denominazione in Microsoft Fakes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: e154973c48bf0fd718b0361fd3bfbad8602e674d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Generazione del codice, compilazione e convenzioni di denominazione in Microsoft Fakes
Questo argomento illustra problemi e opzioni di generazione e compilazione di codice Fakes e descrive le convenzioni di denominazione per tipi, membri e parametri generati da Fakes.  
  
 **Requisiti**  
  
-   Visual Studio Enterprise  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
  
-   [Generazione e compilazione di codice](#BKMK_Code_generation_and_compilation)  
  
-   [Configurazione della generazione di codice degli stub](#BKMK_Configuring_code_generation_of_stubs)
  
-   [Filtro dei tipi](#BKMK_Type_filtering)
  
-   [Generazione di stub per classi concrete e metodi virtuali](#BKMK_Stubbing_concrete_classes_and_virtual_methods)
  
-   [Tipi interni](#BKMK_Internal_types)
  
-   [Ottimizzazione dei tempi di compilazione](#BKMK_Optimizing_build_times)
  
-   [Come evitare conflitti di nome tra gli assembly](#BKMK_Avoiding_assembly_name_clashing)  
  
-   [Convenzioni di denominazione Fakes](#BKMK_Fakes_naming_conventions)  
  
-   [Convenzioni di denominazione dei tipi shim e stub](#BKMK_Shim_type_and_stub_type_naming_conventions)
  
-   [Convenzioni di denominazione delle proprietà dei delegati shim o dei campi dei delegati stub](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions)
  
-   [Convenzioni di denominazione dei tipi di parametro](#BKMK_Parameter_type_naming_conventions)
  
-   [Regole ricorsive](#BKMK_Recursive_rules)  
  
-   [Risorse esterne](#BKMK_External_resources)  
  
-   [Linee guida](#BKMK_Guidance)  
  
##  <a name="BKMK_Code_generation_and_compilation"></a> Generazione e compilazione di codice  
  
###  <a name="BKMK_Configuring_code_generation_of_stubs"></a> Configurazione della generazione di codice degli stub  
 La generazione dei tipi stub è configurata in un file XML con estensione fakes. Il framework Fakes si integra nel processo di compilazione tramite attività MSBuild personalizzate e rileva tali file in fase di compilazione. Il generatore di codice Fakes compila i tipi stub in un assembly e aggiunge il riferimento al progetto.  
  
 L'esempio seguente illustra i tipi stub definiti in FileSystem.dll:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
    <Assembly Name="FileSystem"/>  
</Fakes>  
  
```  
  
###  <a name="BKMK_Type_filtering"></a> Filtro dei tipi  
 Per limitare i tipi per i quali è necessario generare stub, è possibile impostare filtri nel file con estensione fakes. È possibile aggiungere un numero illimitato di elementi Clear, Add e Remove nell'elemento StubGeneration per creare l'elenco dei tipi selezionati.  
  
 Il file con estensione fakes seguente, ad esempio, genera stub per i tipi negli spazi dei nomi System e System.IO, ma esclude qualsiasi tipo in System che contiene "Handle":  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Clear />  
    <Add Namespace="System!" />  
    <Add Namespace="System.IO!"/>  
    <Remove TypeName="Handle" />  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
 Le stringhe di filtro usano una grammatica semplice per definire come eseguire la corrispondenza:  
  
-   Per impostazione predefinita, i filtri non fanno distinzione tra maiuscole e minuscole e trovano la corrispondenza nelle sottostringhe:  
  
     `el` trova la corrispondenza con "hello"  
  
-   Se si aggiunge `!` alla fine del filtro, viene trovata una corrispondenza precisa con distinzione tra maiuscole e minuscole:  
  
     `el!` non trova la corrispondenza con "hello"  
  
     `hello!` trova la corrispondenza con "hello"  
  
-   Se si aggiunge `*` alla fine del filtro, viene trovata una corrispondenza con il prefisso della stringa:  
  
     `el*` non trova la corrispondenza con "hello"  
  
     `he*` trova la corrispondenza con "hello"  
  
-   Più filtri in un elenco con valori delimitati da punti e virgola vengono combinati come disgiunzione:  
  
     `el;wo` trova la corrispondenza con "hello" e "world"  
  
###  <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Generazione di stub per classi concrete e metodi virtuali  
 Per impostazione predefinita, vengono generati tipi stub per tutte le classi non sealed. È possibile limitare i tipi stub alle classi astratte tramite il file di configurazione con estensione fakes:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Types>  
      <Clear />  
      <Add AbstractClasses="true"/>  
    </Types>  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
###  <a name="BKMK_Internal_types"></a> Tipi interni  
 Il generatore di codice Fakes genera tipi shim e stub per i tipi visibili nell'assembly Fakes generato. Per fare in modo che i tipi interni di un assembly sottoposto a shim siano visibili per Fakes e l'assembly di test, aggiungere attributi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> al codice dell'assembly sottoposto a shim per dare visibilità all'assembly Fakes generato e all'assembly di test. Di seguito è riportato un esempio:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes")]  
[assembly: InternalsVisibleTo("FileSystem.Tests")]  
```  
  
 **Tipi interni in assembly con nome sicuro**  
  
 Se l'assembly sottoposto a shim ha un nome sicuro e si vuole accedere ai tipi interni dell'assembly:  
  
-   Sia l'assembly di test sia l'assembly Fakes devono avere un nome sicuro.  
  
-   È necessario aggiungere le chiavi pubbliche degli assembly di test e Fakes agli attributi **InternalsVisibleToAttribute** negli assembly sottoposti a shim. Ecco come apparirebbero gli attributi di esempio nel codice dell'assembly sottoposto a shim se tale assembly avesse un nome sicuro:  
  
    ```csharp  
    // FileSystem\AssemblyInfo.cs  
    [assembly: InternalsVisibleTo("FileSystem.Fakes",  
        PublicKey=<Fakes_assembly_public_key>)]  
    [assembly: InternalsVisibleTo("FileSystem.Tests",  
        PublicKey=<Test_assembly_public_key>)]  
    ```  
  
 Se l'assembly sottoposto a shim ha un nome sicuro, il framework Fakes firma automaticamente in modo sicuro l'assembly Fakes generato. È necessario firmare in modo sicuro l'assembly di test. Vedere [Creazione e utilizzo degli assembly con nome sicuro](http://msdn.microsoft.com/Library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Il framework Fakes usa la stessa chiave per firmare tutti gli assembly generati. È pertanto possibile usare questo frammento di codice come punto di partenza per aggiungere l'attributo **InternalsVisibleTo** per l'assembly Fakes al codice dell'assembly sottoposto a shim.  
  
```csharp  
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]  
```  
  
 È possibile specificare una chiave pubblica diversa per l'assembly Fakes, ad esempio una chiave creata per l'assembly sottoposto a shim, specificando il percorso completo del file **.snk** che contiene la chiave alternativa come valore dell'attributo `KeyFile` nell'elemento `Fakes`\\`Compilation` del file con estensione **fakes**. Ad esempio:  
  
```xml  
<-- FileSystem.Fakes.fakes -->  
<Fakes ...>  
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />  
</Fakes>  
  
```  
  
 È quindi necessario usare la chiave pubblica del file con estensione **snk** alternativo come secondo parametro dell'attributo InternalVisibleTo per l'assembly Fakes nel codice dell'assembly sottoposto a shim:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes",  
    PublicKey=<Alternate_public_key>)]  
[assembly: InternalsVisibleTo("FileSystem.Tests",  
    PublicKey=<Test_assembly_public_key>)]  
```  
  
 Nell'esempio precedente i valori `Alternate_public_key` e `Test_assembly_public_key` possono corrispondere.  
  
###  <a name="BKMK_Optimizing_build_times"></a> Ottimizzazione dei tempi di compilazione  
 La compilazione di assembly Fakes può comportare un aumento significativo del tempo di compilazione. È possibile ridurre al minimo il tempo di compilazione generando gli assembly Fakes per gli assembly di sistema .NET e gli assembly di terze parti in un progetto centralizzato separato. Poiché tali assembly vengono modificati raramente nel computer, è possibile riutilizzare gli assembly Fakes generati in altri progetti.  
  
 Dai progetti di unit test, è sufficiente usare un riferimento agli assembly Fakes compilati che si trovano in FakesAssemblies nella cartella del progetto.  
  
1.  Creare una nuova libreria di classi con la versione del runtime .NET corrispondente ai progetti di test. Verrà usato il nome Fakes.Prebuild. Rimuovere il file class1.cs dal progetto, in quanto non è necessario.  
  
2.  Aggiungere un riferimento a tutti gli assembly di sistema e di terze parti per i quali è necessario Fakes.  
  
3.  Aggiungere un file con estensione fakes per ognuno degli assembly ed eseguire la compilazione.  
  
4.  Dal progetto di test  
  
    -   Assicurarsi di disporre di un riferimento alla DLL di runtime Fakes:  
  
         C:\Programmi\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll  
  
    -   Per ogni assembly per cui è stato creato Fakes, aggiungere un riferimento al file DLL corrispondente nella cartella Fakes.Prebuild\FakesAssemblies del progetto.  
  
###  <a name="BKMK_Avoiding_assembly_name_clashing"></a> Come evitare conflitti di nome tra gli assembly  
 In un ambiente Team Build, tutti gli output di compilazione vengono uniti in una singola directory. Nel caso di più progetti che usano Fakes, assembly Fakes di versioni diverse potrebbero eseguire l'override gli uni degli altri. Ad esempio, il file mscorlib.dll di TestProject1 Fakes di .NET Framework 2.0 e il file mscorlib.dll di TestProject2 Fakes per .NET Framework 4 restituirebbero entrambi un assembly Fakes Fakes.dll.  
  
 Per evitare questo problema, Fakes deve creare automaticamente nomi di assembly Fakes con l'indicazione della versione per i riferimenti non di progetto quando vengono aggiunti file con estensione fakes. Un nome di assembly Fakes con indicazione della versione include il numero di versione che viene incorporato quando si crea il nome:  
  
 Dato un assembly MyAssembly e una versione 1.2.3.4, il nome di assembly Fakes è MyAssembly.1.2.3.4.Fakes.  
  
 È possibile modificare o rimuovere la versione modificando l'attributo Versione dell'elemento Assembly nel file con estensione fakes:  
  
```xml  
attribute of the Assembly element in the .fakes:  
<Fakes ...>  
  <Assembly Name="MyAssembly" Version="1.2.3.4" />  
  ...  
</Fakes>  
  
```  
  
##  <a name="BKMK_Fakes_naming_conventions"></a> Convenzioni di denominazione Fakes  
  
###  <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Convenzioni di denominazione dei tipi shim e stub  
 **Spazi dei nomi**  
  
-   Viene aggiunto il suffisso .Fakes allo spazio dei nomi.  
  
     Ad esempio, lo spazio dei nomi `System.Fakes` contiene i tipi shim dello spazio dei nomi System.  
  
-   Global.Fakes contiene il tipo shim dello spazio dei nomi vuoto.  
  
 **Nomi dei tipi**  
  
-   Viene aggiunto il prefisso Shim al nome del tipo per creare il nome del tipo shim.  
  
     Ad esempio, ShimExample è il tipo shim del tipo Example.  
  
-   Viene aggiunto il prefisso Stub al nome del tipo per creare il nome del tipo stub.  
  
     Ad esempio, StubIExample è il tipo di stub del tipo IExample.  
  
 **Argomenti tipo e strutture di tipi annidati**  
  
-   Gli argomenti tipo generico vengono copiati.  
  
-   La struttura dei tipi annidati viene copiata per i tipi shim.  
  
###  <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Convenzioni di denominazione delle proprietà dei delegati shim o dei campi dei delegati stub  
 **Regole di base** per la denominazione dei campi, a partire da un nome vuoto:  
  
-   Viene aggiunto il nome del metodo.  
  
-   Se il nome del metodo è un'implementazione esplicita dell'interfaccia, i punti vengono rimossi.  
  
-   Se il metodo è generico, viene aggiunto `Of`*n*, dove *n* è il numero di argomenti del metodo generico.  
  
 I **nomi di metodi speciali**, come getter o setter di proprietà, vengono trattati come descritto nella tabella seguente.  
  
|Se il metodo è un/una…|Esempio|Nome del metodo aggiunto|  
|-------------------|-------------|--------------------------|  
|**Costruttore**|`.ctor`|`Constructor`|  
|**Costruttore** statico|`.cctor`|`StaticConstructor`|  
|**Funzione di accesso** con nome di metodo composto da due parti separate da "_" (ad esempio getter proprietà)|*kind_name* (caso comune, ma non applicato da ECMA)|*NameKind*, dove entrambe le parti iniziano con una maiuscola e la loro posizione è stata scambiata|  
||Getter della proprietà `Prop`|`PropGet`|  
||Setter della proprietà `Prop`|`PropSet`|  
||Metodo di aggiunta evento|`Add`|  
||Metodo di rimozione evento|`Remove`|  
|**Operatore** costituito da due parti|`op_name`|`NameOp`|  
|Ad esempio: operatore +|`op_Add`|`AddOp`|  
|Per un **operatore di conversione**, viene aggiunto il tipo restituito.|`T op_Implicit`|`ImplicitOpT`|  
  
 **Note**  
  
-   **Getter e setter di indicizzatori** vengono trattati in modo analogo a quelli di proprietà. Il nome predefinito per un indicizzatore è `Item`.  
  
-   I nomi dei **tipi di parametro** vengono trasformati e concatenati.  
  
-   Il **tipo restituito** viene ignorato a meno che non vi sia un'ambiguità di overload. In questo caso, il tipo restituito viene aggiunto alla fine del nome.  
  
###  <a name="BKMK_Parameter_type_naming_conventions"></a> Convenzioni di denominazione dei tipi di parametro  
  
|Dato un|La stringa aggiunta è...|  
|-----------|-------------------------|  
|**Tipo**`T`|T<br /><br /> Lo spazio dei nomi, la struttura annidata e i tipi generici vengono eliminati.|  
|**Parametro Out**`out T`|`TOut`|  
|**Parametro Ref** `ref T`|`TRef`|  
|**Tipo di matrice**`T[]`|`TArray`|  
|Tipo di **matrice multidimensionale** `T[ , , ]`|`T3`|  
|Tipo di **puntatore** `T*`|`TPtr`|  
|**Tipo generico** `T<R1, ...>`|`TOfR1`|  
|**Argomento di tipo generico**`!i` del tipo `C<TType>`|`Ti`|  
|**Argomento di metodo generico**`!!i` del metodo `M<MMethod>`|`Mi`|  
|**Tipo annidato**`N.T`|Vengono aggiunti `N` e quindi `T`.|  
  
###  <a name="BKMK_Recursive_rules"></a> Regole ricorsive  
 Le regole seguenti vengono applicate in modo ricorsivo:  
  
-   Poiché Fakes usa C# per generare gli assembly Fakes, qualsiasi carattere che produrrebbe un token C# non valido viene fatto precedere da un carattere di escape "_" (carattere di sottolineatura).  
  
-   Se un nome risultante è in conflitto con qualsiasi membro del tipo dichiarante, viene usato uno schema di numerazione aggiungendo un contatore a due cifre, a partire da 01.  
  
##  <a name="BKMK_External_resources"></a> Risorse esterne  
  
###  <a name="BKMK_Guidance"></a> Materiale sussidiario  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188) (Test per il recapito continuo con Visual Studio 2012 - Capitolo 2: Testing unità: Test interni)  
  
## <a name="see-also"></a>Vedere anche  
 [Isolamento del codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
