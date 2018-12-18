---
title: Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig in Visual Studio | Microsoft Docs
ms.date: 02/28/2018
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language conventions [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e69d7e291d1b13a5205aa4798c78c6a4e337db50
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig

In Visual Studio 2017 l'uso di un file [EditorConfig](../ide/create-portable-custom-editor-options.md) consente di definire e mantenere uno stile di codice coerente nella propria codebase. EditorConfig include diverse proprietà di formattazione di base, ad esempio `indent_style` e `indent_size`. In Visual Studio è possibile configurare le impostazioni delle convenzioni per la scrittura del codice .NET anche usando un file EditorConfig. I file EditorConfig consentono di abilitare o disabilitare singole convenzioni per la scrittura del codice .NET e di configurare il livello in base al quale applicare la convenzione tramite un livello di gravità. Per altre informazioni su come usare EditorConfig per garantire la coerenza nella propria codebase, vedere [Creare impostazioni personalizzate e portabili per l'editor](../ide/create-portable-custom-editor-options.md). Per un esempio, è inoltre possibile esaminare il [file .editorconfig in .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig).

Esistono tre categorie di convenzioni per la scrittura del codice .NET supportate:

- [Convenzioni del linguaggio](#language-conventions)

   Regole relative al linguaggio C# o Visual Basic. Ad esempio, è possibile specificare regole relative all'uso di `var` o di tipi espliciti quando si definiscono le variabili oppure alla preferenza di membri con corpo di espressione.

- [Convenzioni di formattazione](#formatting-conventions)

   Regole relative al layout e alla struttura del codice per renderlo più facile da leggere. Ad esempio, è possibile specificare regole per le parentesi graffe di Allman o la preferenza di spazi nei blocchi di controllo.

- [Convenzioni di denominazione](../ide/editorconfig-naming-conventions.md)

   Regole relative alla denominazione degli elementi di codice. Ad esempio, è possibile specificare che i metodi `async` devono terminare con "Async".

## <a name="language-conventions"></a>Convenzioni del linguaggio

Le regole per le convenzioni del linguaggio hanno il formato seguente:

`options_name = false|true : none|suggestion|warning|error`

Per ogni regola di convenzione del linguaggio è necessario specificare **true** (preferire questo stile) o **false** (non preferire questo stile) e un livello di **gravità**. La gravità specifica il livello di imposizione per lo stile.

Nella tabella seguente sono elencati i valori di gravità possibili e i relativi effetti:

Gravità | Effetto
:------- | ------
none o silent | Quando questa regola viene violata non viene visualizzato alcun avviso all'utente. Le funzionalità di generazione del codice genereranno tuttavia il codice in questo stile.
suggestion | Quando questa regola di stile viene violata, viene visualizzato un suggerimento all'utente. I suggerimenti vengono visualizzati come tre punti grigi sotto i primi due caratteri.
avviso | Quando questa regola di stile viene violata, viene visualizzato un avviso del compilatore.
errore | Quando questa regola di stile viene violata, viene visualizzato un errore del compilatore.

L'elenco seguente illustra le regole di convenzione del linguaggio consentite:

- Impostazioni di stile del codice .NET
    - [Qualificatori "This." e "Me."](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Parole chiave del linguaggio anziché nomi dei tipi di framework per i riferimenti ai tipi](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Preferenze del modificatore](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
    - [Preferenze a livello di espressione](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_prefer\_inferred\_tuple_names
        - dotnet\_prefer\_inferred\_anonymous\_type\_member_names
    - [Preferenze controllo "Null"](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Impostazioni di stile del codice C#
    - [Tipi impliciti ed espliciti](#var)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Membri con corpo di espressione](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Criteri di ricerca](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [Dichiarazioni di variabili inline](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Preferenze a livello di espressione](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - [Preferenze controllo "Null"](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Preferenze per i blocchi di codice](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Impostazioni di stile del codice .NET

Le regole di stile illustrate in questa sezione sono applicabili a C# e Visual Basic. Per vedere esempi di codice nel linguaggio di programmazione preferito, selezionarlo nel menu a discesa **Linguaggio** nell'angolo superiore destro della finestra del browser.

#### <a name="this_and_me">Qualificatori "This." e "Me."</a>

È possibile applicare questa regola di stile (ID regola IDE0003 e IDE0009) a campi, proprietà, metodi o eventi. Il valore **true** indica la preferenza a far precedere il simbolo del codice da `this.` in C# o da `Me.` in Visual Basic. Il valore **false** indica la preferenza a _non_ far precedere l'elemento di codice da `this.` o da `Me.`.

Nella tabella seguente sono riportati i nomi delle regole, i linguaggi di programmazione applicabili e i valori predefiniti:

| Nome regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# e Visual Basic | false:none |
| dotnet_style_qualification_for_property | C# e Visual Basic | false:none |
| dotnet_style_qualification_for_method | C# e Visual Basic | false:none |
| dotnet_style_qualification_for_event | C# e Visual Basic | false:none |

**dotnet\_style\_qualification\_for_field**

- Quando questa regola è impostata su **true** indica la preferenza a far precedere i campi da `this.` in C# o da `Me.` in Visual Basic.
- Quando questa regola è impostata su **false** indica la preferenza a _non_ far precedere i campi da `this.` o da `Me.`.

Esempi di codice:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- Quando questa regola è impostata su **true** indica la preferenza a far precedere le proprietà da `this.` in C# o da `Me.` in Visual Basic.
- Quando questa regola è impostata su **false** indica la preferenza a _non_ far precedere le proprietà da `this.` o da `Me.`.

Esempi di codice:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**dotnet\_style\_qualification\_for_method**

- Quando questa regola è impostata su **true** indica la preferenza a far precedere i metodi da `this.` in C# o da `Me.` in Visual Basic.
- Quando questa regola è impostata su **false** indica la preferenza a _non_ far precedere i metodi da `this.` o da `Me.`.

Esempi di codice:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**dotnet\_style\_qualification\_for_event**

- Quando questa regola è impostata su **true** indica la preferenza a far precedere gli eventi da `this.` in C# o da `Me.` in Visual Basic.
- Quando questa regola è impostata su **false** si indica la preferenza a _non_ far precedere gli eventi da `this.` o da `Me.`.

Esempi di codice:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

Queste regole possono essere visualizzate in un file .editorconfig come indicato di seguito:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords">Parole chiave del linguaggio anziché nomi dei tipi di framework per i riferimenti ai tipi</a>

È possibile applicare questa regola di stile a variabili locali, parametri dei metodi e membri delle classi oppure come regola separata alle espressioni di accesso ai membri di tipo. Il valore **true** indica la preferenza per la parola chiave del linguaggio (ad esempio, `int` o `Integer`) rispetto al nome del tipo (ad esempio, `Int32`) per i tipi con una parola chiave che li rappresenta. Il valore **false** indica la preferenza per il nome del tipo rispetto alla parola chiave del linguaggio.

Nella tabella seguente sono riportati i nomi delle regole, gli ID delle regole, i linguaggi di programmazione applicabili e i valori predefiniti:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 e IDE0014 | C# e Visual Basic | true:none |
| dotnet_style_predefined_type_for_member_access | IDE0013 e IDE0015 | C# e Visual Basic | true:none |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- Quando questa regola è impostata su **true** indica la preferenza per la parola chiave per variabili locali, parametri dei metodi e membri delle classi rispetto al nome del tipo per i tipi con una parola chiave che li rappresenta.
- Quando questa regola è impostata su **false** indica la preferenza per il nome del tipo per variabili locali, parametri dei metodi e membri delle classi rispetto alla parola chiave del linguaggio.

Esempi di codice:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**dotnet\_style\_predefined\_type\_for\_member_access**

- Quando questa regola è impostata su **true** indica la preferenza per la parola chiave per le espressioni di accesso ai membri rispetto al nome del tipo per i tipi con una parola chiave che li rappresenta.
- Quando questa regola è impostata su **false** indica la preferenza per il nome del tipo per le espressioni di accesso ai membri rispetto alla parola chiave del linguaggio.

Esempi di codice:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

Queste regole possono essere visualizzate in un file .editorconfig come indicato di seguito:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers">Preferenze del modificatore</a>

Le regole di stile in questa sezione riguardano le preferenze del modificatore, inclusa la richiesta di modificatori dell'accessibilità e la specifica dell'ordinamento preferito dei modificatori.

Nella tabella seguente sono riportati i nomi delle regole, gli ID delle regole, i linguaggi di programmazione applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# e Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:none | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:none | 15.5 |

**dotnet\_style\_require\_accessibility_modifiers**

Questa regola non accetta un valore **true** o **false**; accetta invece un valore della tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| always | Preferisce che vengano specificati i modificatori dell'accessibilità |
| for\_non\_interface_members | Preferisce modificatori dell'accessibilità da dichiarare, fatta eccezione per i membri di interfaccia pubblica. Questa impostazione non è attualmente diversa da **always** e funzionerà da strumento di correzione futuro se C# aggiungerà metodi di interfaccia predefiniti. |
| never | Non preferisce i modificatori dell'accessibilità da specificare |

Esempi di codice:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst= "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst= "constant";
}
```

**csharp_preferred_modifier_order**

- Quando questa regola è impostata su un elenco di modificatori, p l'ordinamento specificato.
- Quando questa regola viene omessa dal file, non preferisce un ordine di modificatori.

Esempi di codice:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Quando questa regola è impostata su un elenco di modificatori, p l'ordinamento specificato.
- Quando questa regola viene omessa dal file, non preferisce un ordine di modificatori.

Esempi di codice:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

Queste regole possono essere visualizzate in un file .editorconfig come indicato di seguito:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="expression_level">Preferenze a livello di espressione</a>

Le regole di stile in questa sezione riguardano preferenze a livello di espressione, incluso l'uso di inizializzatori di oggetto, inizializzatori di raccolta, nomi di tupla espliciti o dedotti e tipi anonimi dedotti.

Nella tabella seguente sono riportati i nomi delle regole, gli ID delle regole, i linguaggi di programmazione applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# e Visual Basic | true:suggestion | Prima versione |
| dotnet_style_collection_initializer | IDE0028 | C# e Visual Basic | true:suggestion | Prima versione |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ e Visual Basic 15+ | true:suggestion | Prima versione |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1+ e Visual Basic 15+ | true:suggestion | 15.6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# e Visual Basic | true:suggestion | 15.6 |

**dotnet\_style\_object_initializer**

- Quando questa regola è impostata su **true** indica la preferenza a inizializzare gli oggetti usando gli inizializzatori di oggetto, laddove possibile.
- Quando questa regola è impostata su **false** indica la preferenza a *non* inizializzare gli oggetti usando gli inizializzatori di oggetto.

Esempi di codice:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**

- Quando questa regola è impostata su **true** indica la preferenza a inizializzare le raccolte usando gli inizializzatori di insieme, laddove possibile.
- Quando questa regola è impostata su **false** indica la preferenza a *non* inizializzare le raccolte usando gli inizializzatori di insieme.

Esempi di codice:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**dotnet\_style\_explicit\_tuple_names**

- Quando questa regola è impostata su **true** indica la preferenza per i nomi di tupla rispetto alle proprietà ItemX.
- Quando questa regola è impostata su **false** indica la preferenza per le proprietà ItemX rispetto ai nomi di tupla.

Esempi di codice:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_prefer\_inferred\_tuple_names**

- Quando questa regola è impostata su **true** indica la preferenza per i nomi di elemento di tupla dedotti.
- Quando questa regola è impostata su **false** indica la preferenza per i nomi di elemento di tupla espliciti.

Esempi di codice:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Quando questa regola è impostata su **true** indica la preferenza per i nomi di membro di tipo anonimo dedotti.
- Quando questa regola è impostata su **false** indica la preferenza per i nomi di membro di tipo anonimo espliciti.

Esempi di codice:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };

```

Queste regole possono essere visualizzate in un file .editorconfig come indicato di seguito:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
```

#### <a name="null_checking">Preferenze di controllo dei valori Null</a>

Le regole di stile in questa sezione riguardano le preferenze di controllo dei valori Null.

Nella tabella seguente sono riportati i nomi delle regole, gli ID delle regole, i linguaggi di programmazione applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# e Visual Basic | true:suggestion | Prima versione |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ e Visual Basic 14+ | true:suggestion | Prima versione |

**dotnet\_style\_coalesce_expression**

- Quando questa regola è impostata su **true** indica la preferenza per le espressioni di unione Null rispetto al controllo degli operatori ternari.
- Quando questa regola è impostata su **false** indica la preferenza per il controllo degli operatori ternari rispetto alle espressioni di unione Null.

Esempi di codice:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- Quando questa regola è impostata su **true** indica la preferenza a usare l'operatore condizionale Null, laddove possibile.
- Quando questa regola è impostata su **false** indica la preferenza a usare il controllo Null ternario, laddove possibile.

Esempi di codice:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

Queste regole possono essere visualizzate in un file .editorconfig come indicato di seguito:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Impostazioni di stile del codice C#

Le regole di stile illustrate in questa sezione sono applicabili solo a C#.

#### <a name="var">Tipi impliciti ed espliciti</a>

Le regole di stile illustrate in questa sezione (ID regola IDE0007 e IDE0008) riguardano l'uso della parola chiave [var](/dotnet/csharp/language-reference/keywords/var) rispetto a un tipo esplicito in una dichiarazione di variabile. Questa regola può essere applicata separatamente ai tipi predefiniti, quando il tipo è apparente, e altrove.

Nella tabella seguente sono riportati i nomi delle regole, i linguaggi di programmazione applicabili e i valori predefiniti:

| Nome regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:none |
| csharp_style_var_when_type_is_apparent | C# | true:none |
| csharp_style_var_elsewhere | C# | true:none |

**csharp\_style\_var\_for\_built\_in_types**

- Quando questa regola è impostata su **true** indica la preferenza a usare `var` per dichiarare le variabili con tipi di sistema predefiniti, ad esempio `int`.
- Quando questa regola è impostata su **false** indica la preferenza a usare un tipo esplicito invece della parola chiave `var` per dichiarare le variabili con tipi di sistema predefiniti, ad esempio `int`.

Esempi di codice:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Quando questa regola è impostata su **true** indica la preferenza per `var` quando il tipo è già menzionato nel lato destro di un'espressione di dichiarazione.
- Quando questa regola è impostata su **false** indica la preferenza a usare un tipo esplicito invece della parola chiave `var` quando il tipo è già menzionato nel lato destro di un'espressione di dichiarazione.

Esempi di codice:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Quando questa regola è impostata su **true** indica la preferenza per `var` rispetto a un tipo esplicito in tutti i casi, a meno che non venga sostituita da un'altra regola di stile del codice.
- Quando questa regola è impostata su **false** indica la preferenza a usare un tipo esplicito rispetto a `var` in tutti i casi, a meno che non venga sostituita da un'altra regola di stile del codice.

Esempi di codice:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members">Membri con corpo di espressione</a>

Le regole di stile illustrate in questa sezione riguardano l'uso di [membri con corpo di espressione](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) quando la logica è costituita da una sola espressione. Questa regola può essere applicata a metodi, costruttori, operatori, proprietà, indicizzatori e funzioni di accesso.

Nella tabella seguente sono riportati i nomi delle regole, gli ID delle regole, le versioni dei linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 e IDE0024 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:none | 15.3 |

**csharp\_style\_expression\_bodied_methods**

La regola accetta valori dalla tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| true | Preferisce membri con corpo di espressione per i metodi |
| when_on_single_line | Preferisce membri con corpo di espressione per i metodi quando sono a riga singola |
| False | Preferisce corpi di blocco per i metodi |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

La regola accetta valori dalla tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| true | Preferisce membri con corpo di espressione per i costruttori |
| when_on_single_line | Preferisce membri con corpo di espressione per i costruttori quando sono a riga singola |
| False | Preferisce corpi di blocco per i costruttori |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

La regola accetta valori dalla tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| true | Preferisce membri con corpo di espressione per gli operatori |
| when_on_single_line | Preferisce membri con corpo di espressione per gli operatori quando sono a riga singola |
| False | Preferisce corpi di blocco per gli operatori |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

La regola accetta valori dalla tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| true | Preferisce membri con corpo di espressione per le proprietà |
| when_on_single_line | Preferisce membri con corpo di espressione per le proprietà quando sono a riga singola |
| False | Preferisce corpi di blocco per le proprietà |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

La regola accetta valori dalla tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| true | Preferisce membri con corpo di espressione per gli indicizzatori |
| when_on_single_line | Preferisce membri con corpo di espressione per gli indicizzatori quando sono a riga singola |
| False | Preferisce corpi di blocco per gli indicizzatori |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _value[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

La regola accetta valori dalla tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| true | Preferisce membri con corpo di espressione per le funzioni di accesso |
| when_on_single_line | Preferisce membri con corpo di espressione per le funzioni di accesso quando sono a riga singola |
| False | Preferisce corpi di blocco per le funzioni di accesso |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching">Criteri di ricerca</a>

Le regole di stile illustrate in questa sezione riguardano l'uso dei [criteri di ricerca](/dotnet/csharp/pattern-matching) in C#.

Nella tabella seguente sono riportati i nomi delle regole, gli ID delle regole, le versioni del linguaggio applicabili e i valori predefiniti:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Quando questa regola è impostata su **true** indica la preferenza dei criteri di ricerca rispetto alle espressioni `is` con i cast di tipo.
- Quando questa regola è impostata su **false** indica la preferenza delle espressioni `is` con i cast di tipo invece dei criteri di ricerca.

Esempi di codice:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Quando questa regola è impostata su **true** indica la preferenza dei criteri di ricerca anziché le espressioni `as` con i controlli Null per determinare se un elemento è di un determinato tipo.
- Quando questa regola è impostata su **false** indica la preferenza delle espressioni `as` con i controlli Null anziché i criteri di ricerca per determinare se un elemento è di un determinato tipo.

Esempi di codice:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations">Dichiarazioni di variabili inline</a>

Questa regola di stile riguarda la possibilità o meno di dichiarare le variabili `out` inline. A partire da C# 7 è possibile [dichiarare una variabile out nell'elenco di argomenti di una chiamata al metodo](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument) anziché in una dichiarazione di variabile separata.

Nella tabella seguente sono riportati il nome della regola, l'ID della regola, le versioni del linguaggio applicabili e i valori predefiniti:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- Quando questa regola è impostata su **true** indica la preferenza di dichiarare le variabili `out` inline nell'elenco di argomenti di una chiamata al metodo, laddove possibile.
- Quando questa regola è impostata su **false** indica la preferenza di dichiarare le variabili `out` prima della chiamata al metodo.

Esempi di codice:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp">Preferenze a livello di espressione</a>

Le regole di stile in questa sezione riguardano le preferenze a livello di espressione, incluso l'uso di [espressioni predefinite](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), variabili decostruite e funzioni locali su funzioni anonime.

Nella tabella seguente sono riportati il nome della regola, l'ID della regola, le versioni dei linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0+ | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0+ | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Questa regola di stile riguarda l'uso del [valore letterale `default` per le espressioni con valore predefinito](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) quando il compilatore è in grado di eseguire l'inferenza del tipo dell'espressione.

- Quando questa regola è impostata su **true** indica la preferenza di `default` rispetto a `default(T)`.
- Quando questa regola è impostata su **false** indica la preferenza di `default(T)` rispetto a `default`.

Esempi di codice:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Quando questa regola è impostata su **true**, preferisce la dichiarazione di variabili decostruite.
- Quando questa regola è impostata su **false**, non preferisce la dichiarazione di variabili decostruite.

Esempi di codice:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Quando questa regola è impostata su **true**, preferisce le funzioni locali alle funzioni anonime.
- Quando questa regola è impostata su **false**, preferisce le funzioni anonime alle funzioni locali.

Esempi di codice:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp">Preferenze controllo "Null"</a>

Queste regole di stile riguardano la sintassi relativa al controllo `null`, incluso l'uso delle espressioni `throw` o delle istruzioni `throw`, nonché la possibilità di eseguire un controllo Null o usare l'operatore di unione condizionale (`?.`) quando viene chiamata un'[espressione lambda](/dotnet/csharp/lambda-expressions).

Nella tabella seguente sono riportati i nomi delle regole, gli ID delle regole, le versioni del linguaggio applicabili e i valori predefiniti:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion |

**csharp\_style\_throw_expression**

- Quando questa regola è impostata su **true** indica la preferenza a usare le espressioni `throw` anziché le istruzioni `throw`.
- Quando questa regola è impostata su **false** indica la preferenza a usare le istruzioni `throw` anziché le espressioni `throw`.

Esempi di codice:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Quando questa regola è impostata su **true** indica la preferenza a usare l'operatore di unione condizionale (`?.`) quando viene chiamata un'espressione lambda, anziché eseguire un controllo Null.
- Quando questa regola è impostata su **false** indica la preferenza a eseguire un controllo Null prima di chiamare un'espressione lambda, anziché usare l'operatore di unione condizionale (`?.`).

Esempi di codice:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block">Preferenze per i blocchi di codice</a>

Questa regola di stile riguarda l'uso delle parentesi graffe `{ }` per racchiudere i blocchi di codice.

Nella tabella seguente sono riportati il nome della regola, l'ID della regola, le versioni dei linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | ID regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_braces | IDE0011 | C# | true:none | 15.3 |

**csharp\_prefer\_braces**

- Quando questa regola è impostata su **true** indica la preferenza a usare le parentesi graffe anche per una riga di codice.
- Quando questa regola è impostata su **false** indica la preferenza a non usare le parentesi graffe, se consentito.

Esempi di codice:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Convenzioni di formattazione

La maggior parte delle regole per le convenzioni di formattazione ha il formato seguente:

`rule_name = false|true`

Specificare **true** (preferire questo stile) o **false** (non preferire questo stile). Non specificare un livello di gravità. Per alcune regole, anziché true o false, è necessario specificare altri valori per descrivere quando e dove applicare la regola.

Nell'elenco seguente sono illustrate le regole delle convenzioni di formattazione disponibili in Visual Studio:

- Impostazioni di formattazione .NET
    - [Organizzare direttive using](#usings)
        - dotnet_sort_system_directives_first
- Impostazioni di formattazione C#
    - [Opzioni dei caratteri di nuova riga](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Opzioni di rientro](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Opzioni di spaziatura](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
    - [Opzioni di ritorno a capo](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Impostazioni di formattazione .NET

Le regole di formattazione illustrate in questa sezione sono applicabili a C# e Visual Basic.

#### <a name="usings">Organizzare direttive using</a>

Questa regola di formattazione riguarda il posizionamento delle direttive using System.* rispetto ad altre direttive using.

Nella tabella seguente sono riportati il nome della regola, i linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_sort_system_directives_first |  C# e Visual Basic | true | 15.3  |

**dotnet\_sort\_system\_directives_first**

- Quando questa regola è impostata su **true** indica che le direttive using System.* verranno ordinate alfabeticamente e posizionate prima di altre direttive using.
- Quando questa regola è impostata su **false** indica che le direttive using System.* non verranno posizionate prima di altre direttive using.

Esempi di codice:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Esempio di file .editorconfig:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

### <a name="c-formatting-settings"></a>Impostazioni di formattazione C#

Le regole di formattazione illustrate in questa sezione si applicano solo al codice C#.

#### <a name="newline">Opzioni dei caratteri di nuova riga</a>

Queste regole di formattazione riguardano l'uso di nuove righe per formattare il codice.

Nella tabella seguente sono riportati i nomi delle regole relative alla "nuova riga", i linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_new_line_before_open_brace |  C# | tutti | 15.3  |
| csharp_new_line_before_else |  C# | true | 15.3  |
| csharp_new_line_before_catch |  C# | true | 15.3  |
| csharp_new_line_before_finally |  C# | true | 15.3  |
| csharp_new_line_before_members_in_object_initializers |  C# | true | 15.3  |
| csharp_new_line_before_members_in_anonymous_types |  C# | true | 15.3  |
| csharp_new_line_between_query_expression_clauses |  C# | true | 15.3  |

**csharp\_new\_line\_before\_open_brace**

Questa regola riguarda il posizionamento di una parentesi graffa di apertura `{` nella stessa riga del codice precedente o in una nuova riga. Per questa regola, non specificare **true** o **false**. Specificare invece **all**, **none** oppure uno o più elementi di codice, ad esempio **methods** o **properties**, per definire quando applicare questa regola. L'elenco completo dei valori consentiti è riportato nella tabella seguente:

| Valore | Descrizione
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection, properties, types.<br>Per più tipi di valore, separarli con ",". | Richiede le parentesi graffe in una nuova riga per gli elementi di codice specificati (anche noto come stile "Allman") |
| tutti | Richiede le parentesi graffe in una nuova riga per tutte le espressioni (stile "Allman") |
| none | Richiede le parentesi graffe nella stessa riga per tutte le espressioni ("K&R") |

Esempi di codice:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- Quando questa regola è impostata su **true**, posizionare le istruzioni `else` in una nuova riga.
- Quando questa regola è impostata su **false**, posizionare le istruzioni `else` nella stessa riga.

Esempi di codice:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- Quando questa regola è impostata su **true**, posizionare le istruzioni `catch` in una nuova riga.
- Quando questa regola è impostata su **false**, posizionare le istruzioni `catch` nella stessa riga.

Esempi di codice:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- Quando questa regola è impostata su **true**, le istruzioni `finally` devono essere posizionate in una nuova riga dopo la parentesi graffa di chiusura.
- Quando questa regola è impostata su **false**, le istruzioni `finally` devono essere posizionate nella stessa riga della parentesi graffa di chiusura.

Esempi di codice:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- Quando questa regola è impostata su **true**, i membri degli inizializzatori di oggetto devono essere posizionati in righe separate.
- Quando questa regola è impostata su **false**, i membri degli inizializzatori di oggetto devono essere posizionati nella stessa riga.

Esempi di codice:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- Quando questa regola è impostata su **true**, i membri dei tipi anonimi devono essere posizionati in righe separate.
- Quando questa regola è impostata su **false**, i membri dei tipi anonimi devono essere posizionati nella stessa riga.

Esempi di codice:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Quando questa regola è impostata su **true**, gli elementi delle clausole di espressione di query devono essere posizionati in righe separate.
- Quando questa regola è impostata su **false**, gli elementi delle clausole di espressione di query devono essere posizionati nella stessa riga.

Esempi di codice:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent">Opzioni di rientro</a>

Queste regole di formattazione riguardano l'uso del rientro per formattare il codice.

Nella tabella seguente sono riportati i nomi delle regole, i linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_indent_case_contents |  C# | true | 15.3  |
| csharp_indent_switch_labels |  C# | true | 15.3  |
| csharp_indent_labels |  C# | no_change | 15.3  |

**csharp\_indent\_case_contents**

- Quando questa regola è impostata su **true** viene impostato un rientro per il contenuto `switch` case.
- Quando questa regola è impostata su **false** non viene impostato un rientro per il contenuto `switch` case.

Esempi di codice:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- Quando questa regola è impostata su **true** viene impostato un rientro per le etichette `switch`.
- Quando questa regola è impostata su **false** non viene impostato un rientro per le etichette `switch`.

Esempi di codice:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

Questa regola non accetta un valore **true** o **false**; accetta invece un valore della tabella seguente:

| Valore | Descrizione |
| ----- |:----------- |
| flush_left | Le etichette vengono posizionate nella colonna più a sinistra |
| one_less_than_current | Le etichette vengono posizionate con un rientro minore rispetto al contesto corrente |
| no_change | Le etichette vengono posizionate con lo stesso rientro del contesto corrente |

Esempi di codice:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing">Opzioni di spaziatura</a>

Queste regole di formattazione riguardano l'uso degli spazi per formattare il codice.

Nella tabella seguente sono riportati i nomi delle regole, i linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_space_after_cast |  C# | False | 15.3  |
| csharp_space_after_keywords_in_control_flow_statements |  C# | true | 15.3  |
| csharp_space_between_method_declaration_parameter_list_parentheses |  C# | False | 15.3  |
| csharp_space_between_method_call_parameter_list_parentheses |  C# | False | 15.3  |
| csharp_space_between_parentheses |  C# | False | 15.3  |

**csharp\_space\_after_cast**

- Quando questa regola è impostata su **true** è necessario uno spazio tra il cast e il valore.
- Quando questa regola è impostata su **false** _non_ sono necessari spazi tra il cast e il valore.

Esempi di codice:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Quando questa regola è impostata su **true** è necessario uno spazio dopo una parola chiave nell'istruzione di un flusso di controllo, ad esempio un ciclo `for`.
- Quando questa regola è impostata su **false** _non_ sono necessari spazi dopo una parola chiave nell'istruzione di un flusso di controllo, ad esempio un ciclo `for`.

Esempi di codice:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Quando questa regola è impostata su **true** inserire uno spazio dopo la parentesi di apertura e prima della parentesi di chiusura dell'elenco di parametri di una dichiarazione di metodo.
- Quando questa regola è impostata su **false** non inserire spazi dopo la parentesi di apertura e prima della parentesi di chiusura dell'elenco di parametri di una dichiarazione di metodo.

Esempi di codice:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Quando questa regola è impostata su **true** inserire uno spazio dopo la parentesi di apertura e prima della parentesi di chiusura della chiamata a un metodo.
- Quando questa regola è impostata su **false** non inserire spazi dopo la parentesi di apertura e prima della parentesi di chiusura della chiamata a un metodo.

Esempi di codice:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Questa regola accetta uno o più valori dalla tabella seguente:

| Valore | Descrizione |
| ----- |:------------|
| control_flow_statements | Inserisce uno spazio tra le parentesi delle istruzioni del flusso di controllo |
| espressioni | Inserisce uno spazio tra le parentesi delle espressioni |
| type_casts | Inserisce uno spazio tra le parentesi dei cast di tipo |

Se si omette questa regola, o si usa un valore diverso da `control_flow_statements`, `expressions` o `type_casts`, l'impostazione non viene applicata.

Esempi di codice:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
```

#### <a name="wrapping">Opzioni di ritorno a capo</a>

Queste regole di formattazione riguardano l'uso di singole righe e righe separate per istruzioni e blocchi di codice.

Nella tabella seguente sono riportati i nomi delle regole, i linguaggi applicabili, i valori predefiniti e la prima versione supportata di Visual Studio:

| Nome regola | Linguaggi applicabili | Impostazione predefinita di Visual Studio | Versione di Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_preserve_single_line_statements |  C# | true | 15.3  |
| csharp_preserve_single_line_blocks |  C# | true | 15.3  |

**csharp_preserve_single_line_statements**

- Quando questa regola è impostata su **true** le istruzioni e le dichiarazioni dei membri vengono lasciate nella stessa riga.
- Quando questa regola è impostata su **false** le istruzioni e le dichiarazioni dei membri vengono lasciate in righe diverse.

Esempi di codice:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Quando questa regola è impostata su **true** il blocco di codice viene lasciato in una singola riga.
- Quando questa regola è impostata su **false** il blocco di codice viene lasciato in righe separate.

Esempi di codice:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

Esempio di file .editorconfig:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="see-also"></a>Vedere anche

- [Azioni rapide](../ide/quick-actions.md)
- [.NET naming conventions for EditorConfig](../ide/editorconfig-naming-conventions.md) (Convenzioni di denominazione .NET per EditorConfig)
- [Creare impostazioni personalizzate e portabili per l'editor](../ide/create-portable-custom-editor-options.md)
- [File .editorconfig in .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
