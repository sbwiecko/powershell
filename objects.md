## Properties and methods of objects

```powershell
gci c:\python | Get-Member # everything in PS is object; alias is gm
gm -InputObject c:\python # reads members of the global object
```



## Variables

```powershell
$variable = 32
variable variable # get content of $variable
Set-Variable valeur 64
Write-Host $variable # print content
Get-Variable # get all variables; alias is gv
Get-Variable valeur # get content

$variable.GetType() # type of the instance (method)
$variable.GetType().BaseType # type of the parent object
```

 

## Strings

```powershell
'coucou'
$v = "coucou"
"coucou $Host" # interpolation works only with double quotes
"coucou $Host.Name" # concatenates .Name to the content of $Host
"coucou $($Host.Name)" # variable substitution
"je suis né en juin".replace("juin", "août")

$here_string = @"
plusieurs
lignes
de texte
"@ # doesn't work in ISE, but in the shell of as a script
```

  

## Tables (lists)

```powershell
$t = 1,2,3,4
$t = @(1,2,3,4) # same as above
$t = 1,2,3,4,"coucou",(ls) # result of dir is an object as well
$t = @(1..10) # sequence
$t = 1..10 # same as above
$t.Count # .length is an alias of Count here
$t[3] # zero-indexed
$t[1..3] # slicing
$t[-1] # last item
$t += 5 # adding a value to the list
$v1, $v2, $v3, $v4 = $t # unpacking
$v2, $v4 $t[1,3]
Remove-Item variable:t

$mois = (new-object System.Globalization.CultureInfo("fr-FR")).DateTimeFormat.MonthNames # create a table from a method
```

  

## Arrays (dictionnaries ~ associative tables)

```powershell
$pays=@{ "FR" = "France";
  "BE" = "Belgique";
  "CA" = "Canada";
  "CH" = "Suisse"} # key = values entries
  
$pays.Count # length doesn't work on arrays
$pays.FR
$pays['FR'] # same as above
$pays.Add("IT","Italie")
$pays.Remove("CA")
$pays.ContainsValue("Belgique")

$params = @{path= "c:\demo"; Recurse= $true} # variable splat
dir @params # passing values from $params array to dir
```

 

## Date objects

```powershell
Get-Date
$d = Get-Date "08/01/2018" # create data object from string
(Get-Date "03/12/2018") | gm
$d.Hour
$d.Month
$d.ToShortDateString()
$d.AddMonths(6)
$d.AddHours(-12)

Get-Culture | gm # localization information using .NET 
$PSCulture #>> fr-FR
$culture = New-Object System.Globalization.CultureInfo("fr-FR") # new object
$culture.DateTimeFormat
$culture.DateTimeFormat.MonthNames[$d.Month-1] # zero-indexed
```

 