##### et-ExecutionPolicy RemoteSigned # (adm) only remote script needs signature

Use access points for debogging

Always execute from destination directory (security) 

```powershell
.\script1.ps1
```

## Parameters

```powershell
param(
	[Parameter(Mandatory=$true)]
	[ValidateScript({ Test-Path $_ -PathType 'Container' })]
		# code for the validation procedure
	[string]
	$chemin
)
```

```powershell
param(
	[string]
	$chemin = '.' # default value
)
```

## Function

```powershell
function GetFolders ([string]$path) {
	Get-ChildItem -Path $path -Directory
}
```

good practice to use long-name commands in scripts

##  Loops

```powershell
foreach ($folder in GetFolders($chemin)) {
    Write-Host $folder.Fullname
}
```