2. Premere F5 (o digitare `vsce up` nella finestra del terminale) per eseguire il servizio. In questo modo, il servizio verrà eseguito automaticamente nel nuovo spazio selezionato `scott`. 
1. È possibile verificarlo eseguendo di nuovo `vsce list`. In primo luogo, si noterà che un'istanza di `mywebapi` è ora in esecuzione nello spazio `scott` (la versione in esecuzione in `mainline` è ancora in esecuzione ma non è elencata). In secondo luogo, l'URL del punto di accesso per `webfrontend` ha il prefisso "scott-". Questo URL è univoco per lo spazio `scott` e indica che le richieste inviate all'URL di scott tenteranno per prima la route verso i servizi nello spazio `scott` e poi eseguiranno il fallback ai servizi nello spazio `mainline`.

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

Questa funzionalità predefinita di Connected Environment consente di eseguire test completi del codice in un ambiente condiviso senza richiedere a ogni sviluppatore di ricreare lo stack completo dei servizi nel proprio spazio. Si noti che questo indirizzamento richiede l'inoltro di intestazioni di propagazione nel codice dell'app, come illustrato nel passaggio precedente di questa guida.

## <a name="test-code-in-a-space"></a>Testare il codice in uno spazio
Per testare la nuova versione di `mywebapi` in combinazione con `webfrontend`, aprire il browser all'URL del punto di accesso pubblico per webfrontend e passare alla pagina About. Dovrebbe essere visualizzato il nuovo messaggio.

A questo punto, rimuovere la parte "scott-" dell'URL e aggiornare il browser. Dovrebbe essere visualizzato il comportamento precedente (esposto dalla versione `mywebapi` in esecuzione in `mainline`).