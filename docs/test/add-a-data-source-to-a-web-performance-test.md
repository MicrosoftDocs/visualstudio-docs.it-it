---
title: Aggiungere un'origine dati a un test delle prestazioni Web in Visual Studio | Microsoft Docs
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: a2a079723d44bd7cee7ae418b5852a99d62cac25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Aggiungere un'origine dati a un test delle prestazioni Web

Associare i dati per fornire valori diversi nello stesso test, ad esempio, per fornire valori diversi ai parametri Post 'per i form.

 ![Associazione di dati a un test prestazioni Web](../test/media/web_test_databinding_conceptual.png)

 Verrà usata un'applicazione ASP.NET di esempio, contenente tre pagine ASPX: la pagina predefinita, una pagina Red e una pagina Blue. La pagina predefinita contiene un pulsante di opzione per la scelta tra rosso e blu e un pulsante Submit. Le altre due pagine ASPX sono molto semplici. Una include un'etichetta denominata Red e l'altra un'etichetta denominata Blue. Quando si sceglie Submit nella pagina predefinita, viene visualizzata una delle altre pagine. È possibile scaricare l'esempio di [ColorWebApp](http://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) o usare la propria applicazione Web.

 ![Esecuzione dell'applicazione Web da testare](../test/media/web_test_databinding_runwebapp.png)

 La soluzione deve inoltre includere un test delle prestazioni Web che scorra le pagine dell'applicazione Web.

 ![Soluzione con test prestazioni Web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Creare un database SQL

1. Se Visual Studio Enterprise non è disponibile, scaricarlo dalla pagina dei [download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).

2. Creare un database SQL.

     ![Aggiungere un nuovo database SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Creare un progetto di database.

     ![Creare il nuovo progetto dal database](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Aggiungere una tabella al progetto di database.

     ![Aggiungere una nuova tabella al progetto di database](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Aggiungere campi alla tabella.

     ![Aggiungere campi alla tabella](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Pubblicare il progetto di database.

     ![Pubblicare il progetto di database in Esplora soluzioni](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Aggiungere dati ai campi.

     ![Aggiungere dati ai campi](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

## <a name="add-the-data-source"></a>Aggiungere l'origine dati

1. Aggiungere un'origine dati.

     ![Aggiungere un'origine dati al test prestazioni Web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Scegliere il tipo di origine dati e denominarlo.

     ![Denominare l'origine database](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Creare una connessione.

     ![Scegliere la nuova connessione](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Immettere i dettagli della connessione.

     ![Immettere le proprietà di connessione del database SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Selezionare la tabella che si desidera utilizzare per il test.

     ![Aggiungere la tabella Color all'origine dati](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     La tabella è associata al test.

     ![Nodo Origini dati aggiunto al test prestazioni Web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Salvare il test.

## <a name="bind-the-data"></a>Associare i dati

1. Associare il campo ColorName.

     ![Associare il campo ColorName al valore RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Aprire il file Local.testsettings in Esplora soluzione e selezionare l'opzione Una esecuzione per riga origine dati.

     ![Modificare il file di impostazioni test](../test/media/web_test_databinding_sql_testsettings.png)

3. Salvare il test delle prestazioni Web.

## <a name="run-the-test-with-the-data"></a>Eseguire il test con i dati

1. Eseguire il test.

     ![Eseguire il test prestazioni Web per verificare l'associazione](../test/media/web_test_databinding_sql_runtest.png)

     Le due esecuzioni vengono visualizzate per ogni riga di dati. L'esecuzione 1 invia una richiesta per la pagina Red.aspx e l'esecuzione 2 invia una richiesta per la pagina Blue.aspx.

     ![Risultati delle esecuzioni dei test](../test/media/web_test_databinding_sql_runresults.png)

     Quando si esegue l'associazione a un'origine dati, è possibile violare la regola dell'URL di risposta predefinito. In questo caso, l'errore nell'esecuzione 2 è causato dalla regola che prevede la pagina Red.aspx dalla registrazione originale del test, ma il data binding ora la indirizza alla pagina Blue.aspx.

2. Correggere l'errore di convalida eliminando la regola di convalida dell'URL di risposta ed eseguendo nuovamente il test.

     ![Eliminare la regola di convalida dell'URL di risposta](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Il test delle prestazioni Web ha ora esito positivo tramite il data binding.

     ![Test superati usando il data binding](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Domande e risposte

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>D. Quali database è possibile utilizzare come origine dati?

**R.** È possibile usare:

- Microsoft SQL Azure.

- Qualsiasi versione di Microsoft SQL Server 2005 o versione successiva.

- File di database di Microsoft SQL Server (incluso SQL Express).

- Microsoft ODBC.

- File di Microsoft Access che utilizzano il provider .NET Framework per OLE DB.

- Oracle 7.3, 8i, 9i o 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>D. È possibile utilizzare un file di testo CSV (con valori delimitati da virgole) come origine dati?

**R.** Ecco come fare:

1. Creare una cartella per organizzare gli artefatti del database dei progetti e aggiungere un elemento.

     ![Aggiungere un nuovo elemento alla cartella dei dati](../test/media/web_test_databinding_foldernewitem.png "Web_Test_DataBinding_FolderNewItem")

2. Creare un file di testo.

     ![Denominare il nuovo file di testo ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png "Web_Test_DataBinding_FolderNewItemTextFile")

3. Modificare il file di testo e aggiungere quanto segue:

    ```
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Usare i passaggi descritti in [Associazione dei dati SQL](#AddingDataBindingWebTest_BindSQLData), ma scegliere File CSV come origine dati.

     ![Immettere un nome e scegliere un file CSV](../test/media/web_test_databinding_adddatasourcedialog.png "Web_Test_DataBinding_AddDataSourceDialog")

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>D. Quali operazioni si devono eseguire se il file CSV esistente non contiene intestazioni di colonna?

**R.** Se non è possibile aggiungere intestazioni di colonna, usare un file di descrizione dello schema per gestire il file CSV come database.

1. Aggiungere un nuovo file di testo denominato schema.ini.

     ![Aggiungere un file schema.ini](../test/media/web_test_databinding_schemafile.png "Web_Test_DataBinding_SchemaFile")

2. Modificare il file schema.ini per aggiungere le informazioni in cui è descritta la struttura dei dati. Ad esempio, un file di schema in cui è descritto il file CSV potrebbe essere simile al seguente:

    ```
    [testdata.csv]
    ColNameHeader=False
    ```

3. Aggiungere un'origine dati al test.

     ![Aggiungere un'origine dati al test delle prestazioni Web](../test/media/web_test_databinding_sql_adddatasource.png "Web_Test_DataBinding_SQL_AddDataSource")

4. Se si utilizza un file schema.ini, scegliere Database (non File CSV) come origine dati e denominarlo.

     ![Aggiungere l'origine dati di un database](../test/media/web_test_databinding_adddatasourcecolortext.png "Web_Test_DataBinding_AddDataSourceColorText")

5. Creare una nuova connessione.

     ![Scegliere una nuova connessione](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png "Web_Test_DataBinding_SQL_AddDataSourceDialogConnectionNew")

6. Selezionare il provider di dati .NET Framework per OLE DB.

     ![Selezionare il provider di dati OLE DB di .NET Framework](../test/media/web_test_databinding_adddatasourcecolortext2.png "Web_Test_DataBinding_AddDataSourceColorText2")

7. Scegliere Avanzate.

     ![Scegliere Avanzate](../test/media/web_test_databinding_advanced.png "Web_Test_DataBinding_Advanced")

8. Per la proprietà Provider, selezionare Microsoft.Jet.OLEDB.4.0, quindi impostare Proprietà estese su Testo;HDR=NO.

     ![Applicare le proprietà avanzate](../test/media/web_test_databinding_advancedproperties.png "Web_Test_DataBinding_AdvancedProperties")

9. Digitare il nome della cartella contenente il file di schema e verificare la connessione.

     ![Immettere il percorso della cartella dei dati](../test/media/web_test_databinding_adddatasourcecolortext5.png "Web_Test_DataBinding_AddDataSourceColorText5")

10. Selezionare il file CVS che si desidera utilizzare.

     ![Selezionare il file di testo](../test/media/web_test_databinding_adddatasourcecolortext6.png "Web_Test_DataBinding_AddDataSourceColorText6")

     Al termine, il file CSV viene visualizzato come tabella.

     ![Origine dati aggiunta al test](../test/media/web_test_databinding_adddatasourcecolortext7.png "Web_Test_DataBinding_AddDataSourceColorText7")

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>D. Come si utilizza un file XML come origine dati?

**R:** Sì.

1. Creare una cartella per organizzare gli artefatti del database dei progetti e aggiungere un elemento.

     ![Aggiungere un nuovo elemento alla cartella dei dati](../test/media/web_test_databinding_foldernewitem.png "Web_Test_DataBinding_FolderNewItem")

2. Creare un file XML.

     ![Aggiungere il file ColorData.XML](../test/media/web_test_databinding_additemxmlfile.png "Web_Test_DataBinding_AddItemXMLFile")

3. Modificare il file XML e aggiungere i dati:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Usare i passaggi descritti in [Associazione dei dati SQL](#AddingDataBindingWebTest_BindSQLData), ma scegliere File XML come origine dati.

     ![Immettere un nome e scegliere un file XML](../test/media/web_test_databinding_adddatasourcedialogxml.png "Web_Test_DataBinding_AddDataSourceDialogXML")

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>D. È possibile aggiungere un data binding a una richiesta di servizio Web che utilizza SOAP?

**R.** Sì, è necessario modificare manualmente il codice XML SOAP.

1. Scegliere la richiesta di servizio Web nell'albero delle richieste e nella finestra Proprietà scegliere il pulsante con i puntini di sospensione (...) nella proprietà Corpo stringa.

     ![Modificare il corpo della stringa del servizio Web](../test/media/web_test_databinding_webservicerequest.png "Web_Test_DataBinding_WebServiceRequest")

2. Sostituire i valori nel corpo SOAP con i valori associati ai dati usando la sintassi seguente:

    ```
    {{DataSourceName.TableName.ColumnName}}
    ```

    Si supponga, ad esempio, di avere il codice seguente:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Questo codice può essere modificato nel modo seguente:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Salvare il test.