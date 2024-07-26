## How create
```bash
python -m venv .venv
```
## Run
```bash
.\.venv\scripts\activate
```

# <font color="#c0504d">Error</font>

A way is changing the terminal in VSCode to Command Prompt instead of PowerShell.

1. Open the drop-down on the right of the terminal and choose `Select Default Profile`
![](https://i.sstatic.net/NcnkD.png)
2. Select Command Prompt from the options.
![](https://i.sstatic.net/Kz2va.png)

Or, you can also set the execution policy to `RemoteSigned` or `Unrestricted` in PowerShell

Note: This only affects the current user

1. Open PowerShell
    
2. Run the following command: `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` OR `Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser`
    

(Remove `-Scope CurrentUser` to apply to all users)

#languageComplement 