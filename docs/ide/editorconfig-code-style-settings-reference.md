---
title: Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig
ms.date: 03/17/2020
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 41d183a757aefd198c282ec84cd6cbe0ef37c933
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508953"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig

È possibile definire e mantenere uno stile di codice coerente nella codebase utilizzando un file [EditorConfig.You](../ide/create-portable-custom-editor-options.md) can define and maintain consistent code style in your codebase by using an EditorConfig file. EditorConfig include diverse proprietà di formattazione di base, ad esempio `indent_style` e `indent_size`. In Visual Studio è possibile configurare le impostazioni delle convenzioni per la scrittura del codice .NET anche usando un file EditorConfig. È possibile abilitare o disabilitare singole convenzioni per la scrittura del codice .NET e di configurare il livello in base al quale applicare ogni regola tramite un livello di gravità.

> [!TIP]
> - Quando si definiscono convenzioni di codifica in un file EditorConfig, si configura la modalità di configurazione degli [analizzatori](../code-quality/roslyn-analyzers-overview.md) di stili di codice incorporati in Visual Studio per analizzare il codice. Il file EditorConfig è il file di configurazione per questi analizzatori.
> - Le preferenze di stile per il codice di Visual Studio si possono impostate anche nella finestra di dialogo [Opzioni dell'editor di testo](code-styles-and-code-cleanup.md). Tuttavia, le impostazioni EditorConfig hanno la precedenza e le preferenze impostate in **Opzioni** non sono associate a un particolare progetto.

## <a name="convention-categories"></a>Categorie di convenzioni

Esistono tre categorie di convenzioni per la scrittura del codice .NET supportate:

- [Convenzioni del linguaggio](../ide/editorconfig-language-conventions.md)

   Regole relative al linguaggio C# o Visual Basic. Ad esempio, è possibile specificare regole relative all'uso di `var` o di tipi espliciti quando si definiscono le variabili oppure alla preferenza di membri con corpo di espressione.

- [Convenzioni di formattazione](../ide/editorconfig-formatting-conventions.md)

   Regole relative al layout e alla struttura del codice per renderlo più facile da leggere. Ad esempio, è possibile specificare regole per le parentesi graffe di Allman o la preferenza di spazi nei blocchi di controllo.

- [Convenzioni di denominazione](../ide/editorconfig-naming-conventions.md)

   Regole relative alla denominazione degli elementi di codice. Ad esempio, è possibile specificare che i metodi `async` devono terminare con "Async".

## <a name="example-editorconfig-file"></a>Esempio di file EditorConfig

Per aiutarti a iniziare, ecco un esempio di file *.editorconfig* con le opzioni predefinite. In Visual Studio, è possibile generare questo file e salvarlo in un progetto in **Strumenti** > **Opzioni** > **Editor di testo** > [ C **'** o **Basic**] > **Code Style** > **General**. Quindi, fare clic sul **pulsante Genera file .editorconfig dalle impostazioni** . Per ulteriori informazioni, consultate [Preferenze stile codice](code-styles-and-code-cleanup.md).

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### .NET Coding Conventions ####

# Organize usings
dotnet_separate_import_directive_groups = false
dotnet_sort_system_directives_first = false

# this. and Me. preferences
dotnet_style_qualification_for_event = false:silent
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_property = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent

# Expression-level preferences
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_object_initializer = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_compound_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:suggestion
dotnet_style_prefer_simplified_interpolation = true:suggestion

# Field preferences
dotnet_style_readonly_field = true:suggestion

# Parameter preferences
dotnet_code_quality_unused_parameters = all:suggestion

#### C# Coding Conventions ####

# var preferences
csharp_style_var_elsewhere = false:silent
csharp_style_var_for_built_in_types = false:silent
csharp_style_var_when_type_is_apparent = false:silent

# Expression-bodied members
csharp_style_expression_bodied_accessors = true:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent

# Pattern matching preferences
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion

# Null-checking preferences
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_prefer_static_local_function = true:suggestion
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:silent

# Code-block preferences
csharp_prefer_braces = true:silent
csharp_prefer_simple_using_statement = true:suggestion

# Expression-level preferences
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
csharp_style_throw_expression = true:suggestion
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
csharp_style_unused_value_expression_statement_preference = discard_variable:silent

# 'using' directive preferences
csharp_using_directive_placement = outside_namespace:silent

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = true
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = suggestion
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i

dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case

dotnet_naming_rule.non_field_members_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.non_field_members_should_be_pascal_case.symbols = non_field_members
dotnet_naming_rule.non_field_members_should_be_pascal_case.style = pascal_case

# Symbol specifications

dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.interface.required_modifiers =

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.types.required_modifiers =

dotnet_naming_symbols.non_field_members.applicable_kinds = property, event, method
dotnet_naming_symbols.non_field_members.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.non_field_members.required_modifiers =

# Naming styles

dotnet_naming_style.pascal_case.required_prefix =
dotnet_naming_style.pascal_case.required_suffix =
dotnet_naming_style.pascal_case.word_separator =
dotnet_naming_style.pascal_case.capitalization = pascal_case

dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.required_suffix =
dotnet_naming_style.begins_with_i.word_separator =
dotnet_naming_style.begins_with_i.capitalization = pascal_case
```

> [!NOTE]
> Per ulteriori informazioni sulle categorie di convenzioni di codifica .NET supportate, vedere le pagine [Convenzioni relative](../ide/editorconfig-language-conventions.md)alla lingua, [Formattazione](../ide/editorconfig-formatting-conventions.md)e Convenzioni di [denominazione.](../ide/editorconfig-naming-conventions.md)

## <a name="see-also"></a>Vedere anche

- [Azioni rapide](../ide/quick-actions.md)
- [Creare impostazioni personalizzate e portabili per l'editor](../ide/create-portable-custom-editor-options.md)
- [File di piattaforma del compilatore .NET "Roslyn" .editorconfig](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
- [File .editorconfig di Platform Runtime del compilatore .NET](https://github.com/dotnet/runtime/blob/master/.editorconfig)
