# Issues running or installing Azure CLI
## "Access Denied"
If you receive a permission error ("Access Denied") when trying to run `az` commands, this normally means the CLI was installed while using PowerShell as an adminstrator, which causes some file permission conflicts.

Open up an PowerShell window as an administrator (choose *Run as administrator* from the start menu) and run the following commands to remove Azure CLI and extensions:
``` powershell
az extension remove -n ssh
```

``` powershell
winget uninstall --exact --id Microsoft.AzureCLI
```

Close this PowerShell window and open up a new window **not as an administrator**, then run the following command to reinstall the CLI:
``` powershell
winget install --exact --id Microsoft.AzureCLI
```

## Issues installing SSH extension
Sometimes locally installed versions of Python can conflict with the version the CLI uses internally, which prevents the CLI from properly installing the SSH extension or otherwise working normally.

Try explictly setting the Python path:
``` powershell
$ENV:PYTHONPATH = "C:\\Program Files\\Microsoft SDKs\\Azure\\CLI2"
```

Then try calling the CLI again:
``` console
az extension add -n ssh
```

### Conflicts with Anaconda
Anaconda can cause wider conflicts, to resolve we need to take it's Python distribution out of the path while we install the Azure CLI extension.

* Rename `C:/Users/<username>/anaconda3` to `C:/Users/<username>/anaconda3_temp`
* Retry ssh extension installation `az extension...`
* Revert anaconda3 directory name back to original

## SSH extension stops working after an update
Occasionally the SSH extension can stop working after an updated with an error message similar to `no module named 'rpds.rpds'`.

Try reinstalling the extension:
``` console
az extension remove -n ssh && az extension add -n ssh
```

[Github issue](https://github.com/Azure/azure-cli/issues/31017){:target="_blank"}