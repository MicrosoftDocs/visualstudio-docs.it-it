---
title: Parametri dei modelli di progetti ed elementi di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c49514aeb164040ea374371cae6a61d1f7eb8948
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="template-parameters"></a>Parametri di modelli

Utilizzando i parametri nei modelli, è possibile sostituire i valori di parti di chiavi del modello, ad esempio i nomi delle classi e degli spazi dei nomi, quando viene creata un'istanza del modello. Questi parametri vengono sostituiti dalla procedura guidata di creazione modelli eseguita in background quando un utente sceglie **OK** o **Aggiungi** nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.

## <a name="declaring-and-enabling-template-parameters"></a>Dichiarazione e abilitazione dei parametri di modello

I parametri di modello vengono dichiarati nel formato $*parametro*$. Ad esempio:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Per abilitare la sostituzione dei parametri nei modelli

1. Nel file .vstemplate del modello individuare l'elemento `ProjectItem` che corrisponde all'elemento per il quale si desidera attivare la sostituzione dei parametri.

1. Impostare l'attributo `ReplaceParameters` dell'elemento `ProjectItem` su `true`.

1. Includere i parametri nella posizione appropriata nel file di codice per l'elemento del progetto. Ad esempio, il parametro seguente specifica che deve essere usato il nome di progetto sicuro per lo spazio dei nomi in un file:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parametri di modello riservati

Nella tabella seguente sono elencati i parametri di modello riservati che possono essere usati da qualsiasi modello.

|Parametro|Descrizione|
|---------------|-----------------|
|clrversion|Versione corrente di Common Language Runtime (CLR).|
|guid[1-10]|GUID usato per sostituire il GUID del progetto in un file di progetto. È possibile specificare fino a 10 GUID univoci, ad esempio `guid1`.|
|itemname|Nome specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**.|
|machinename|Nome del computer corrente, ad esempio Computer01.|
|projectname|Nome specificato dall'utente nella finestra di dialogo **Nuovo progetto**.|
|registeredorganization|Valore della chiave del Registro di sistema da HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Spazio dei nomi radice del progetto corrente. Questo parametro è valido solo per i modelli di elemento.|
|safeitemname|Nome specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento** con tutti i caratteri non sicuri e gli spazi rimossi.|
|safeprojectname|Nome specificato dall'utente nella finestra di dialogo **Nuovo progetto** con tutti i caratteri non sicuri e gli spazi rimossi.|
|ora|L'ora corrente nel formato GG/MM/AAAA 00:00:00.|
|SpecificSolutionName|Nome della soluzione. Quando l'opzione per creare una directory di soluzione è selezionata, `SpecificSolutionName` è il nome della soluzione. Quando l'opzione per creare una directory di soluzione non è selezionata, `SpecificSolutionName` è vuoto.|
|userdomain|Dominio dell'utente corrente.|
|nomeutente|Nome dell'utente corrente.|
|webnamespace|Nome del sito Web corrente. Questo parametro viene usato nel modello di modulo Web per garantire che i nomi delle classi siano univoci. Se il sito Web si trova nella directory radice del server Web, questo parametro di modello si risolve nella directory radice del server Web.|
|anno|L'anno corrente nel formato AAAA.|

> [!NOTE]
> I parametri di modello fanno distinzione tra maiuscole e minuscole.

## <a name="custom-template-parameters"></a>Parametri di modello personalizzati

Oltre ai parametri di modello riservati predefiniti usati durante la sostituzione dei parametri, è possibile specificare i propri valori e i propri parametri di modello. Per altre informazioni, vedere [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-using-the-project-name-for-a-file-name"></a>Esempio: uso del nome del progetto per un nome file

È possibile specificare nomi di file variabili per gli elementi del progetto usando un parametro nell'attributo `TargetFileName`.

L'esempio seguente specifica che il nome di un file eseguibile usi il nome del progetto, specificato da `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-safe-project-name-for-the-namespace-name"></a>Esempio: uso del nome di progetto sicuro per il nome dello spazio dei nomi

Per usare il nome di progetto sicuro per lo spazio dei nomi in un file di classe C#, usare la sintassi seguente:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

Nel file VSTEMPLATE del modello di progetto includere l'attributo `ReplaceParameters="true"` quando si fa riferimento al file:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Vedere anche

[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)  
[Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)