## Jobs

```powershell
Start-Job {pip install numpy} # start job in bg
Get-Job # see status
Receive-Job Job1 # receive output from Job 1
```

## Services

```powershell
Restart-Service -Name Spooler -Force

```

##  Processes

```powershell
Get-Process # alias ps
ps | format-list ProcessName, WS
ps | Sort-Object -Descending WS | Format-List ProcessName, WS
ps | sort -desc WS | Select-Object -First 5
ps | Where-Object {$_.WS -gt 100*1024*1024} | sort -desc
ps | ? {$_.WS -gt 100*1024*1014} | sort -desc WS | fl ProcessName, WS
ps | ? {$_.WS -gt 100*1024*1014} | sort -desc WS | ft ProcessName,  
@{ Name='Memoire (MB)'; Expression= { $_.WS / 1024 / 1024 } }
```

##  Event_log

```powershell
Get-EventLog system
Get-EventLog -EntryType Error -LogName Application
Get-EventLog -EntryType Error -LogName Application -Message "*charger*"
```

##  PSDrive

```powershell
Get-PSDrive
cd Variable:
cd HKCU:
Get-ItemProperty .\Environment # not objects
Set-ItemProperty . -Name TEMP -value "c:\tmp"
```

## Users (adm)

```powershell
hostname # computer name
$ici = [adsi]"WinNT://$(hostname)"
$moi = $ici.Create("User", "seb")
$moi.setpassword("PASS#0123")
$moi.SetInfo() # register user
```

##  WMI

```powershell
$ici = [adsi]"WinNT://hostname"
$ici.Owner
Get-WmiObject -List -Namespace 'root\CIMV2'
gwmi -Class 'win32_Processor' -Namespace 'root\CIMV2' | gm
[wmi]'\root\CIMV2:win32_Processor.DeviceId="CPU0"'
```
