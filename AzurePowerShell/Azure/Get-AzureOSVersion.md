---
external help file: Microsoft.WindowsAzure.Commands.ServiceManagement.dll-Help.xml
online version: 
schema: 2.0.0
---

# Get-AzureOSVersion
## SYNOPSIS
Lists all Azure guest operating systems.

## SYNTAX

```
Get-AzureOSVersion [-Profile <AzureSMProfile>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>]
```

## DESCRIPTION
The Get-AzureOSVersion cmdlet lists all the available Azure guest operating systems.

## EXAMPLES

### --------------------------  Example 1: Get all available operating systems  --------------------------
@{paragraph=PS C:\\\>}

```
PS C:\>Get-AzureOSVersion
```

This command retrieves an object that contains a list of all versions of guest operating systems that are available in the current subscription.

### --------------------------  Example 2: Display operating system information in a table  --------------------------
@{paragraph=PS C:\\\>}

```
PS C:\>Get-AzureOSVersion | Format-Table -AutoSize -Property "Family", "FamilyLabel", "Version"
```

This command retrieves an object that contains a list of all versions of guest operating systems that are available in the current subscription.
The command passes them to the Format-Table cmdlet by using the pipeline operator.
That cmdlet formats them as a table that shows the operating system family, operating system family label, and version.

## PARAMETERS

### -Profile
Specifies the Azure profile from which this cmdlet reads.
If you do not specify a profile, this cmdlet reads from the local default profile.

```yaml
Type: AzureSMProfile
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InformationAction
@{Text=}

```yaml
Type: ActionPreference
Parameter Sets: (All)
Aliases: infa

Required: False
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

### -InformationVariable
@{Text=}

```yaml
Type: String
Parameter Sets: (All)
Aliases: iv

Required: False
Position: Named
Default value: 
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AzureOSDisk]()

