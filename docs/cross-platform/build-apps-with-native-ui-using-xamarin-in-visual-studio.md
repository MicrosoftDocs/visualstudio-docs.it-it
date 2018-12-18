---
title: Creare app con interfaccia utente nativa con Xamarin in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: a8602915827c442fa2fc4cbddf4db2a25ef21749
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Creare app con interfaccia utente nativa con Xamarin in Visual Studio

La maggior parte degli sviluppatori che scelgono Xamarin e C# per scrivere applicazioni per dispositivi mobili multipiattaforma usa Xamarin.Forms. Xamarin.Forms definisce un'interfaccia utente che esegue il mapping a controlli nativi in iOS, in Android e nella piattaforma UWP (Universal Windows Platform). Una descrizione di Xamarin.Forms è disponibile nell'articolo [Nozioni di base sulla compilazione di app con Xamarin.Forms in Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

Questo articolo descrive un approccio diverso che prevede l'accesso alle API di interfaccia utente native di ogni piattaforma. L'uso di API native rappresenta un approccio molto più complesso rispetto a Xamarin.Forms, perché richiede una profonda conoscenza di ogni piattaforma. Il vantaggio è rappresentato dalla possibilità di personalizzare l'interfaccia utente in base ai punti di forza e alle funzionalità di ogni piattaforma, condividendo comunque la logica di business sottostante.

Dopo l'esecuzione dei passaggi descritti in [Configurazione e installazione](../cross-platform/setup-and-install.md) e in [Verificare l'ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md), questa procedura dettagliata illustra come compilare un'app Xamarin di base con i livelli dell'interfaccia utente nativa. Con l'interfaccia utente nativa, il codice condiviso si trova in una libreria .NET Standard e i singoli progetti di piattaforma contengono le definizioni dell'interfaccia utente. Ecco l'applicazione che verrà compilata, in esecuzione (da sinistra a destra) in telefoni iOS e Android e sul desktop di Windows 10.
  
[![App Xamarin in iOS, Android e Windows](../cross-platform/media/cross-plat-xamarin-build-1.png "Cross-Plat Xamarin Build 1")](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)
  
Verranno eseguite queste operazioni per la creazione dell'app:  
  
- [Configurare la soluzione](#solution)  
  
- [Scrivere un codice di servizio dati condiviso](#dataservice)  
  
- [Progettare l'interfaccia utente per Android](#Android)  

- [Progettare l'interfaccia utente per Windows](#Windows)  
  
- [Passaggi successivi](#next), che includono la progettazione di un'interfaccia utente iOS
  
> [!TIP]
> È possibile trovare il codice sorgente completo per questo progetto nell'[archivio mobile-samples in GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Se si riscontrano difficoltà o errori, porre le domande su [forums.xamarin.com](http://forums.xamarin.com). Molti errori possono essere risolti con l'aggiornamento agli SDK più recenti richiesti da Xamarin, descritti nelle [note sulla versione di Xamarin](https://developer.xamarin.com/releases/) per ogni piattaforma.    
  
> [!NOTE]
> La documentazione per gli sviluppatori di Xamarin offre inoltre diverse procedure dettagliate con sezioni introduttive e di approfondimento, come indicato di seguito. In tutte queste pagine, per vedere le procedure dettagliate specifiche di Visual Studio, assicurarsi di selezionare "Visual Studio".  
>   
>  -   App Xamarin con interfaccia utente nativa:  
>     -   [Hello, Android](/xamarin/android/get-started/hello-android/) (app semplice con una sola schermata)  
>     -   [Hello, Android Multiscreen](/xamarin/android/get-started/hello-android-multiscreen/) (app con spostamento tra le schermate)  
>     -   [Android Fragments Walkthrough](/xamarin/android/platform/fragments/fragments/implementing-with-fragments/walkthrough/) (usata tra l'altro per le schermate master/dettagli)  
>     -   [Hello, iOS](/xamarin/ios/get-started/hello-iOS/)  
>     -   [Hello, iOS Multiscreen](/xamarin/ios/get-started/hello-iOS-multiscreen/) 

>  -   App Xamarin con Xamarin.Forms (interfaccia utente condivisa)  
>     -   [Hello, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)  
>     -   [Hello, Xamarin.Forms Multiscreen](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)  
  
<a name="solution" />

##  <a name="set-up-your-solution"></a>Configurare la soluzione  

Visual Studio non ha un modello di soluzione per la creazione di applicazioni con interfaccia utente nativa che condividono una libreria .NET Standard. Non è tuttavia difficile creare una soluzione di questo tipo dai progetti singoli. Questi passaggi consentono di creare una soluzione Xamarin con progetti per ogni tipo di piattaforma applicativa e una libreria .NET Standard per il codice condiviso.  
  
1.  In Visual Studio creare una nuova soluzione **Libreria di classi (.NET Standard)** assegnando a questa il nome **WeatherApp**. È possibile trovare molto facilmente questo modello selezionando **Visual C#** a sinistra e quindi **.NET Standard**: 

    ![Creazione della soluzione .NET Standard](../cross-platform/media/cross-plat-xamarin-build-2.png "Build Xamarin multipiattaforma 2")

    Fare clic su OK. La soluzione **WeatherApp** è costituita da un unico progetto denominato **WeatherApp**. 

2.  Se si vuole usare iOS come destinazione, aggiungere un progetto iOS alla soluzione. Fare clic con il pulsante destro del mouse sul nome della soluzione in **Esplora soluzioni** e selezionare **Aggiungi** e **Nuovo progetto**.  Sul lato sinistro della finestra di dialogo **Nuovo progetto** selezionare **Visual C#** e quindi **iOS** e **Universale**. Se non è presente, potrebbe essere necessario installare Xamarin o abilitare la funzionalità di Visual Studio 2017. Vedere [Configurazione e installazione](../cross-platform/setup-and-install.md). Nell'elenco dei modelli selezionare **App visualizzazione singola (iOS)**. Assegnare il nome **WeatherApp.iOS**.

3.  Se si vuole usare Android come destinazione, aggiungere un progetto Android alla soluzione. Sul lato sinistro della finestra di dialogo **Nuovo progetto** selezionare **Visual C#** e quindi **Android**. Nell'elenco dei modelli, selezionare **App vuota (Android)**. Assegnare il nome **WeatherApp.Android**. 

4. Se si vuole usare la piattaforma UWP (Universal Windows Platform) come destinazione, sul lato sinistro della finestra di dialogo **Nuovo progetto** selezionare **Visual C#** e **Universale di Windows**. Nell'elenco dei modelli selezionare **App vuota (Windows universale)** e denominarla **WeatherApp.UWP**.
  
5. Per ogni progetto dell'applicazione (iOS, Android e UWP),fare clic con il pulsante destro del mouse sulla sezione **Riferimenti** in **Esplora soluzioni** e selezionare **Aggiungi riferimento**. Sul lato sinistro della finestra di dialogo **Gestione riferimenti** selezionare **Progetto** e **Soluzione**. Verrà visualizzato un elenco di tutti i progetti nella soluzione, ad eccezione del progetto di cui si stanno gestendo i riferimenti:

   ![Impostazione di un riferimento nel progetto .NET Standard](../cross-platform/media/cross-plat-xamarin-build-3.png "Build Xamarin multipiattaforma 3")

   Selezionare la casella di controllo accanto a **WeatherApp**. 

   Dopo che questa casella di controllo è stata selezionata per ognuno dei progetti dell'applicazione, tutti i progetti contengono riferimenti alla libreria .NET Standard e possono condividere il codice di tale libreria.
  
6. Aggiungere il pacchetto NuGet **Newtonsoft.Json** al progetto .NET Standard. Il pacchetto verrà usato per elaborare le informazioni recuperate da un servizio dati meteo:  
  
    -   Fare clic con il pulsante destro del mouse sul progetto **WeatherApp** in **Esplora soluzioni** e selezionare **Gestisci pacchetti NuGet**.  
  
         Nella finestra di NuGet selezionare la scheda **Sfoglia** e cercare **Newtonsoft**.  
  
    -   Selezionare **Newtonsoft.Json**.  
  
    -   Verificare che il campo **Versione** sia impostato su **Ultima versione stabile** .  
  
    -   Fare clic su **Installa**.  
  
7.  Ripetere il passaggio 7 per trovare e installare il pacchetto **Microsoft.CSharp** nel progetto .NET Standard. Questa libreria è necessaria per usare il tipo di dati `dynamic` C# in una libreria .NET Standard.
  
8.  Compilare la soluzione e verificare che non ci siano errori di compilazione.  
  
<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Scrivere un codice di servizio dati condiviso  

 Il progetto **WeatherApp** è la libreria .NET Standard. È in questo progetto che si scriverà il codice condiviso tra tutte le piattaforme. Poiché ogni progetto dell'applicazione include un riferimento alla libreria .NET Standard, quest'ultima è inclusa nei pacchetti delle applicazioni iOS, Android e UWP.  
  
 Nei passaggi seguenti viene aggiunto codice alla libreria .NET Standard per accedere e archiviare i dati dal servizio meteo:  
  
1.  Prima registrarsi presso il sito Web [ http://openweathermap.org/appid ](http://openweathermap.org/appid) per una chiave API gratuita. Questa chiave API consentirà all'applicazione di ricevere informazioni meteo relative a qualsiasi codice postale degli Stati Uniti. Non funziona per i codici postali al di fuori degli Stati Uniti.
  
2.  Fare clic con il pulsante destro del mouse sul progetto **WeatherApp** e selezionare **Aggiungi > Classe**. Nella finestra di dialogo **Aggiungi nuovo elemento** denominare il file **Weather.cs**. Questa classe verrà usata per archiviare i dati dal servizio di dati meteo.  
  
3.  Sostituire tutto il contenuto di **Weather.cs** con il codice seguente:  
  
    ```csharp  
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```  
  
4.  Aggiungere un'altra classe al progetto .NET Standard denominato **DataService.cs**. Questa classe verrà usata per elaborare dati JSON provenienti dal servizio dati meteo.  
  
5.  Sostituire tutto il contenuto di **DataService.cs** con il codice seguente:  
  
    ```csharp  
    using System.Net.Http;  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
  
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
6.  Aggiungere una terza classe alla libreria .NET Standard denominata **Core.cs**. Questa classe verrà usata per formare una stringa di query con un codice postale, per chiamare il servizio dati meteo e per popolare un'istanza della classe **Weather**.  
  
7.  Sostituire il contenuto di **Core.cs** con il codice seguente:  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR API KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }
  
                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  
  
8. Sostituire la prima occorrenza di *YOUR API KEY HERE* con la chiave API ottenuta nel passaggio 1, che deve comunque essere racchiusa tra virgolette.
  
9. Eliminare il file **MyClass.cs** nella libreria .NET Standard perché non verrà usato.  
  
10. Compilare il progetto **WeatherApp** per verificare che il codice sia corretto.  
  
<a name="Android" />

## <a name="design-ui-for-android"></a>Progettare l'interfaccia utente per Android  

 È ora possibile progettare l'interfaccia utente, connetterla al codice condiviso e quindi eseguire l'app.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Progettare l'aspetto dell'app  
  
1.  In **Esplora soluzioni** espandere la cartella **WeatherApp.Droid > Resources > layout** e aprire **Main.axml**. Questo comando apre il file nella finestra di progettazione visiva. Se viene visualizzato un errore relativo a Java, vedere questo [post di blog](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).  
  
    > [!TIP]
    >  Il progetto include molti altri file che però non verranno esaminati in questo articolo. Per informazioni più dettagliate sulla struttura di un progetto Android, vedere la [parte 2 di approfondimento](/xamarin/android/get-started/hello-android/hello-android-deepdive/) dell'articolo Hello Android in xamarin.com.  
  
2.  Aprire la casella degli strumenti con **Visualizza > Altre finestre > Casella degli strumenti**.  
  
3.  Trascinare un controllo **RelativeLayout**nella finestra di progettazione dalla **Casella degli strumenti** . Usare questo controllo come contenitore padre per altri controlli.  
  
    > [!TIP]
    >  Se in qualsiasi momento sembra che il layout non sia visualizzato correttamente, salvare il file e passare dalla scheda **Progettazione** alla scheda **Origine** e viceversa per aggiornare.  
  
4.  Nella finestra **Proprietà** impostare la proprietà **background** (gruppo Stile) su `#545454`.  Assicurarsi tramite l'intestazione nella finestra **Proprietà** che si stia impostando lo sfondo per **RelativeLayout**.
  
5.  Dalla **Casella degli strumenti**trascinare un controllo **TextView** sul controllo **RelativeLayout** .  
  
6.  Nella finestra **Proprietà** impostare le proprietà riportate di seguito. Può essere utile elencare le voci in ordine alfabetico usando il pulsante di ordinamento sulla barra degli strumenti della finestra Proprietà:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**text**|**Search by Zip Code**|  
    |**ID**|`@+id/ZipCodeSearchLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**textColor**|`@android:color/white`|  
    |**textStyle**|`bold`|  
  
    > [!TIP]
    >  Si noti che molte proprietà non includono un elenco a discesa di valori selezionabili.  Può quindi risultare difficile individuare il valore di stringa da usare per una data proprietà. Per suggerimenti provare a cercare il nome di una proprietà nella pagina della classe [R.attr](http://developer.android.com/reference/android/R.attr.html) .  
    >   
    >  Cercando in Internet viene spesso visualizzata una pagina del sito Web [http://stackoverflow.com/](http://stackoverflow.com/) in cui altri utenti hanno usato la stessa proprietà.  
  
     Per riferimento, se si passa alla visualizzazione **Origine**, dovrebbe apparire il seguente codice per questo elemento:  
  
    ```xml  
    <TextView  
        android:text="Search by Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:id="@+id/ZipCodeSearchLabel"  
        android:layout_marginStart="10dp"  
        android:textColor="@android:color/white"  
        android:textStyle="bold" />  
  
    ```  
  
7.  Dalla **Casella degli strumenti** trascinare un controllo **TextView** sul controllo **RelativeLayout** e posizionarlo sotto il controllo ZipCodeSearchLabel. Rilasciare il nuovo controllo sul bordo appropriato del controllo esistente. Può essere utile eseguire lo zoom avanti nella finestra di progettazione per posizionare il controllo.  
  
8. Nella finestra **Proprietà** impostare queste proprietà:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**testo**|**Zip Code**|  
    |**ID**|`@+id/ZipCodeLabel`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginTop**|`6dp`|  
    |**textColor**|`@android:color/white`|  
  
    Ecco quale deve essere l'aspetto del codice nella visualizzazione **Origine**:  
  
    ```xml  
    <TextView  
        android:text="Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeSearchLabel"  
        android:id="@+id/ZipCodeLabel"  
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"  
        android:textColor="@android:color/white" />  
    ```  
  
9. Dalla **Casella degli strumenti** trascinare un controllo **Number** su **RelativeLayout** e posizionarlo sotto l'etichetta **Zip Code**. Quindi impostare le proprietà seguenti:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**ID**|`@+id/zipCodeEntry`|  
    |**layout_marginStart**|`10dp`|  
    |**layout_marginBottom**|`10dp`|  
    |**width**|`165dp`|  
    |**textColor**|`@android:color/white`|  
  
    Nel controllo **Number** l'utente digiterà un codice postale di cinque cifre degli Stati Uniti. Ecco il markup che corrisponde a tale controllo:  
  
    ```xml  
    <EditText  
        android:inputType="number"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeLabel"  
        android:id="@+id/zipCodeEntry"  
        android:layout_marginStart="10dp"  
        android:layout_marginBottom="10dp"  
        android:width="165dp"  
        android:textColor="@android:color/white" />  
    ```  
  
10. Dalla **Casella degli strumenti** trascinare un **pulsante** sul controllo **RelativeLayout** e posizionarlo a destra del controllo zipCodeEntry. Impostare quindi queste proprietà:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**ID**|`@+id/weatherBtn`|  
    |**testo**|**Get Weather**|  
    |**layout_marginStart**|`20dp`|  
    |**layout_alignBottom**|`@id/zipCodeEntry`|  
    |**width**|`165dp`|  
  
    ```xml  
    <Button
        android:text="Get Weather"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_toRightOf="@id/zipCodeEntry"  
        android:id="@+id/weatherBtn"  
        android:layout_marginStart="20dp"  
        android:layout_alignBottom="@id/zipCodeEntry"  
        android:width="165dp" />  
    ```  
  
11. Si hanno ora nozioni sufficienti per creare un'interfaccia utente di base usando la finestra di progettazione di Android. È anche possibile creare un'interfaccia utente aggiungendo markup direttamente nel file Main.axml della pagina. Per creare la parte restante dell'interfaccia utente in questo modo, passare alla visualizzazione Origine nella finestra di progettazione e quindi incollare il markup seguente *sotto* il tag di fine `</RelativeLayout>`. Questi elementi devono trovarsi sotto il tag perché *non* sono contenuti in `RelativeLayout`.  
  
    ```xml  
    <TextView  
        android:text="Location"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationLabel"  
        android:layout_marginStart="10dp"  
        android:layout_marginTop="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/locationText"  
        android:layout_marginStart="20dp"  
        android:layout_marginBottom="10dp" />  
    <TextView  
        android:text="Temperature"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/tempText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Wind Speed"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/windText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Humidity"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidtyLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/humidityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Visibility"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/visibilityText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunrise"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunriseText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    <TextView  
        android:text="Time of Sunset"  
        android:textAppearance="?android:attr/textAppearanceSmall"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetLabel"  
        android:layout_marginStart="10dp" />  
    <TextView  
        android:textAppearance="?android:attr/textAppearanceMedium"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:id="@+id/sunsetText"  
        android:layout_marginBottom="10dp"  
        android:layout_marginStart="20dp" />  
    ```  
  
12. Salvare il file e passare alla visualizzazione **Progettazione**. L'interfaccia utente dovrebbe essere simile a quella seguente:  
  
     ![Interfaccia utente per app Android](../cross-platform/media/xamarin_androidui.png "Xamarin_AndroidUI")  
  
13. Aprire **MainActivity.cs**. Di seguito è illustrato l'aspetto del codice:  
  
    ```  
    protected override void OnCreate (Bundle bundle)  
    {  
        base.OnCreate (bundle);  
  
        // Set our view from the "main" layout resource  
        SetContentView (Resource.Layout.Main);  
    }  
    ```  
  
14. Compilare il progetto Android per verificare il lavoro. Il processo di compilazione aggiunge gli ID dei controlli al file **Resource.Designer.cs**, in modo che sia possibile fare riferimento ai controlli nel codice in base al nome.  
  
### <a name="consume-your-shared-code"></a>Usare il codice condiviso  
  
1.  Aprire il file **MainActivity.cs** del progetto **WeatherApp** nell'editor di codice e sostituire il contenuto con il codice riportato di seguito. Questo codice chiama il metodo `GetWeather` definito nel codice condiviso, quindi visualizza nell'interfaccia utente dell'app i dati recuperati da tale metodo.  
  
    ```csharp  
    using System;  
    using Android.App;  
    using Android.Widget;  
    using Android.OS;  
  
    namespace WeatherApp.Droid  
    {  
        [Activity(Label = "Sample Weather App", 
                  Theme = "@android:style/Theme.Material.Light", 
                  MainLauncher = true)]  
        public class MainActivity : Activity  
        {  
            protected override void OnCreate(Bundle bundle)  
            {  
                base.OnCreate(bundle);  
  
                SetContentView(Resource.Layout.Main);  
  
                Button button = FindViewById<Button>(Resource.Id.weatherBtn);  
  
                button.Click += Button_Click;  
            }  
  
            private async void Button_Click(object sender, EventArgs e)  
            {  
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);  
  
                if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
                {  
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;  
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;  
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;  
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;  
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;  
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;  
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;  
                }  
            }  
        }  
    }  
    ```  

    Si noti che all'attività è stato assegnato un tema per uno sfondo chiaro.
  
### <a name="run-the-app-and-see-how-it-looks"></a>Eseguire l'app e verificarne l'aspetto  
  
1.  In **Esplora soluzioni** verificare che il progetto **WeatherApp** sia impostato come progetto di avvio.  
  
2.  Selezionare come destinazione un dispositivo o emulatore appropriato, quindi avviare l'app premendo il tasto F5.  

    > [!NOTE]
    > Se Visual Studio indica che il progetto Android non riesce a trovare il file Newtonsoft.Json, aggiungere il pacchetto NuGet corrispondente al progetto Android. 
  
3.  Nel dispositivo o nell'emulatore digitare un codice postale di cinque cifre valido negli Stati Uniti nella casella di modifica e fare clic su **Get Weather** (Ottieni meteo). Nei controlli verranno visualizzati i dati relativi al meteo in tale area.  
  
    [![App Xamarin in Android](../cross-platform/media/cross-plat-xamarin-build-1-android.png "Cross-Plat Xamarin Build 1 Android")](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)  
  
> [!TIP]
>  Il codice sorgente completo per questo progetto si trova nell'[archivio mobile-samples in GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
<a name="Windows" /> 

## <a name="design-ui-for-windows"></a>Progettare l'interfaccia utente per Windows

Il passaggio successivo è la progettazione dell'interfaccia utente per Windows, che verrà connessa al codice condiviso. Verrà quindi eseguita l'app.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Progettare l'aspetto dell'app  

 Il processo di progettazione di un'interfaccia utente nativa per la piattaforma UWP nativa in un'app Xamarin non è diverso rispetto a qualsiasi altra app nativa per la piattaforma UWP. Per questo motivo, in questa sede non verrà descritto l'uso della finestra di progettazione. Per una trattazione dettagliata, vedere [Creazione di un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
 Aprire invece **MainPage.xaml** e sostituire tutto il contenuto XAML con il markup seguente:   
  
```xaml  
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" 
                    VerticalAlignment="Top" 
                    Height="120" Margin="10,40,0,0" Width="400" 
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap" 
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />
            
            <TextBlock Text="Zip Code" TextWrapping="Wrap" 
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            
            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text="" 
                         Margin="10,10,0,0" VerticalAlignment="Top" 
                         InputScope="Number" Width="165" />
                
                <Button x:Name="weatherBtn" Content="Get Weather" 
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60" 
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        
        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>
                
                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>
            
            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />
            
            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```  
  
### <a name="consume-your-shared-code"></a>Usare il codice condiviso  
  
Nel file code-behind **MainPage.xaml.cs** aggiungere il gestore eventi seguente per il pulsante: 
  
```csharp  
private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)  
{  
    if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
    {  
        Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
        locationText.Text = weather.Title;  
        tempText.Text = weather.Temperature;  
        windText.Text = weather.Wind;  
        visibilityText.Text = weather.Visibility;  
        humidityText.Text = weather.Humidity;  
        sunriseText.Text = weather.Sunrise;  
        sunsetText.Text = weather.Sunset;  

        weatherBtn.Content = "Search Again";  
    }  
}  
```  
  
Questo codice chiama il metodo `GetWeather` definito nel codice condiviso, `GetWeather` è lo stesso metodo chiamato nell'app Android. Questo codice consente inoltre di visualizzare i dati recuperati dal metodo nei controlli dell'interfaccia utente dell'app.  
  
### <a name="run-the-app-and-see-how-it-looks"></a>Eseguire l'app e verificarne l'aspetto  
  
1.  In **Esplora soluzioni** impostare il progetto **WeatherApp.UWP** come progetto di avvio.  

2.  Nella casella di riepilogo a discesa **Piattaforme soluzione** selezionare **x86** e **Computer locale** per distribuire l'applicazione al desktop di Windows 10.
  
3.  Premere F5 per avviare l'app.  
  
4.  Digitare un codice postale di cinque cifre degli Stati Uniti valido nella casella di modifica e premere **Get Weather** (Ottieni meteo). Nella pagina verranno visualizzati i dati relativi al meteo nell'area corrispondente.  

    [![App Xamarin nella piattaforma UWP](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png "Cross-Plat Xamarin Build 1 UWP")](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)  

> [!TIP]
>  Il codice sorgente completo per questo progetto si trova nell'[archivio mobile-samples in GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  

<a name="next" /> 

## <a name="next-steps"></a>Passaggi successivi  

 **Aggiungere l'interfaccia utente per iOS alla soluzione**  
  
 È possibile estendere questo esempio aggiungendo l'interfaccia utente nativa per iOS. Per testare il codice in iOS, è necessario connettersi a un computer Mac nella rete locale in cui siano installati Xcode e Xamarin. Dopo aver eseguito questa operazione, è possibile usare la finestra di progettazione iOS direttamente in Visual Studio. Per l'app completa, vedere l'[archivio mobile-samples in GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
 Vedere anche la procedura dettagliata [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin).   
  
 **Aggiungere codice specifico della piattaforma in un progetto condiviso**  
  
 Il codice condiviso in una libreria .NET Standard è indipendente dalla piattaforma. La libreria viene compilata una sola volta e viene inclusa nel pacchetto dell'app specifico di ogni piattaforma. Per scrivere codice condiviso che usa la compilazione condizionale per isolare il codice specifico della piattaforma, è possibile usare un progetto *condiviso*. Per altre informazioni, vedere [Opzioni di condivisione del codice](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies).  
  
## <a name="see-also"></a>Vedere anche  

 [Documentazione di Xamarin](http://docs.microsoft.com/xamarin)   
 [Windows Dev Center](https://dev.windows.com/en-us)   
 [Poster di riferimento rapido Swift e C#](http://aka.ms/scposter)