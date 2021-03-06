---
title: Gestire le impostazioni dell'applicazione (.NET)
description: Informazioni su come gestire le impostazioni dell'applicazione (in precedenza denominate proprietà dinamiche) che non sono incluse nel codice dell'applicazione, ma sono necessarie in fase di esecuzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: acfaf1f74f856bb90bfc16cacef20579abdcf8c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886561"
---
# <a name="manage-application-settings-net"></a>Gestire le impostazioni dell'applicazione (.NET)

Le impostazioni dell'applicazione consentono di archiviare le informazioni sull'applicazione in modo dinamico. Le impostazioni consentono di archiviare nel computer client le informazioni che non devono essere incluse nel codice dell'applicazione (ad esempio una stringa di connessione), le preferenze dell'utente e altre informazioni necessarie in fase di esecuzione.

Le impostazioni dell'applicazione sostituiscono le proprietà dinamiche usate nelle versioni precedenti di Visual Studio.

Ogni impostazione dell'applicazione deve avere un nome univoco. Tale nome può essere formato da una combinazione di lettere, numeri o un carattere di sottolineatura, non può iniziare con un numero e non può avere spazi. Il nome viene modificato tramite la proprietà `Name`.

Le impostazioni dell'applicazione possono essere archiviate come qualsiasi tipo di dati che viene serializzato come XML che abbia un oggetto `TypeConverter` che implementa `ToString`/`FromString`. I tipi più comuni sono `String`, `Integer`e `Boolean`, ma è anche possibile archiviare i valori come <xref:System.Drawing.Color>, <xref:System.Object>o come una stringa di connessione.

Anche le impostazioni dell'applicazione mantengono un valore. Il valore viene impostato con la proprietà **Valore** e deve corrispondere al tipo di dati dell'impostazione.

Inoltre, in fase di progettazione, è possibile associare le impostazioni dell'applicazione alla proprietà di un form o di un controllo.

Sono disponibili due tipi di impostazioni dell'applicazione, in base all'ambito:

- Le impostazioni con ambito di applicazione possono essere usate per informazioni quali un URL per un servizio Web o una stringa di connessione del database. Questi valori sono associati all'applicazione. Di conseguenza, gli utenti non possono modificarli in fase di esecuzione.

- Le impostazioni con ambito di utente possono essere usate per informazioni quali la memorizzazione dell'ultima posizione di un form oppure una preferenza su un tipo di carattere. Gli utenti possono modificare questi valori in fase di esecuzione.

È possibile modificare il tipo di un'impostazione usando la proprietà **Ambito** .

Il sistema del progetto archivia le impostazioni dell'applicazione in due file XML:

- un file *app.config*, creato in fase di progettazione quando si crea la prima impostazione dell'applicazione

- un file *user.config*, creato in fase di esecuzione quando l'utente che esegue l'applicazione modifica il valore di un'impostazione utente.

Le modifiche apportate alle impostazioni utente non vengono scritte su disco a meno che nell'applicazione non venga specificamente chiamato un metodo che esegua questa operazione.

## <a name="create-application-settings-at-design-time"></a>Creare impostazioni dell'applicazione in fase di progettazione

In fase di progettazione, le impostazioni dell'applicazione possono essere create in due modi, mediante la pagina **Impostazioni** di **Creazione progetti** oppure mediante la finestra **Proprietà** per un form o un controllo, che consente di associare un'impostazione direttamente a una proprietà.

Quando si crea un'impostazione con ambito di applicazione, ad esempio una stringa di connessione al database o un riferimento a risorse del server, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la Salva in *app.config* con il `<applicationSettings>` tag. (Le stringhe di connessione vengono salvate nel tag `<connectionStrings>` .)

Quando si crea un'impostazione con ambito di utente, ad esempio il tipo di carattere predefinito, la home page o la dimensione della finestra, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la Salva in *app.config* con il `<userSettings>` tag.

> [!IMPORTANT]
> Quando si archiviano stringhe di connessione in *app.config*, è necessario adottare le precauzioni per evitare di rivelare informazioni riservate, quali password o percorsi del server, nella stringa di connessione.
>
> Se si ricevono informazioni della stringa di connessione da un'origine esterna, quale un utente che immette un ID utente e una password, accertarsi che tra i valori usati per costruire la stringa di connessione non siano presenti parametri aggiuntivi in grado di modificare il comportamento della connessione.
>
> Valutare l'uso della funzionalità di configurazione protetta per crittografare le informazioni riservate nel file di configurazione. Per altre informazioni, vedere [Proteggere le informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Poiché non è presente alcun modello di file di configurazione per le librerie di classi, le impostazioni dell'applicazione non si applicano ai progetti Libreria di classi, ad eccezione dei progetti DLL di Visual Studio Tools per Office che possono avere un file di configurazione.

## <a name="use-customized-settings-files"></a>Usare file di impostazioni personalizzati

È possibile aggiungere file di impostazioni personalizzati al progetto per agevolare la gestione dei gruppi di impostazioni. Le impostazioni contenute in un unico file vengono caricate e salvate come unità. L'archiviazione delle impostazioni in file diversi per i gruppi di utilizzo frequente e di utilizzo non frequente può determinare un risparmio di tempo nel caricamento e nel salvataggio delle impostazioni.

Ad esempio, è possibile aggiungere un file, ad esempio *SpecialSettings. Settings* , al progetto. Mentre la classe `SpecialSettings` non è esposta nello spazio dei nomi `My` , **Visualizza codice** può leggere il file di impostazioni personalizzate contenente `Partial Class SpecialSettings`.

La **finestra di progettazione delle impostazioni** cerca innanzitutto il file *Settings. Settings* creato dal sistema del progetto; Questo file è il file predefinito visualizzato in **Progettazione progetti** nella scheda **Impostazioni** . *Settings. Settings* si trova nella cartella *progetto* per i [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetti e nella cartella *Proprietà* per i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetti. **Progettazione progetti** cerca quindi gli altri file di impostazioni nella cartella radice del progetto. Pertanto, è necessario inserirvi il file di impostazioni personalizzato. Se si aggiunge un file *. Settings* in un altro punto del progetto, **Progettazione progetti** non sarà in grado di individuarlo.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Accedere o modificare le impostazioni dell'applicazione in fase di esecuzione in Visual Basic

Nei progetti Visual Basic è possibile accedere alle impostazioni dell'applicazione in fase di esecuzione usando l'oggetto `My.Settings`. Nella pagina **Impostazioni** fare clic sul pulsante **Visualizzare codice** per visualizzare il file *Settings.vb*. *Settings. vb* definisce la `Settings` classe, che consente di gestire questi eventi nella classe delle impostazioni: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> , <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> e <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> . La classe `Settings` nel file *Settings.vb* è una classe parziale in cui viene visualizzato solo il codice di proprietà dell'utente, non l'intera classe generata. Per altre informazioni sull'accesso alle impostazioni dell'applicazione usando l'oggetto `My.Settings`, vedere [Accedere alle impostazioni dell'applicazione (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

I valori di qualsiasi impostazione con ambito di utente modificata dall'utente in fase di esecuzione, ad esempio la posizione di un form, vengono archiviati in un file di *user.config* . Si noti che i valori predefiniti vengono comunque salvati in *app.config*.

Se è stata modificata qualsiasi impostazione con ambito di utente in fase di esecuzione, ad esempio durante il test dell'applicazione, e si desidera ripristinare i valori predefiniti per queste impostazioni, scegliere il pulsante **Sincronizza**.

È consigliabile usare l' `My.Settings` oggetto e il file default *. Settings* per accedere alle impostazioni. Questo perché è possibile usare **Progettazione impostazioni** per assegnare proprietà alle impostazioni e, inoltre, le impostazioni utente vengono salvate automaticamente prima della chiusura dell'applicazione. L'applicazione Visual Basic può comunque accedere direttamente alle impostazioni. In tal caso, è necessario accedere alla `MySettings` classe e usare un file *. Settings* personalizzato nella radice del progetto. È necessario salvare le impostazioni utente prima di terminare l'applicazione, come per le applicazioni C#, come illustrato nella sezione seguente.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Accedere o modificare le impostazioni dell'applicazione in fase di esecuzione in C#
<!-- markdownlint-enable MD003 MD020 -->

In linguaggi diversi da Visual Basic, ad esempio C#, è necessario accedere direttamente alla classe `Settings`, come illustrato nell'esempio seguente relativo a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

È necessario chiamare in modo esplicito il metodo `Save` di questa classe wrapper per rendere persistenti le impostazioni utente. Questa operazione viene generalmente effettuata nel gestore eventi `Closing` del form principale. Nell'esempio seguente di C# viene illustrata una chiamata al metodo `Save`.

```csharp
Properties.Settings.Default.Save();
```

Per informazioni generali sull'accesso alle impostazioni dell'applicazione tramite la `Settings` classe, vedere [Cenni preliminari sulle impostazioni delle applicazioni (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Per impostazioni sullo scorrimento delle impostazioni, vedere questo [post del forum](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Vedi anche

- [Accedere alle impostazioni dell'applicazione (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
