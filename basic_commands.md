## PS env

```powershell
$PSVersionTable
$Host # ConsoleHost
$Host.Version
$env:Path
```

 

## Command basics

```powershell
Get-Command # list of commands
gcm # alias
Get-Command -Verb Get # filter -Verb or -Noun or *term*
Get-Command -Noun Date
```

 

## Help

```powershell
Get-Help Get-Alias # same as help gal
help gal -Online
Update-Help # in administrator session, if required
```

 

## \Redirection

```powershell
dir > dir_text.txt # redirection into a txt file
dir | sort Length # pipe
```

 

## \Alias

```powershell
Get-Alias # list of aliases
Get-Alias gal
gal gal | gm
gal dir #> Get-ChildIten
gal -Definition Get-ChildItem #> dir, gci, ls

New-Alias quoi? Get-ChildItem # new alias created
Set-Alias quoi? Get-Command
Export-Alias -Path MesAliasPS.txt -Name quoi?
Import-Alias -Path MesAliasPS.txt
```

 

## History

```powershell
Get-History
gal -Definition *History #> h
h -count 2 # last 2 commands listed
h 1
Invoke-History note # look in history for occurrence of note* cmd; alias is r
```

 