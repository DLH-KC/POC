---
external help file: Microsoft.Azure.Commands.Batch.dll-Help.xml
online version: 
schema: 2.0.0
---

# Get-AzureBatchJob
## SYNOPSIS
Gets Batch jobs for a Batch account or job schedule.

## SYNTAX

### ODataFilter (Default)
```
Get-AzureBatchJob [-JobScheduleId <String>] [-Filter <String>] [-MaxCount <Int32>] [-Select <String>]
 [-Expand <String>] -BatchContext <BatchAccountContext>
```

### Id
```
Get-AzureBatchJob [[-Id] <String>] [-Select <String>] [-Expand <String>] -BatchContext <BatchAccountContext>
```

### ParentObject
```
Get-AzureBatchJob [[-JobSchedule] <PSCloudJobSchedule>] [-Filter <String>] [-MaxCount <Int32>]
 [-Select <String>] [-Expand <String>] -BatchContext <BatchAccountContext>
```

## DESCRIPTION
The Get-AzureBatchJob cmdlet gets the Azure Batch jobs for the Batch account specified by the BatchAccountContext parameter.
You can use the Id parameter to get a single job.
You can use the Filter parameter to get the jobs that match an Open Data Protocol (OData) filter.
If you supply a job schedule ID or PSCloudJobSchedule instance, this cmdlet returns only the jobs for that job schedule.

## EXAMPLES

### --------------------------  Example 1: Get a Batch job by ID  --------------------------
@{paragraph=PS C:\\\>}

```
PS C:\>Get-AzureBatchJob -Id "Job01" -BatchContext $Context
          CommonEnvironmentSettings   :
          Constraints                 : Microsoft.Azure.Commands.Batch.Models.PSJobConstraints
          CreationTime                : 7/25/2015 9:12:07 PM
          DisplayName                 :
          ETag                        : 0x8D29535B2941439
          ExecutionInformation        : Microsoft.Azure.Commands.Batch.Models.PSJobExecutionInformation
          Id                          : Job01
          JobManagerTask              :
          JobPreparationTask          :
          JobReleaseTask              :
          LastModified                : 7/25/2015 9:12:07 PM
          Metadata                    :
          PoolInformation             : Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
          PreviousState               :
          PreviousStateTransitionTime :
          Priority                    : 0
          State                       : Active
          StateTransitionTime         : 7/25/2015 9:12:07 PM
          Statistics                  :
          Url                         : https://pfuller.westus.batch.azure.com/jobs/Job01
```

This command gets the job that has the ID Job01.
Use the Get-AzureRmBatchAccountKeys cmdlet to assign a context to the $Context variable.

### --------------------------  Example 2: Get all active jobs for a job schedule  --------------------------
@{paragraph=PS C:\\\>}

```
PS C:\>Get-AzureBatchJob -JobScheduleId "JobSchedule27" -Filter "state eq 'active'" -BatchContext $Context
          CommonEnvironmentSettings   :
          Constraints                 : Microsoft.Azure.Commands.Batch.Models.PSJobConstraints
          CreationTime                : 7/25/2015 9:15:44 PM
          DisplayName                 :
          ETag                        : 0x8D2953633DD13E1
          ExecutionInformation        : Microsoft.Azure.Commands.Batch.Models.PSJobExecutionInformation
          Id                          : JobSchedule27:job-1
          JobManagerTask              :
          JobPreparationTask          :
          JobReleaseTask              :
          LastModified                : 7/25/2015 9:15:44 PM
          Metadata                    :
          PoolInformation             : Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
          PreviousState               :
          PreviousStateTransitionTime :
          Priority                    : 0
          State                       : Active
          StateTransitionTime         : 7/25/2015 9:15:44 PM
          Statistics                  :
          Url                         : https://pfuller.westus.batch.azure.com/jobs/JobSchedule27:job-1
```

This command gets the active jobs for the job schedule that has the ID JobSchedule27.

### --------------------------  Example 3: Gets all jobs under a job schedule by using the pipeline  --------------------------
@{paragraph=PS C:\\\>}

```
PS C:\>Get-AzureBatchJobSchedule -Id "JobSchedule27" -BatchContext $Context | Get-AzureBatchJob -BatchContext $Context
          CommonEnvironmentSettings   :
          Constraints                 : Microsoft.Azure.Commands.Batch.Models.PSJobConstraints
          CreationTime                : 7/25/2015 9:15:44 PM
          DisplayName                 :
          ETag                        : 0x8D2953633DD13E1
          ExecutionInformation        : Microsoft.Azure.Commands.Batch.Models.PSJobExecutionInformation
          Id                          : JobSchedule27:job-1
          JobManagerTask              :
          JobPreparationTask          :
          JobReleaseTask              :
          LastModified                : 7/25/2015 9:15:44 PM
          Metadata                    :
          PoolInformation             : Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
          PreviousState               :
          PreviousStateTransitionTime :
          Priority                    : 0
          State                       : Active
          StateTransitionTime         : 7/25/2015 9:15:44 PM
          Statistics                  :
          Url                         : https://pfuller.westus.batch.azure.com/jobs/JobSchedule27:job-1
```

This command gets the job schedule that has the ID JobSchedule27 by using the Get-AzureBatchJobSchedule cmdlet.
The command passes that job schedule to the current cmdlet by using the pipeline operator.
The command gets all jobs for that job schedule.

## PARAMETERS

### -BatchContext
Specifies the BatchAccountContext instance that this cmdlet uses to interact with the Batch service.
To obtain a BatchAccountContext object that contains access keys for your subscription, use the Get-AzureRmBatchAccountKeys cmdlet.

```yaml
Type: BatchAccountContext
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Expand
Specifies an Open Data Protocol (OData) expand clause.
Specify a value for this parameter to get associated entities of the main entity that you get.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter
Specifies an OData filter clause for jobs.
If you do not specify a filter, this cmdlet returns all jobs for the Batch account or job schedule.

```yaml
Type: String
Parameter Sets: ODataFilter, ParentObject
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
Specifies the ID of the job that this cmdlet gets.
You cannot specify wildcard characters.

```yaml
Type: String
Parameter Sets: Id
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobSchedule
Specifies a PSCloudJobSchedule object that represents the job schedule which contains the jobs.
To obtain a PSCloudJobSchedule object, use the Get-AzureBatchJobSchedule cmdlet.

```yaml
Type: PSCloudJobSchedule
Parameter Sets: ParentObject
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JobScheduleId
Specifies the ID of the job schedule which contains the jobs.

```yaml
Type: String
Parameter Sets: ODataFilter
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxCount
Specifies the maximum number of jobs to return.
If you specify a value of zero (0) or less, the cmdlet does not use an upper limit.
The default value is 1000.

```yaml
Type: Int32
Parameter Sets: ODataFilter, ParentObject
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Select
Specifies an OData select clause.
Specify a value for this parameter to get specific properties rather than all object properties.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

## OUTPUTS

### PSCloudJob

## NOTES

## RELATED LINKS

[Disable-AzureBatchJob]()

[Enable-AzureBatchJob]()

[Get-AzureRmBatchAccountKeys]()

[Get-AzureBatchJobSchedule]()

[New-AzureBatchJob]()

[Remove-AzureBatchJob]()

[Stop-AzureBatchJob]()

[Azure Batch Cmdlets]()

