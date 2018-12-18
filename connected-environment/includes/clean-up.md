## <a name="clean-up"></a>Eseguire la pulizia
Per eliminare completamente un ambiente Connected Environment in Azure, inclusi tutti i servizi in esecuzione al suo interno, usare il comando `vsce env rm`. Tenere presente che questa azione è irreversibile.

L'esempio seguente elenca gli ambienti Connected Environment nella sottoscrizione di Azure attiva, e quindi elimina l'ambiente denominato 'myenv' incluso nel gruppo di risorse 'myenv-rg'.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

