# SSH configuration files
Setting up an SSH configuration file allows you to simplify connecting to the server - rather than having to include all the different options when you run the `ssh` command, we can define all of these in the configuration file and then initiate a connection with less effort.

If you setup a connection using [Visual Studio Code](../connecting/vscode.md) then this will have already created a configuration file for you.

## File location
Your configuration file is a text file called `config`, which lives inside the `.ssh` directory in your home/user directory.

=== "Windows"
    ```
    C:\Users\<username>\.ssh\config
    ```

=== "macOS"
    ```
    /Users/<username>/.ssh/config
    ```

=== "Linux"
    ```
    /home/<username>/.ssh/config
    ```

=== "UWE lab computers"
    ```
    C:\Users\<username>\OneDrive - UWE Bristol\.ssh\config
    ```
Open or create this file using a text editor (like Visual Studio Code).

## Standard format
The configuration file follows a standard format - a `Host` block for each machine we want to be able to connect to using SSH, with a set of directives which define how this connection should be setup.

A very simple configuration file would look like this:

```
Host csctcloud
    Hostname csctcloud.uwe.ac.uk
    User a.student@live.uwe.ac.uk
```

A connection can then be launched by referencing the relevant `Host` in the SSH connection command, without any additional arguments required:

``` bash
ssh csctcloud
```

### Specifiying an SSH key
Unless you specify otherwise, the SSH program will try to authenticate you to the server using keys stored in a standard way - saved in the `.ssh` folder in your home/user profile, and named after one of the available key algorithms that can be used to generate them.

!!! example
    If the `rsa` key algorithm was used to generate a public and private key pair, by default these would be saved as `id_rsa.pub` and `id_rsa` respectively.

The `IdentityFile` directive is used to specify the private key file that should be presented when it is saved in a non-standard location, or named differently. Set this directive to point to the correct private key to use.

!!! example
    If you chose `~/.ssh/csctcloud` as the file to save your key in, your public and private keys would be saved as `csctcloud.pub` and `csctcloud`.
    
    You would then reference this private key using the directive:

    ```
    IdentityFile ~/.ssh/csctcloud
    ```
