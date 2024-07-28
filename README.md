# CovSysTime2AnyZone_ps
ALL BASIC POWERSHELL. This script is dedicated to helping users obtain the time in any zone, regardless of their system default time.

```powershell
# Which time zone you need
$NeedZone = [Int16]8
# Which format you'd like to use for output
$OutputFormat = "%Y-%m-%d_%H.%M.%S"
#
#
# Get time now as seconds with zone
$NowTime = [UInt32](Get-Date -UFormat "%s")
# Get zone as int (never use uint for this)
$Zone = [Int16](Get-Date -UFormat "%Z").ToString()
# Switch to Zone you need
$NeedTime = ($NeedZone - $Zone) * 60 * 60
$Result = $NowTime + $NeedTime
# Format it
$Formated = (Get-Date -UnixTimeSeconds $Result -UFormat $OutputFormat).ToString()
$Formated
```
