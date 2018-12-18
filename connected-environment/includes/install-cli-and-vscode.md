## <a name="install-the-connected-environment-cli"></a>Installare l'interfaccia della riga di comando di Connected Environment
Connected Environment richiede una configurazione minima del computer locale. La maggior parte della configurazione dell'ambiente di sviluppo viene archiviata nel cloud ed è condivisibile con altri utenti.

### <a name="install-on-mac"></a>Installare in Mac
Scaricare e installare l'interfaccia della riga di comando di Connected Environment:
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Installare in Windows
1. Scaricare ed eseguire il [programma di installazione dell'interfaccia della riga di comando di Connected Environment](https://aka.ms/get-vsce-windows). 

### <a name="install-on-linux"></a>Installare in Linux
Presto disponibile...

## <a name="get-kubernetes-debugging-for-vs-code"></a>Ottenere le funzionalità di debug di Kubernetes per Visual Studio Code
Anche se è possibile usare l'interfaccia della riga di comando di Connected Environment come strumento autonomo, le funzionalità avanzate come il debug di Kubernetes sono disponibili per gli sviluppatori di .NET Core e Node.js con Visual Studio Code.

1. Se non è disponibile, installare [Visual Studio Code](https://code.visualstudio.com/Download).
1. Scaricare l'[estensione Visual Studio Connected Environment](https://aka.ms/get-vsce-code).
1. Installare l'estensione: 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.1.vsix
```
