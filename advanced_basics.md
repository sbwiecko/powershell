## Comparisons

```powershell
$mois -gt "juin" # attention not alphabetical sorting
$mois -like "jui*" # returns the table @('juin', 'juillet')
$mois -eq "juin" -or $mois -eq "août" #>> True
$mois -match "juin|août" # returns the table @('juin', 'août')
"rudi@babaluga.com" -match "\b[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]+\b" # regular expression
```



## Pipe

```powershell
dir | Where-Object { $_.Name -gt "f"} # filter
dir -File -Recurse -Depth 2 | Where-Object { $_.Length -lt 1000000 -and $_.Name -like 'h*' }
dir | Where-Object { $_.Name -like "p*" } | ForEach-Object { "c'est le fichier $($_.Name)" } # pass each element
dir | where { $_.Length -lt 1000000 } | Format-Table Name, Length
dir | ? { $_.Length -lt 1000000 } | ft Name, Length
dir | where { $_.Length -lt 1000000 } | fl # format-list
 
dir -File -Recurse -Depth 2 | ? { $_.Length -lt 1000000 -and $_.Name -like 'h*' } | % { "le fichier $($_.Name) pèse $($_.Length) octets" } | fl # foreach and % are aliases of ForEach-Object

dir | Rename-Item -newname {$_.name.remove(0,8)} # remove the first 8 characters of the name of each file in the folder
```



## Maths

```powershell
[math]::sqrt(4)
[math]::pi
[math]::log(10000,10)
[math]::round(2.56789)
[math]::floor(2.56789)
```



## Jobs

```powershell
Start-Job {pip install numpy} # start job in bg
Get-Job # see status
Receive-Job Job1 # receive output from Job 1
```


