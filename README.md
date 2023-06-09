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

5.Navigate to the resource group that you have created. You should see a Azure Database for MySQL server provisioned. Select the database server.

![image](https://user-images.githubusercontent.com/63562181/224486156-7292541d-ce0d-4a6e-92b6-1bac601ffa6c.png)

6. Select Properties. Save the Server name and Server admin login name to a notepad.

+ Mateo Olaya:
  - ServerName: `onateolayaserver.mysql.database.azure.com`
  - Admin: `mysqldbuser@onateolayaserver`

+ Andrés Oñate
  - ServerName: `olayaonateserver.mysql.database.azure.com`
  - Admin: `mysqldbuser@olayaonateserver`

7. Select Connection security. Enable Allow access to Azure services toggle and Save the changes. This provides access to Azure services for all the databases in your MySQL server.

![image](https://user-images.githubusercontent.com/89365336/224486389-0b66f094-c076-456a-84a7-2e7ece7f170f.png)


## Exercise 2: Updating the App Settings for the Web App

1. Select Configuration. Set the Stack settings as shown in below image and click Save.

![image](https://user-images.githubusercontent.com/63562181/224486528-eb565dfe-536c-40c3-986b-0adbf8b0c351.png)

2. Select Overview and click Browse.

![image](https://user-images.githubusercontent.com/63562181/224486640-2c8cc974-856a-4927-abac-6299afaca768.png)

![image](https://user-images.githubusercontent.com/63562181/224486654-790f278c-8088-49e7-a084-603ae81827f5.png)

3. From the Azure portal, select the Web app you provisioned. Go to Configuration | Application settings | Connection strings and click on + New connection string.
```
jdbc:mysql://olayaonateserver.mysql.database.azure.com:3306/alm?useSSL=true&requireSSL=false&autoReconnect=true&user=mysqldbuser@olayaonateserver&password=P2ssw0rd@123
```

![image](https://user-images.githubusercontent.com/63562181/224487026-1d72eeba-4663-4c4e-8a9b-9d383f146cd9.png)

### Exercise 3: Deploy the changes to Web App

1. Select Pipelines | Pipelines. Choose the pipeline MyShuttleBuild and click Edit Pipeline to view the build definition.

![image](https://user-images.githubusercontent.com/63562181/224487286-6a84fe63-cb65-401c-bf79-6e7892ba2bed.png)


2. Click Queue to trigger the build and wait for the build to complete.

![image](https://user-images.githubusercontent.com/63562181/224487359-8e82b010-544b-4d44-8358-04bc3b6fbf9d.png)

![image](https://user-images.githubusercontent.com/63562181/224487436-9a0d73c8-b601-4a97-9ed7-f61e0ff2e9e6.png)

Este paso nos generó un error, se procede a completar el formulario asociado al problema.

Esperamos de 2 a 3 dias despues de enviar el formulario y reintentamos nuevamente 

![image](https://user-images.githubusercontent.com/89365336/225787340-421a1342-3a6b-447a-a2da-67d462df6be4.png)

3. Once the build succeeds, select Releases under Pipelines.

4. Select MyShuttle Release and click Edit to open the release definition.

![image](https://user-images.githubusercontent.com/89365336/225787412-abb48ede-8d76-4bb8-bd01-da3bf7782468.png)

5. Make sure the artifact is pointing to the Build artifact as shown below. If you are following this lab from Jenkins hands-on-lab, make sure the artifact is pointing to Jenkins.

![image](https://user-images.githubusercontent.com/89365336/225787741-77f007d7-3c3a-44f2-be55-ce6aa2984628.png)

6. Click Tasks. Select Execute Azure MySQL : SqlTaskFile task and provide the following details.

![image](https://user-images.githubusercontent.com/89365336/225788158-9392a8c0-7947-48b3-a06f-ceee9ed5b9a7.png)

7. Select the Deploy Azure App Service task, choose the Azure subscription details and select App Service name from the dropdown.

![image](https://user-images.githubusercontent.com/89365336/225788592-f6e8da53-a968-436d-be88-1c0d08f4bade.png)

8. Click on Save and then +Release | Create Release to start a new release

![image](https://user-images.githubusercontent.com/89365336/225789552-20a0e53a-0730-4218-943a-8b9760e902e1.png)

![image](https://user-images.githubusercontent.com/63562181/225794458-6f38fbc8-327e-4f85-ab9d-81b85b88b134.png)

![image](https://user-images.githubusercontent.com/63562181/225794532-d6782763-5ede-4b32-855d-72cb2ae4566e.png)

9. Wait for the release to complete. Then navigate to the Web App and select the URL from the overview blade. Add /myshuttledev context to the URL. For instance - http://myshuttle1.azurewebsites.net/myshuttledev

![image](https://user-images.githubusercontent.com/63562181/225794584-e72bb917-26f5-4512-b1b2-e515b21036aa.png)

10. Seleccione Iniciar sesión e intente iniciar sesión en el sitio con cualquiera de las siguientes credenciales.

![image](https://user-images.githubusercontent.com/63562181/225794808-694b8b67-4c32-4b80-bcf5-af52516627e5.png)

11. Si la base de datos se configuró correctamente y los parámetros de conexión son válidos, debería poder iniciar sesión en el portal.

