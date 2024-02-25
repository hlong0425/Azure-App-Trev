### Deployment
1.
```bash
    dotnet publish -o publish
```
2.
```bash
    cd ./publish
```
3.
```bash
    Compress-Archive * publish.zip
```

4.Use Azure cloud shell to create resources.
```bash
    az group create --location eastasia --resource-group az-group-rg
```

```bash
    az appservice plan create -g az-group-rg -n az-trev-plan --tags ApplicationName="test-azure" OwnerService="longhoang" ProjectID="no"
```

```bash
    az webapp create -g az-group-rg -p az-trev-plan -n az-webapp-trev-2024 --tags ApplicationName="test-azure" OwnerService="longhoang" ProjectID="no"
```

5.Deployment (powershell)
```bash
    az webapp deployment source config-zip --src .\publish.zip -n az-webapp-trev-2024 -g az-group-rg
```

5.Deployment (powershell)
```bash
    az webapp browse -n az-webapp-trev-2024 -g az-group-rg
```

