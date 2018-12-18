---
title: 'Procedura dettagliata: Creazione di un SDK tramite JavaScript | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2132269329c8b6af3ac846596adea7b3462db5bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Procedura dettagliata: Creazione di un SDK tramite JavaScript
Questa procedura dettagliata viene illustrato come utilizzare JavaScript per creare un SDK come un Visual Studio Extension (VSIX) semplici operazioni matematiche.  La procedura dettagliata è suddivisa nelle parti seguenti:  
  
-   [Per creare il progetto SDK di estensione SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Per creare un'app di esempio che utilizza il SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Per JavaScript, non è disponibile alcun tipo di progetto libreria di classi. In questa procedura dettagliata viene creato il file di esempio arithmetic.js direttamente nel progetto VSIX. In pratica, è consigliabile innanzitutto compilare e testare i file CSS e JavaScript come un'applicazione Windows Store, ad esempio, tramite il **applicazione vuota** modello, prima di inserirli in un progetto VSIX.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> Per creare il progetto SDK di estensione SimpleMathVSIX  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco di categorie dei modelli, in **Visual c#**selezionare **estendibilità**, quindi selezionare il **progetto VSIX** modello.  
  
3.  Nel **nome** testo specificare `SimpleMathVSIX` e scegliere il **OK** pulsante.  
  
4.  Se il **Creazione guidata pacchetto di Visual Studio** viene visualizzata, scegliere il **Avanti** pulsante il **iniziale** pagina e quindi su **pagina 1 di 7**, scegliere il **Fine** pulsante.  
  
     Sebbene il **progettazione manifesto** viene aperto, si manterranno in questa procedura dettagliata semplice modificando direttamente il file manifesto.  
  
5.  In **Esplora**, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere **Visualizza codice**. Utilizzare questo codice per sostituire il contenuto esistente nel file.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  In **Esplora**, aprire il menu di scelta rapida per il progetto SimpleMathVSIX e quindi scegliere **Aggiungi**, **nuovo elemento**.  
  
7.  Nel **dati** categoria, seleziona **file XML**, denominare il file `SDKManifest.xml`, scegliere il **Aggiungi** pulsante.  
  
8.  In **Esplora**, aprire il menu di scelta rapida per il file SDKManifest.xml e quindi scegliere **aprire** per visualizzare il file di **Editor XML**.  
  
9. Aggiungere il codice seguente al file SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. In **Esplora**, scegliere il menu di scelta rapida per il file SDKManifest.xml **proprietà**.  
  
11. Nel **proprietà** finestra, impostare il **Includi in VSIX** proprietà **True**.  
  
12. In **Esplora**, nel menu di scelta rapida per il progetto SimpleMathVSIX scegliere **Aggiungi**, **nuova cartella**e quindi assegnare un nome di cartella `Redist`.  
  
13. Aggiungere le sottocartelle di Redist per creare questa struttura di cartelle:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. Scegliere il menu di scelta rapida per la cartella \js\ **Aggiungi**, **nuovo elemento**.  
  
15. In **elementi Visual c#**, selezionare il **Web** categoria e quindi selezionare il **JavaScript File** elemento. Nome del file `arithmetic.js`, quindi scegliere il **Aggiungi** pulsante.  
  
16. Inserire il codice seguente arithmetic.js:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. In **Esplora**, scegliere il menu di scelta rapida per il file arithmetic.js **proprietà**. Apportare queste modifiche delle proprietà:  
  
    -   Impostare il **Includi in VSIX** proprietà **True**.  
  
    -   Impostare il **copia nella Directory di Output di** proprietà **Copia sempre**.  
  
18. In **Esplora**, scegliere il menu di scelta rapida per il progetto SimpleMathVSIX **compilare**.  
  
19. Dopo la compilazione viene completata correttamente, nel menu di scelta rapida per il progetto, scegliere **Apri cartella in Esplora File**. Passare a \bin\debug\\ed eseguire `SimpleMathVSIX.vsix` per installarlo.  
  
20. Scegliere il **installare** pulsante e consentire l'installazione completa.  
  
21. Riavviare Visual Studio.  
  
##  <a name="createSampleApp"></a> Per creare un'app di esempio che utilizza il SDK  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco di categorie dei modelli, in **JavaScript**selezionare **Windows Store**, quindi selezionare il **applicazione vuota** modello.  
  
3.  Nel **nome** specificare `ArithmeticUI`. Fare clic sul pulsante **OK** .  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il progetto ArithmeticUI e quindi scegliere **Aggiungi**, **riferimento**.  
  
5.  In **Windows**, scegliere **estensioni**e notare che **semplici operazioni matematiche** viene visualizzato.  
  
6.  Selezionare il **semplici operazioni matematiche** casella di controllo e quindi scegliere il **OK** pulsante.  
  
7.  In **Esplora**in **riferimenti**, si noti che il **semplici operazioni matematiche** riferimento viene visualizzato. Espandere il nodo e notare che è in una cartella \js\ che include arithmetic.js. È possibile aprire arithmetic.js per verificare che il codice sorgente è stato installato.  
  
8.  Utilizzare il codice seguente per sostituire il contenuto di default.htm.  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. Utilizzare il codice successivo per sostituire il contenuto di \js\default.js.  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. Sostituire il contenuto di \css\default.css con questo codice:  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Premere il tasto F5 per compilare ed eseguire l'app.  
  
12. Nell'interfaccia utente dell'app, immettere i due numeri, selezionare un'operazione e quindi scegliere il **=** pulsante. Viene visualizzato il risultato corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)