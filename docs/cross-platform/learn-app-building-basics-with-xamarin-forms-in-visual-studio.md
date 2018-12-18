---
title: Nozioni di base sulla compilazione di app con Xamarin.Forms in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 608eebc113c9df7a8978299cc69907e28d81a16f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Nozioni di base sulla compilazione di app con Xamarin.Forms in Visual Studio

Dopo aver eseguito i passaggi in [Configurazione e installazione](../cross-platform/setup-and-install.md) e in [Verificare l'ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md), questa procedura dettagliata illustra come compilare un'app di base con Xamarin.Forms. Con Xamarin.Forms, tutto il codice dell'interfaccia utente viene scritto una sola volta in una libreria di classi .NET Standard. Xamarin esegue quindi il rendering automatico dei controlli dell'interfaccia utente nativi per le piattaforme iOS, Android e UWP. 

Per il codice comune, è in genere preferibile usare una libreria .NET Standard anziché un progetto condiviso. La libreria .NET Standard include le API .NET che possono essere eseguite in tutte le piattaforme di destinazione.  

Ecco l'applicazione che verrà compilata, eseguita (da sinistra a destra) in telefoni iOS e Android e nella piattaforma UWP (Universal Windows) di Windows 10:
  
[![Applicazione di esempio Weather App in iOS, Android e UWP](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)
  
Per compilare l'applicazione verranno eseguiti questi passaggi:  
  
-   [Configurare la soluzione](#solution)  
  
-   [Scrivere un codice di servizio dati condiviso](#dataservice)  
  
-   [Iniziare a scrivere il codice dell'interfaccia utente condiviso](#uicode)  
  
-   [Testare l'app usando Visual Studio Emulator for Android](#test)  
  
-   [Terminare l'interfaccia utente con un aspetto nativo tra le piattaforme](#finish)  
  
> [!TIP]
> È possibile trovare il codice sorgente completo per questo progetto nella finestra di [archivio degli esempi di Xamarin-Forms in GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
<a name="solution" />

## <a name="set-up-your-solution"></a>Configurare la soluzione  

Questi passaggi consentono di creare una soluzione Xamarin.Forms che contiene una libreria di classi .NET Standard per il codice condiviso e due pacchetti NuGet aggiunti. 
  
1. In Visual Studio creare una nuova soluzione **App multipiattaforma (Xamarin.Forms)** e denominarla **WeatherApp**. Cercare il modello selezionando **Visual C#** e **Multipiattaforma** nell'elenco a sinistra.  
    
    ![Creazione di un nuovo progetto di app Xamarin.Forms multipiattaforma](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

    Se il modello non è presente, può essere necessario installare Xamarin o abilitare la funzionalità di Visual Studio 2017. Vedere [Configurazione e installazione](../cross-platform/setup-and-install.md).  

2.  Dopo aver fatto clic su OK sarà possibile selezionare alcune opzioni. Scegliere **App vuota** e **.NET Standard**:

    ![Creazione di un nuovo progetto App multipiattaforma](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Fare clic su OK per creare la soluzione. Verrà visualizzata una soluzione con quattro progetti:  
  
    -   **WeatherApp**: la libreria .NET Standard in cui verrà scritto il codice condiviso tra le piattaforme, inclusa la logica di business comune e il codice dell'interfaccia utente con Xamarin.Forms.  
  
    -   **WeatherApp.Android**: il progetto che contiene il codice Android nativo.  
  
    -   **WeatherApp.iOS**: il progetto che contiene il codice iOS nativo.  
  
    -   **WeatherApp.UWP**: progetto che contiene il codice UWP di Windows 10.  
  
    > [!NOTE]
    >  È possibile eliminare qualsiasi progetto presente in piattaforme a cui non si fa riferimento.   
  
     In ogni progetto nativo è possibile accedere alla finestra di progettazione nativa per la piattaforma corrispondente e implementare schermate e funzionalità specifiche della piattaforma secondo necessità.  
  
4.  Aggiornare il pacchetto NuGet di Xamarin.Forms nella soluzione alla versione stabile più recente come descritto di seguito:  
  
    -   Selezionare **Strumenti > Gestione pacchetti NuGet > Gestisci pacchetti NuGet per la soluzione**.  
  
    -   Nella scheda **Aggiornamenti** selezionare il pacchetto **Xamarin.Forms** e selezionare l'aggiornamento di tutti i progetti nella soluzione. Non selezionare gli aggiornamenti per le raccolte di supporto di Xamarin Android.  
  
    -   Aggiornare il campo **Versione** all' **Ultima versione stabile** disponibile.  
  
    -   Fare clic su **Installa**.  
  
         ![Aggiornamento del pacchetto NuGet di Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  

    È necessario prendere l'abitudine di aggiornare la versione di Xamarin.Forms ogni volta che si crea una nuova soluzione Xamarin.Forms. Non aggiornare alcuna libreria di supporto per Android. Se necessario, queste librerie vengono aggiornate quando si aggiorna la versione di Xamarin.Forms.
  
5.  Aggiungere il pacchetto NuGet **Newtonsoft.Json** al progetto **WeatherApp**. Questa libreria viene usata per elaborare le informazioni recuperate da un servizio dati meteo:  
  
    -   In Gestione pacchetti NuGet (aperto dal passaggio 4) selezionare la scheda **Sfoglia** e cercare **Newtonsoft**.  
  
    -   Selezionare **Newtonsoft.Json**.  
  
    -   Selezionare il progetto **WeatherApp**, l'unico progetto in cui è necessario installare il pacchetto.  
  
    -   Verificare che il campo **Versione** sia impostato su **Ultima versione stabile** .  
  
    -   Fare clic su **Installa**.  
  
    ![Individuare e installare il pacchetto NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Ripetere il passaggio 5 per trovare e installare il pacchetto **Microsoft.CSharp** nel progetto .NET Standard. Questa libreria è necessaria per usare il tipo di dati `dynamic` C# in una libreria .NET Standard.
  
7.  Compilare la soluzione e verificare che non ci siano errori di compilazione.  
  
<a name="dataservice" /> 

## <a name="write-shared-data-service-code"></a>Scrivere un codice di servizio dati condiviso  

All'interno del progetto di libreria .NET Standard **WeatherApp** verrà scritto codice condiviso da tutte le piattaforme. A questa libreria fanno riferimento i pacchetti dell'app compilati dai progetti iOS, Android e Windows.  
  
Per eseguire questo esempio, è prima di tutto necessario iscriversi per una chiave API gratuita all'indirizzo [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
Nei passaggi seguenti viene aggiunto codice alla libreria .NET Standard per accedere e archiviare i dati dal servizio meteo:  
  
1.  Fare clic con il pulsante destro del mouse sul progetto **WeatherApp** e selezionare **Aggiungi > Classe**. Nella finestra di dialogo **Aggiungi nuovo elemento** denominare il file **Weather.cs**. Questa classe verrà usata per archiviare i dati dal servizio di dati meteo.  
  
2.  Sostituire tutto il contenuto di **Weather.cs** con il codice seguente:  
  
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
  
3.  Aggiungere un'altra classe al progetto **WeatherApp** denominato **DataService.cs** che verrà usato per elaborare i dati JSON dal servizio di dati meteo.  
  
4.  Sostituire tutto il contenuto di **DataService.cs** con il codice seguente:  
  
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
  
5.  Aggiungere una terza classe al progetto **WeatherApp** denominato **Core.cs** in cui verrà inserita la logica di business condivisa. Questo codice forma una stringa di query con il codice postale, chiama il servizio dati meteo e popola un'istanza della classe `Weather`.  
  
6.  Sostituire il contenuto di **Core.cs** con il codice seguente:  
  
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
  
                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);  
  
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

7. Sostituire *YOUR API KEY HERE* con la chiave API ottenuta, che deve comunque essere racchiusa tra virgolette.     
  
8.  Compilare il progetto di libreria **WeatherApp** per verificare che il codice sia corretto.  
  
 <a name="uicode" /> 

## <a name="begin-writing-shared-ui-code"></a>Iniziare a scrivere il codice dell'interfaccia utente condiviso  

Xamarin.Forms consente di implementare codice dell'interfaccia utente condiviso nella libreria .NET Standard. In questa procedura si aggiungerà al progetto una pagina con un pulsante. Il pulsante aggiorna il testo della pagina con i dati restituiti dal servizio meteo illustrato nella sezione precedente:  
  
1.  Aggiungere una **Pagina contenuto** denominata **WeatherPage** facendo clic con il pulsante destro del mouse sul progetto **WeatherApp** e scegliendo **Aggiungi > Nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Pagina contenuto**. Prestare attenzione a non selezionare **Pagina contenuto (C#)** o **Visualizzazione contenuto**. Assegnare il nome **WeatherPage.xaml**.  
  
    ![Aggiunta di una nuova pagina XAML Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Xamarin.Forms è basato su XAML, quindi questo passaggio crea un file **WeatherPage.xaml** e un file code-behind annidato **WeatherPage.xaml.cs**. È possibile scrivere logica dell'interfaccia utente in XAML o nel codice. In questa procedura dettagliata verranno eseguite operazioni relative a entrambi i casi.  
  
2.  Per aggiungere un pulsante alla schermata **WeatherPage**, sostituire il contenuto di **WeatherPage.xaml** con il markup seguente:  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">  
      <Button x:Name="getWeatherBtn" 
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />  
    </ContentPage>  
    ```  
  
     Il nome del pulsante deve essere definito usando l'attributo `x:Name`, in modo che si possa fare riferimento al pulsante tramite il nome all'interno del file code-behind.  
  
3.  Per aggiungere un gestore eventi per l'evento `Clicked` del pulsante e aggiornarne il testo del pulsante stesso, sostituire il contenuto di **WeatherPage.xaml.cs** con il codice seguente. Il codice postale "60601" può essere liberamente sostituito da un altro codice.  
  
    ```csharp  
    using System;  
    using Xamarin.Forms;  
  
    namespace WeatherApp  
    {  
        public partial class WeatherPage: ContentPage  
        {  
            public WeatherPage()  
            {  
                InitializeComponent();  
  
                //Set the default binding to a default object for now  
                BindingContext = new Weather();  
            }  
  
            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
            {  
                Weather weather = await Core.GetWeather("60601");  
                getWeatherBtn.Text = weather.Title;  
            }  
        }  
    }  
    ```  
  
4.  Per aprire **WeatherPage** come prima schermata all'avvio dell'app, sostituire il costruttore predefinito in **App.xaml.cs** con il codice seguente:  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Compilare il progetto **WeatherApp** per verificare che il codice sia corretto.  
  
<a name="test" /> 

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a>Testare l'app usando Visual Studio Emulator for Android  

È ora possibile eseguire l'app. Eseguire prima solo la versione Android per verificare che l'app stia ottenendo i dati dal servizio meteo. In un secondo momento verranno eseguite anche le versioni iOS e UWP dopo aver aggiunto altri elementi di interfaccia utente.   
  
1.  Impostare il progetto **WeatherApp.Android** come progetto di avvio facendo clic con il pulsante destro del mouse su di esso e scegliendo **Imposta come progetto di avvio**.  
  
2.  Nella barra degli strumenti di Visual Studio viene visualizzato **WeatherApp.Android** come progetto di destinazione. Selezionare uno degli emulatori di Android per il debug e premere **F5**. Si consiglia di usare una delle opzioni dell'emulatore di **Visual Studio**, che eseguirà l'app in Visual Studio Emulator for Android.  
  
    ![Selezione di una destinazione di debug Emulatore Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

    > [!NOTE]
    > Se Visual Studio indica che il progetto Android non riesce a trovare il file Newtonsoft.Json, aggiungere il pacchetto NuGet corrispondente al progetto Android.   
  
3.  Quando l'app viene avviata nell'emulatore, fare clic sul pulsante **Get Weather** . Il testo del pulsante verrà aggiornato in **Chicago**, che è la proprietà `Title` dei dati recuperati dal servizio meteo.  
  
     ![App Meteo prima e dopo un tocco sul pulsante](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  

<a name="finish" /> 

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a>Terminare l'interfaccia utente con un aspetto nativo tra le piattaforme  

Xamarin.Forms esegue il rendering dei controlli dell'interfaccia utente nativi per ciascuna piattaforma, in modo da conferire un aspetto nativo all'app. È possibile visualizzare più chiaramente questo aspetto nativo completando l'interfaccia utente con l'aggiunta di un campo di input per un codice postale e di controlli per visualizzare i dati meteo.  
  
1.  Sostituire il contenuto di **WeatherPage.xaml** con il markup qui sotto. È possibile fare riferimento dal codice agli elementi denominati con l'attributo `x:Name`, come descritto in precedenza. Xamarin.Forms offre anche alcune [opzioni di layout](/xamarin/xamarin-forms/controls/layouts/). Qui WeatherPage usa [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) e [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/).  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
            
                <Label Text="Search by Zip Code" 
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />
            
                <Label x:Name="zipCodeLabel" Text="Zip Code:" 
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />
            
                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />
            
                <Button x:Name="getWeatherBtn" Text="Get Weather" 
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>  
     ```  
  
     Anche se non è incluso in questo esempio, è possibile usare il tag `OnPlatform` all'interno di file XAML per selezionare un valore della proprietà specifico per la piattaforma corrente in cui l'app è in esecuzione. Vedere [Sintassi XAML essenziale](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax/). Nel file code-behind è possibile determinare in quale piattaforma l'applicazione è in esecuzione confrontando la proprietà [`Device.RuntimePlatform`](https://developer.xamarin.com/api/property/Xamarin.Forms.Device.RuntimePlatform/) con le costanti definite nella classe [`Device`](https://developer.xamarin.com/api/type/Xamarin.Forms.Device/) denominate [`Device.iOS`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.iOS/), [`Device.Android`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.Android/) e [`Device.UWP`](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.UWP/).  
  
2.  In **WeatherPage.xaml.cs**sostituire il gestore eventi `GetWeatherBtn_Clicked` con il codice qui sotto. Questo codice verifica che sia presente un codice postale nel campo di immissione e recupera i dati relativi a tale codice. Imposta quindi il contesto di associazione dell'intera pagina sull'istanza di `Weather` risultante. Il codice termina impostando il testo del pulsante su "Search Again" (Cerca di nuovo). Ogni etichetta nell'interfaccia utente è associata a una proprietà della classe `Weather`. Quando si imposta il contesto di associazione della schermata su un'istanza di `Weather`, le etichette vengono aggiornate automaticamente.  
  
    ```csharp  
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            BindingContext = weather;  
            getWeatherBtn.Text = "Search Again";  
        }  
    }  
    ```  
  
3.  Eseguire l'app in tutte e tre le piattaforme facendo clic con il pulsante destro del mouse sul progetto appropriato, selezionando **Imposta come progetto di avvio** e avviando l'app in un dispositivo o in un emulatore. Immettere un codice postale di cinque cifre degli Stati Uniti valido e premere il pulsante **Get Weather** (Ottieni meteo) per visualizzare i dati meteo per l'area. Visual Studio deve essere connesso a un computer Mac nella rete per il progetto iOS.  
  
     [![Applicazione di esempio Weather App in iOS, Android e UWP](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)
  
Il codice sorgente completo per questo progetto si trova in [archivio degli esempi di Xamarin-Forms in GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).