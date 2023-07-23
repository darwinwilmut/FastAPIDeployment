# FastApi Deployment in Azure AppService

##### 1. Create an AppService with the Python 3.8 runtime stack.

##### 2. Enable AppService Logs in Azure AppService.

##### 3. Utilize Kuduconsole to remove Hostingstart.html from wwwroot/site.

##### 4. Add the application configuration for zip deployment: SCM_DO_BUILD_DURING_DEPLOYMENT=true.

##### 5. Navigate to Configuration --> General Settings --> Startup Command, set it to "startup.sh," and then click Save.

##### 6. Include the "startup.sh" file in the same location as the requirements.txt file. The contents of startup.sh should be: 
```sh
gunicorn -w 4 -k uvicorn.workers.UvicornWorker main:app
```

##### 7. Ensure that the "gunicorn" package is listed in the requirements.txt file.

##### 8. Use the Azure CLI command for zip deployment: 
```sh
az webapp deploy --name $APP_SERVICE_NAME --resource-group $RESOURCE_GROUP_NAME --src-path <zip-file-path>.
```
