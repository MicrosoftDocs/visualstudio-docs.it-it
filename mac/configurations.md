---
title: Informazioni sulle configurazioni della build
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: e435418c0c77f1577e9db8ab35d76d6bd54f8447
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="understanding-build-configurations"></a>Informazioni sulle configurazioni della build

## <a name="project-build-configurations"></a>Configurazioni della build di progetti 

I progetti possono avere più configurazioni. Passare da una configurazione a un'altra consente di ottenere output diversi in fase di compilazione. Se si usa una configurazione di debug, ad esempio, l'output includerà simboli di debug che consentono al debugger di risolvere i nomi delle funzioni, dei parametri o delle variabili dall'analisi dello stack di un'applicazione bloccata. L'uso di una configurazione di debug, tuttavia, fa aumentare eccessivamente le dimensioni dei file e di conseguenza non è ideale per le applicazioni destinate alla distribuzione.

Ogni piattaforma deve avere una configurazione della build specifica. Lo sviluppo Xamarin.Android ha sempre una sola configurazione, di versione o di debug. Xamarin.iOS ha più configurazioni. I progetti per iOS più recenti hanno solo configurazioni di debug o di versione, che però possono essere impostate per un dispositivo o per un qualsiasi simulatore installato.

## <a name="solution-configurations"></a>Configurazioni di soluzioni

Analogamente alle configurazioni di progetti, le configurazioni di soluzioni vengono usate per creare configurazioni personalizzate per un intero progetto. Tramite la scheda **Mapping di configurazione** in **Compilazione > Configurazioni** è possibile assegnare una configurazione di destinazione per ogni elemento della soluzione, come illustrato di seguito:


 ![Opzioni di Mapping di configurazione](media/projects-and-solutions-image3.png)

Per altre informazioni, vedere il video di James Montemagno su [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg).

## <a name="run-configuration"></a>Configurazione dell'esecuzione

Nelle versioni precedenti di Xamarin Studio era disponibile un'opzione per impostare un progetto come **progetto di avvio**, ovvero come progetto da eseguire o di cui eseguire il debug quando veniva usato il comando di esecuzione/debug globale. Il progetto di avvio era contrassegnato dal nome in grassetto nel riquadro dei progetti.

In Visual Studio per Mac, anziché impostare un progetto di avvio, è possibile impostare una _configurazione di esecuzione_. Le configurazioni di esecuzione sono disponibili in un elenco a discesa sulla barra degli strumenti accanto al selettore della configurazione della build, come illustrato di seguito:

 ![Elenco a discesa della configurazione di esecuzione](media/projects-and-solutions-image8.png)

Una configurazione di esecuzione è un set di opzioni di esecuzione con un nome. Per un progetto possono essere definite diverse configurazioni per scopi diversi. Le configurazioni di esecuzione sono definite a livello di progetto. Per ogni progetto eseguibile viene creata automaticamente una configurazione predefinita, anche se è possibile aggiungerne un numero illimitato. Alcuni tipi di progetto generano automaticamente altre configurazioni di esecuzione. Ad esempio, i progetti watchOS possono generare _configurazioni per Glances e notifiche_. 
 
Le configurazioni possono essere condivise con altri sviluppatori, nel qual caso vengono archiviate nel file con estensione csproj, o mantenute in locale, nel qual caso vengono archiviate in un file con estensione user.

### <a name="android-run-configurations"></a>Configurazioni di esecuzione Android
 
Le configurazioni di esecuzione per i progetti Android consentono di specificare quale ricevitore di attività, servizi o trasmissioni avviare per l'esecuzione o il debug del progetto. Per poter testare i componenti in diverse condizioni di avvio, è possibile passare dati di intent aggiuntivi e impostare flag di intent.

Alle attività diverse da `MainLauncher` è necessario aggiungere `Exported=true` all'attributo Activity per il debug su un dispositivo fisico o definire filtri di intent.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Esempi di dati che possono essere inclusi nelle configurazioni di esecuzione

L'elenco seguente offre alcuni esempi di dati che possono essere inclusi nelle configurazioni di esecuzione:

* Progetto .NET normale
    * App di avvio alternativa
    * Argomenti di avvio
    * Directory di lavoro
    * Variabili di ambiente
    * Opzioni di runtime di Mono (da usare solo se in esecuzione in Mono)
* Progetto Android
    * Punto di ingresso (attività, servizio, ricevitore)
    * Argomenti e dati di intent
* Progetto iOS
    * Modalità (normale, recupero in background)
* Progetto di estensione iOS
    * App di avvio: predefinita o personalizzata
* Progetto WatchKit
    * Modalità (Glance, notifica)
    * Payload di notifica
