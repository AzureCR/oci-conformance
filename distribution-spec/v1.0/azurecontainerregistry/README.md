Prerequisites: Install the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/) and create an Azure subscription.

Create a resource group using the `az group create --name myResourceGroup --location eastus` command.

Create a registry by running `az acr create --resource-group myResourceGroup --name <testacr> --sku Basic`.

Enable basic credentials `az acr update -n <testacr> --admin-enabled true`.

Using `az acr credential show -n <testacr>` take note of the username and one of the admin credentials.

Set the required environment variables using the previous credentials.

```
$Env:OCI_ROOT_URL="https://<testacr>.azurecr.io"
$Env:OCI_USERNAME="<username>"
$Env:OCI_PASSWORD="<password>"
$Env:OCI_NAMESPACE="conformance"
$Env:OCI_TEST_PULL=1
$Env:OCI_TEST_PUSH=1
$Env:OCI_TEST_CONTENT_DISCOVERY=1
$Env:OCI_TEST_CONTENT_MANAGEMENT=1
```

And finally run the conformance tests.
