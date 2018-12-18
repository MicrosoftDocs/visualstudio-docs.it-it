## <a name="build-and-run-code-in-kubernetes"></a>Compilare ed eseguire codice in Kubernetes
A questo punto il codice verrà eseguito. Nella finestra del terminale eseguire questo comando dalla **cartella radice del codice**, ovvero webfrontend:

```cmd
vsce up
```

Nell'output del comando si noteranno vari aspetti man mano che procede:
1. Il codice sorgente è sincronizzato con l'ambiente di sviluppo in Azure.
1. Viene compilata un'immagine contenitore in Azure, come specificato dagli asset di Docker nella cartella del codice.
1. Vengono creati oggetti Kubernetes che usano l'immagine contenitore come specificato dal grafico Helm nella cartella del codice.
1. Vengono visualizzate informazioni sugli endpoint del contenitore. In questo caso, è previsto un URL HTTPS pubblico.
1. Presupponendo che le fasi precedenti siano state completate correttamente, dovrebbe iniziare a comparire output `stdout` (e `stderr`) durante l'avvio del contenitore.

> [!Note]
> Questi passaggi richiederanno più tempo alla prima esecuzione del comando `up`, ma le esecuzioni successive dovrebbero essere più rapide.

## <a name="test-the-web-app"></a>Testare l'app Web
Analizzare l'output della console per informazioni sull'URL pubblico che è stato creato dal comando `up`. Sarà nel formato: 

`Running at public URL: https://<servicename>-<environmentname>.vsce.io` 

Aprire l'URL in una finestra del browser. L'app Web dovrebbe essere caricata. Durante l'esecuzione del contenitore, l'output `stdout` e `stderr` viene trasmesso nella finestra del terminale.
