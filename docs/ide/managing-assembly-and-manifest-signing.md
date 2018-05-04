---
title: Gestione delle firme di assembly e manifesti
ms.date: 02/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 431daee3571efdab666867dc8e1a3a5d17b92b39
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="manage-assembly-and-manifest-signing"></a>Gestione delle firme di assembly e manifesti

La firma con nome sicuro offre un'identità univoca globale per un componente software. I nomi sicuri sono usati per garantire che l'assembly non possa essere sottoposto a spoofing da parte di altri utenti e per verificare che le dipendenze dei componenti e le istruzioni di configurazione siano mappate al componente e alla versione del componente corretti.

 Un nome sicuro è costituito dall'identità dell'assembly, corrispondente al nome semplice in formato testo, al numero di versione e alle informazioni sulle impostazioni cultura, più un token di chiave pubblica e una firma digitale.

 Per informazioni sulla firma degli assembly nei progetti Visual Basic e C#, vedere [Creare e usare gli assembly con nome sicuro](http://msdn.microsoft.com/Library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

 Per informazioni sulla firma degli assembly nei progetti Visual C++, vedere [Assembly con nome sicuro (firma degli assembly) (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> La firma con nome sicuro non offre protezione da attacchi di reverse engineering dell'assembly.  Per proteggere da attacchi di reverse engineering, vedere [Dotfuscator Community Edition (CE)](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Tipi di asset e firma

È possibile firmare gli assembly .NET e i manifesti dell'applicazione, tra cui:

-   file eseguibili (*.exe*)

-   manifesti dell'applicazione (*.exe.manifest*)

-   manifesti della distribuzione (*.application*)

-   assembly di componenti condivisi (*.dll*)

È necessario firmare i seguenti tipi di asset:

1.  Assembly, se si vuole distribuirli alla Global Assembly Cache (GAC).

2.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti di applicazione e distribuzione. Visual Studio abilita la firma per impostazione predefinita per queste applicazioni.

3.  Assembly di interoperabilità primari, usati per l'interoperabilità COM. L'utilità TLBIMP attiva l'assegnazione di nomi sicuri quando crea un assembly di interoperabilità primario da una libreria di tipi COM.

In generale è consigliabile non firmare i file eseguibili. Un componente con nome sicuro non può fare riferimento a un componente senza nome sicuro distribuito con l'applicazione. Visual Studio non firma gli eseguibili dell'applicazione, consente invece di firmare il manifesto dell'applicazione, che fa riferimento al file eseguibile con nome debole. Non è in genere consigliabile firmare i componenti privati dell'applicazione, perché la firma può rendere più difficile la gestione delle dipendenze.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Come firmare un assembly in Visual Studio

Per firmare un'applicazione o un componente, usare la scheda **Firma** della finestra delle proprietà del progetto (fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà** o digitare **proprietà del progetto** nella finestra **Avvio veloce** oppure premere **Alt**+**Invio** nella finestra **Esplora soluzioni**). Selezionare la scheda **Firma**, quindi la casella di controllo **Firma assembly**.

Specificare un file di chiave. Se si sceglie di creare un nuovo file di chiave, tenere presente che i nuovi file di chiave vengono sempre creati in formato *.pfx*. Sono necessari un nome e una password per il nuovo file.

> [!WARNING]
> Proteggere sempre il file di chiave con una password per impedire ad altri di usarlo. È possibile proteggere le chiavi usando provider o archivi certificati.

 È anche possibile fare riferimento a una chiave già creata. Per altre informazioni sulla creazione delle chiavi, vedere [Procedura: Creare una coppia di chiavi pubblica/privata](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

 Se si ha accesso solo a una chiave pubblica, è possibile usare il ritardo della firma per rinviare l'assegnazione della chiave. Per abilitare il ritardo della firma selezionare la casella di controllo **Ritarda firma**. Un progetto con firma ritardata non verrà eseguito e non sarà possibile eseguirne il debug. Tuttavia, è possibile ignorare la verifica durante lo sviluppo usando [Sn.exe (strumento nome sicuro)](/dotnet/framework/tools/sn-exe-strong-name-tool) con l'opzione `-Vr`.

 Per informazioni sulla firma dei manifesti, vedere [Procedura: Firmare manifesti dell'applicazione e di distribuzione](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Vedere anche

- [Assembly con nomi sicuri](/dotnet/framework/app-domains/strong-named-assemblies)
- [Assembly con nome sicuro (firma degli assembly) (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
