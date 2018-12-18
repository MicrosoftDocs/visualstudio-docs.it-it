## <a name="sign-in-to-azure"></a>Accedere ad Azure
Sarà necessario accedere ad Azure per creare l'ambiente di sviluppo. Digitare il comando seguente in un finestra del terminale:
```cmd
az login
```

> [!Note]
> Se non è già disponibile una sottoscrizione di Azure, è possibile creare un [account gratuito](https://azure.microsoft.com/free).

### <a name="if-you-have-multiple-azure-subscriptions"></a>Se sono disponibili più sottoscrizioni di Azure...
È possibile visualizzare le sottoscrizioni eseguendo: 
```cmd
az account list
```
Individuare la sottoscrizione con `isDefault: true` nell'output JSON.
Se non si tratta della sottoscrizione da usare, è possibile modificare la sottoscrizione predefinita:
```cmd
az account set --subscription <subscription ID>
```
