---
title: Strumento di acquisizione da riga di comando | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 68ea5a718b1a0d1ccff7155f842bc3808d640c21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="command-line-capture-tool"></a>Strumento di acquisizione da riga di comando
DXCap.exe è uno strumento da riga di comando per l'acquisizione e la riproduzione della diagnostica della grafica. Supporta Direct3D dalla versione 10 alla 12 per tutti i livelli di funzionalità.  
  
## <a name="syntax"></a>Sintassi  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe -p [filename] -screenshot [-frame frames]  
DXCap.exe -p [filename] -toXML [xml_filename]  
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe -info  
```  
  
#### <a name="parameters"></a>Parametri  
 `-file` `filename`  
 In modalità di acquisizione (`-c`), `filename` specifica il nome del file di log di grafica che le informazioni grafiche vengono registrate in. Se `filename` non viene specificato, informazioni grafiche vengono registrate in un file denominato `<appname>-<date>-<time>.vsglog` per impostazione predefinita.  
  
 In modalità di convalida (-v), `filename` specifica il nome del file di log di grafica da convalidare. Se `filename` non viene specificato, viene usato di nuovo il log di grafica dell'ultima convalida.  
  
 `-frame` `frames`  
 In modalità di acquisizione, `frames` specifica i frame da acquisire. Il primo frame è 1. È possibile specificare più frame usando virgole e intervalli. Ad esempio, se `frames` è `2, 5, 7-9, 15`, i frame `2`, `5`, `7`, `8`, `9`, e `15` vengono acquisiti.  
  
 `-period` `periods`  
 In modalità di acquisizione, `periods` specifica gli intervalli di tempo, espressi in secondi, durante i quali acquisire i frame. È possibile specificare più periodi usando virgole e intervalli. Ad esempio se `periods` è `2.1-5, 7.0-9.3`, i frame che eseguono il rendering tra `2.1` e `5` secondi tra`7` e `9.3` vengono acquisiti i secondi.  
  
 `-manual`  
 In modalità di acquisizione, `-manual` specifica che i frame verranno acquisiti manualmente premendo il tasto STAMP. È possibile acquisire i frame all'avvio dell'app. Per interrompere l'acquisizione dei frame, tornare all'interfaccia della riga di comando e premere INVIO.  
  
 `-c` `app` [`args...`]  
 Modalità di acquisizione. In modalità di acquisizione, `app` specifica il nome dell'app da cui acquisire le informazioni grafiche; `args...` specifica ulteriori parametri della riga di comando per tale app.  
  
 `-p` [`filename`]  
 Modalità di riproduzione (`-p`). In modalità di riproduzione, `filename` specifica il nome del file di log di grafica da riprodurre. Se `filename` non viene specificato, viene usato di nuovo il log di grafica dell'ultima riproduzione.  
  
 `-debug`  
 In modalità di riproduzione, `-debug` specifica che la riproduzione deve essere eseguita con il livello di debug Direct3D abilitato.  
  
 `-warp`  
 In modalità di riproduzione, `-warp` specifica che la riproduzione deve essere eseguita mediante il programma di rendering software WARP.  
  
 `-hw`  
 In modalità di riproduzione, `-hw` specifica che la riproduzione deve essere eseguita mediante hardware della GPU.  
  
 `-config`  
 In modalità di riproduzione, `-config` Visualizza le informazioni relative al computer che è stato usato per acquisire il file di log di grafica, se queste informazioni è state registrate nel registro.  
  
 `-rawmode`  
 In modalità di riproduzione, `-rawmode` specifica che la riproduzione deve essere eseguita senza alcuna modifica per gli eventi registrati. Durante il normale funzionamento, la modalità di riproduzione potrebbe apportare piccole modifiche alla riproduzione per semplificare il debug e velocizzare la riproduzione. Ad esempio, potrebbe simulare l'output della catena di scambio, anziché l'esecuzione dei comandi della catena di scambio. In genere questo non è un problema, ma potrebbe essere necessario che la riproduzione avvenga in modo più fedele agli eventi registrati. È possibile ad esempio usare questa opzione per ripristinare il comportamento di rendering a schermo intero in un'app acquisita durante l'esecuzione in modalità a schermo intero.  
  
 `-toXML` [`xml_filename`]  
 In modalità di riproduzione, `xml_filename` specifica il nome del file in cui viene scritta una rappresentazione XML della riproduzione. Se `xml_filename` non viene specificato, la rappresentazione XML viene scritta in un file denominato come il file da riprodurre, ma con l'estensione `.xml`.  
  
 `-v`  
 Modalità di convalida. In modalità di convalida, i frame acquisiti vengono riprodotti sia su dispositivi hardware che WARP e i relativi risultati vengono confrontati mediante una funzione di confronto immagini. È possibile usare questa funzionalità per identificare rapidamente i problemi di driver che interessano il rendering.  
  
 `-examine` `events`  
 In modalità di convalida, `events` specifica il set di eventi grafici di cui vengono confrontati i risultati immediati. Ad esempio, `-examine present,draw,copy,clear` limita il confronto solo gli eventi appartenenti a tali categorie.  
  
> [!TIP]
>  È consigliabile iniziare con `-examine present,draw,copy,clear` perché questo sarà rivelare la maggior parte dei problemi ma molto meno tempo rispetto a un set più completo di eventi. Se necessario, è possibile specificare un set di eventi diverso o più grande per convalidare tali eventi e rivelare altri tipi di problemi.  
  
 `-haltonfail`  
 In modalità di convalida, `-haltonfail` interrompe la convalida quando vengono rilevate differenze tra il renderer hardware e WARP. Per riprendere la convalida, premere un tasto.  
  
 `-exitonfail`  
 In modalità di convalida, `-exitonfail` esce immediatamente quando vengono rilevate differenze tra il renderer hardware e WARP dalla convalida. Al termine del programma in questo modo, viene restituito `0` per l'ambiente; in caso contrario restituisce `1`.  
  
 `-showprogress`  
 In modalità di convalida, `-showprogress` Visualizza informazioni sullo stato relative alla sessione di convalida. Lo stato WARP viene visualizzato a sinistra; lo stato hardware viene visualizzato a destra.  
  
 `-e` `search_string`  
 Enumera le app UWP installati. È possibile utilizzare queste informazioni per eseguire acquisizioni della riga di comando con le app UWP.  
  
 `-info`  
 Visualizza le informazioni sul computer e sulle DLL di acquisizione.  
  
## <a name="remarks"></a>Note  
 DXCap.exe funziona in tre modalità:  
  
 Modalità di acquisizione (-c)  
 Consente di acquisire le informazioni grafiche da un'app in esecuzione e le registra in un file di log di grafica. Le funzionalità di acquisizione e il formato di file sono identici a quelli di Visual Studio.  
  
 Modalità di riproduzione (-p)  
 Consente di riprodurre gli eventi grafici acquisiti in precedenza da un file di log di grafica esistente. Per impostazione predefinita, la riproduzione avviene in una finestra, anche quando il file di log di grafica è stato acquisito da un'app a schermo intero. La riproduzione viene eseguita a schermo intero solo quando la log di grafica file è stato acquisito da un'app a schermo intero e `-rawmode` è specificato.  
  
 Modalità di convalida (`-v`)  
 Convalida il comportamento di rendering riproducendo i frame acquisiti, sia su dispositivi hardware che WARP, quindi confrontando i risultati con una funzione di confronto immagini. È possibile usare questa funzionalità per identificare rapidamente i problemi di driver che interessano il rendering.  
  
 Oltre a queste modalità, dxcap.exe esegue altre due funzioni che non eseguono l'acquisizione o la riproduzione di informazioni grafiche.  
  
 Funzione di enumerazione (`-e`)  
 Visualizza i dettagli sulle App UWP che vengono installati nel computer. Questi dettagli includono il nome del pacchetto e appid che identificano il file eseguibile in un'app UWP. Per acquisire informazioni grafiche da un'app di Windows Store con DXCap.exe, usare il nome del pacchetto e l'ID app anziché il nome del file eseguibile usato durante l'acquisizione di un'app desktop.  
  
 Informazioni sulla funzione (`-info)`  
 Visualizza i dettagli sul computer e sulle DLL di acquisizione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Acquisizione di informazioni grafiche da un'app desktop  
 Utilizzare `-c` per specificare l'app da cui si desidera acquisire informazioni grafiche.  
  
```ms-dos  
DXCap.exe -c BasicHLSL11.exe  
```  
  
 Per impostazione predefinita, informazioni grafiche vengono registrate in un file denominato `<appname>-<date>-<time>.vsglog`. Utilizzare `-file` per specificare un altro file da registrare.  
  
```ms-dos  
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe  
```  
  
 Specificare ulteriori parametri della riga di comando per l'app da cui si esegue l'acquisizione includendoli dopo il nome file dell'app.  
  
```ms-dos  
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Il comando nell'esempio precedente acquisisce informazioni grafiche della versione desktop di Internet Explorer durante la visualizzazione di pagina Web all'indirizzo www.fishgl.com che usa l'API WebGL per il rendering del contenuto 3D.  
  
> [!NOTE]
>  Poiché gli argomenti della riga di comando inseriti dopo l'app vengono passati al metodo, è necessario specificare gli argomenti per DXCap.exe prima di utilizzare il `-c` opzione.  
  
### <a name="capture-graphics-information-from-a-uwp-app"></a>Acquisire informazioni grafiche da un'app UWP.  
 È possibile acquisire informazioni grafiche da un'app UWP.  
  
```ms-dos  
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Con DXCap.exe per l'acquisizione da un'app UWP è simile a quello per l'acquisizione da un'applicazione desktop di Windows, ma invece identifica un'applicazione desktop mediante il nome del file, si identifica un'app UWP per il nome del pacchetto e il nome o ID dell'eseguibile contenuto nel pacchetto che si desidera  acquisire. Per rendere più semplice scoprire come identificare le app UWP che vengono installate nel computer, utilizzare il `-e` opzione con DXCap.exe per enumerarle:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 È possibile fornire una stringa di ricerca facoltativa per trovare l'app che si sta cercando. Quando viene fornita la stringa di ricerca, DXCap.exe enumera le app UWP il cui nome del pacchetto, nome dell'applicazione o ID dell'app corrispondano alla stringa di ricerca. La ricerca non fa distinzione tra maiuscole e minuscole.  
  
```ms-dos  
DXCap.exe -e map  
```  
  
 Il comando precedente enumera le app UWP che corrispondono a "map" di seguito è riportato l'output:  
  
 **Pacchetto "Microsoft.BingMaps":**  
 **InstallDirectory: C:\Programmi\Microsoft Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName: Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Nome: Microsoft.BingMaps**  
 **Server di pubblicazione: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US**  
 **Versione: 2.1.2914.1734**  
 **Applicazioni offline:**  
 **ID: AppexMaps**  
 **File exe: C:\Programmi\Microsoft Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: No**  
 * * AppSpec (per avviare): **DXCap.exe - c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps*** l'ultima riga di output per ogni app enumerata Visualizza il comando è possibile utilizzare per acquisire informazioni grafiche da esso.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Acquisizione di frame specifici o frame tra intervalli di tempo specifici  
 Utilizzare `-frame` per specificare i frame da acquisire con virgole e intervalli:  
  
```ms-dos  
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe  
```  
  
 In alternativa, utilizzare `-period` per specificare un set di intervalli di tempo durante i quali acquisire i frame. Gli intervalli di tempo vengono specificati in secondi ed è possibile indicare più intervalli:  
  
```ms-dos  
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Acquisizione di frame in modo interattivo  
 Utilizzare `-manual` per acquisire i frame in modo interattivo. Premere INVIO per avviare l'acquisizione e premere di nuovo INVIO per interromperla.  
  
```ms-dos  
DXCap.exe -manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Riproduzione di un file di log di grafica  
 Utilizzare `-p` per riprodurre un file di log di grafica acquisito in precedenza.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog  
```  
  
 Omettere il nome del file per riprodurre il log di grafica acquisito più di recente.  
  
```ms-dos  
DXCap.exe -p  
```  
  
### <a name="play-back-in-raw-mode"></a>Riproduzione in modalità raw  
 Utilizzare `-rawmode` per riprodurre i comandi acquisiti esattamente come si sono verificate. Nella riproduzione normale, alcuni comandi vengono emulati, ad esempio un file di log di grafica acquisito da un'app a schermo intero verrà riprodotto in una finestra. Se invece è abilitata la modalità raw, lo stesso file verrà riprodotto a schermo intero.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Riproduzione con dispositivo WARP o hardware  
 Potrebbe essere necessario forzare la riproduzione di un file di log di grafica acquisito su un dispositivo hardware all'uso di WARP o forzare la riproduzione di un log acquisito su WARP all'uso di un dispositivo hardware. Utilizzare `-warp` per eseguire la riproduzione con WARP.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -warp  
```  
  
 Utilizzare `-hw` per eseguire la riproduzione con hardware.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Convalida di un file di log di grafica per un dispositivo WARP  
 In modalità di convalida, il file di log di grafica viene riprodotto sia su dispositivo hardware che WARP confrontando i relativi risultati. Ciò consente di identificare gli errori di rendering causati dal driver. Utilizzare - v per convalidare il comportamento corretto dei componenti hardware grafici per un dispositivo WARP.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Per ridurre la quantità di confronti, è possibile specificare un subset di comandi per la convalida da confrontare e gli altri comandi verranno ignorati. Utilizzare - examine per specificare i comandi di cui si desidera confrontare i risultati.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Conversione di un file di log di grafica in formato PNG  
 Per visualizzare o analizzare i frame da un file di log di grafica, DXCap.exe può salvare i frame acquisiti come file di immagine con estensione PNG (Portable Network Graphics). Utilizzare `-screenshot` per in modalità di riproduzione per restituire i frame acquisiti come file con estensione png.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Utilizzare `-frame` con `-screenshot` per specificare i frame che si desidera restituire.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Conversione di un file di log di grafica in formato XML  
 Per elaborare e analizzare i log di grafica usando strumenti familiari come FindStr o XSLT, DXCap.exe può convertire un file di log di grafica in formato XML. Utilizzare `-toXML` in modalità di riproduzione per convertire il log in formato XML anziché riprodurlo eseguire il backup.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -toXML  
```  
  
 Per impostazione predefinita, l'output XML viene scritto in un file con lo stesso nome del log di grafica, ma con estensione XML. Nell'esempio precedente, il file XML verrà denominato **regression_test_12.xml**. Per assegnare al file XML di un nome diverso, specificarlo dopo `-toXML`.  
  
```ms-dos  
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml  
```  
  
 Il file risultante conterrà un codice XML simile al seguente:  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Requisiti