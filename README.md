# CVDS-LAB6

1.

![image](https://user-images.githubusercontent.com/63562181/224484253-cf443f44-99d7-4250-ac29-04b9582d4b55.png)


2. 

![image](https://user-images.githubusercontent.com/63562181/224484265-c0a07e48-fcad-4f6a-80ac-96608a6df3ff.png)

3. 

![image](https://user-images.githubusercontent.com/89365336/224484578-0224bc65-666f-4ee3-9021-1f07062e48f3.png)

4. 


### Exercise 1: Creating Azure Web App and MySQL database


![image](https://user-images.githubusercontent.com/89365336/224484927-9f2eeb1e-0b47-4d0a-a052-2b18519c6e59.png)


![image](https://user-images.githubusercontent.com/63562181/224485158-adbe7a3d-603e-4990-9e2a-1053567e20ef.png)

![image](https://user-images.githubusercontent.com/89365336/224485244-095f7325-dcaf-4154-8f1e-a5b59f0cd753.png)


![image](https://user-images.githubusercontent.com/63562181/224485253-6ab20be4-caa9-4712-8626-04ae1af21215.png)

1. Launch the Azure Cloud Shell from the portal. To deploy to a resource group, enter the following command

```
az group create --name MyResourceGroup --location westus
```

![image](https://user-images.githubusercontent.com/63562181/224485386-7b750324-b70d-4b21-aee1-25ea97895f08.png)

2. To create an App service plan
```
az appservice plan create --resource-group MyResourceGroup --name MyPlan --sku S1
```

```
Resource provider 'Microsoft.Web' used by this operation is not registered. We are registering for you.
Registration succeeded.
{
  "elasticScaleEnabled": false,
  "extendedLocation": null,
  "freeOfferExpirationTime": null,
  "geoRegion": "West US",
  "hostingEnvironmentProfile": null,
  "hyperV": false,
  "id": "/subscriptions/172f5658-617b-47f3-8dab-0b902b6db63a/resourceGroups/MyResourceGroup/providers/Microsoft.Web/serverfarms/MyPlan",
  "isSpot": false,
  "isXenon": false,
  "kind": "app",
  "kubeEnvironmentProfile": null,
  "location": "westus",
  "maximumElasticWorkerCount": 1,
  "maximumNumberOfWorkers": 0,
  "name": "MyPlan",
  "numberOfSites": 0,
  "numberOfWorkers": 1,
  "perSiteScaling": false,
  "provisioningState": "Succeeded",
  "reserved": false,
  "resourceGroup": "MyResourceGroup",
  "sku": {
    "capabilities": null,
    "capacity": 1,
    "family": "S",
    "locations": null,
    "name": "S1",
    "size": "S1",
    "skuCapacity": null,
    "tier": "Standard"
  },
  "spotExpirationTime": null,
  "status": "Ready",
  "subscription": "172f5658-617b-47f3-8dab-0b902b6db63a",
  "tags": null,
  "targetWorkerCount": 0,
  "targetWorkerSizeId": 0,
  "type": "Microsoft.Web/serverfarms",
  "workerTierName": null,
  "zoneRedundant": false
}
```
3. Create the web app with a unique app name
```
az webapp create --resource-group MyResourceGroup --plan MyPlan --name MyUniqueAppName
```

![image](https://user-images.githubusercontent.com/63562181/224485855-351bf482-624d-49a1-b744-b18610b54a40.png)

Cambiamos MyUniqueAppName por OlayaOnate

4. Finally, create the MySQL server with a unique server name.
```
az mysql server create --resource-group MyResourceGroup --name mysqldbserver --admin-user mysqldbuser --admin-password P2ssw0rd@123 --sku-name GP_Gen5_2
```

![image](https://user-images.githubusercontent.com/89365336/224486013-4015c58a-9835-4034-bc13-99790f76860f.png)

