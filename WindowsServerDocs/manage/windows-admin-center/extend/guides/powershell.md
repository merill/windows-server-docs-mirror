---
layout: Conceptual
title: Using PowerShell in your extension | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/guides/powershell
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Using PowerShell in your extension Windows Admin Center SDK (Project Honolulu)
ms.topic: concept-article
author: davannaw-msft
ms.author: dawhite
ms.date: 2019-05-09T00:00:00.0000000Z
locale: en-us
document_id: 1118ce1a-217b-834f-cfa6-b90b5220d784
document_version_independent_id: b0dd7acf-9830-e9f4-a6c2-4ad9e7daff28
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/guides/powershell.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/guides/powershell
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/guides/powershell.md
cmProducts: []
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 115586d8-f8ec-83b9-3536-d7ca336ca1d4
---

# Using PowerShell in your extension | Microsoft Learn

Let's go more in-depth into the Windows Admin Center Extensions SDK - let's talk about adding PowerShell commands to your extension.

## PowerShell in TypeScript

The gulp build process has a generate step that will take any `{!ScriptName}.ps1` that is placed in the `\src\resources\scripts` folder and build them into the `powershell-scripts` class under the `\src\generated` folder.

Note

Don't manually update the `powershell-scripts.ts` nor the `strings.ts` files. Any change you make will be overwritten on the next generate.

## Running a PowerShell Script

Any scripts that you want to run on a node can be placed in `\src\resources\scripts\{!ScriptName}.ps1`.

Important

Any changes make in a `{!ScriptName}.ps1` file will not be reflected in your project until `gulp generate` has been run.

The API works by first creating a PowerShell session on the nodes you are targeting, creating the PowerShell script with any parameters that need to be passed in, and then running the script on the sessions that were created.

For example, we have this script `\src\resources\scripts\Get-NodeName.ps1`:

```ps1
Param
 (
    [String] $stringFormat
 )
 $nodeName = [string]::Format($stringFormat,$env:COMPUTERNAME)
 Write-Output $nodeName
```

We will create a PowerShell session for our target node:

```ts
const session = this.appContextService.powerShell.createSession('{!TargetNode}');
```

Then we will create the PowerShell script with an input parameter:

```ts
const command = PowerShell.createCommand(PowerShellScripts.Get_NodeName, {stringFormat: 'The name of the node is {0}!'});
```

Lastly, we need to run that script in the session we created:

```ts
  public ngOnInit(): void {
    this.session = this.appContextService.powerShell.createAutomaticSession('{!TargetNode}');
  }

  public getNodeName(): Observable<any> {
    const command = PowerShell.createCommand(PowerShellScripts.Get_NodeName, { stringFormat: 'The name of the node is {0}!'});
    return this.appContextService.powerShell.run(this.session, command)
    .pipe(
        map(
        response => {
            if (response && response.results) {
                return response.results;
            }
            return 'no response';
        }
      )
    );
  }

  public ngOnDestroy(): void {
    this.session.dispose()
  }

```

Now we will need to subscribe to the observable function we just created. Place this where you need to call the function to run the PowerShell script:

```ts
this.getNodeName().subscribe(
     response => {console.log(response)
     }
);
```

By providing the node name to the createSession method, a new PowerShell session is created, used, and then immediately destroyed upon completion of the PowerShell call.

### Key Options

A few options are available when calling the PowerShell API. Each time a session is created it can be created with or without a key.

**Key:** This creates a keyed session that can be looked up and reused, even across components (meaning that Component 1 can create a session with key "SME-ROCKS," and Component 2 can use that same session). If a key is provided, the session that is created must be disposed of by calling dispose() as was done in the example above. A session should not be kept without being disposed of for more than 5 minutes.

```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNode}', '{!Key}');
```

**Keyless:** A key will automatically be created for the session. This session with be disposed of automatically after 3 minutes. Using keyless allows your extension to recycle the use of any runspace that is already available at the time of creation of a session. If no runspace is available then a new one will be created. This functionality is good for one-off calls, but repeated use can affect performance. A session takes approximately 1 second to create, so continuously recycling sessions can cause slowdowns.

```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNodeName}');
```

or

```ts
const session = this.appContextService.powerShell.createAutomaticSession('{!TargetNodeName}');
```

In most situations, create a keyed session in the `ngOnInit()` method, and then dispose of it in `ngOnDestroy()`. Follow this pattern when there are multiple PowerShell scripts in a component but the underlying session IS NOT shared across components. For best results, make sure session creation is managed inside of components rather than services - this helps ensure that lifetime and cleanup can be managed properly.

For best results, make sure session creation is managed inside of components rather than services - this helps ensure that lifetime and cleanup can be managed properly.

### PowerShell Stream

If you have a long running script and data is outputted progressively, a PowerShell stream will allow you to process the data without having to wait for the script to finish. The observable next() will be called as soon as data is received.

```ts
this.appContextService.powerShellStream.run(session, script);
```

### Long Running Scripts

If you have a long running script that you would like to run in the background, a work item can be submitted. The state of the script will be tracked by the Gateway and updates to the status can be sent to a notification.

```ts
const workItem: WorkItemSubmitRequest = {typeId: 'Long Running Script',objectName: 'My long running service',powerShellScript: script,
//in progress notificationsinProgressTitle: 'Executing long running request',startedMessage: 'The long running request has been started',progressMessage: 'Working on long running script – {{ percent }} %',
//success notificationsuccessTitle: 'Successfully executed a long running script!',successMessage: '{{objectName}} was successful',successLinkText: 'Bing',successLink: 'http://www.bing.com',successLinkType: NotificationLinkType.Absolute,
//error notificationerrorTitle: 'Failed to execute long running script',errorMessage: 'Error: {{ message }}'
nodeRequestOptions: {   logAudit: true,   logTelemetry: true}
};

return this.appContextService.workItem.submit('{!TargetNode}', workItem);
```

Note

For progress to be shown, Write-Progress must be included in the script that you have written. For example:

```ps1
 Write-Progress -Activity ‘The script is almost done!' -percentComplete 95
```

#### WorkItem Options

| function | Explanation |
| --- | --- |
| submit() | Submits the work item |
| submitAndWait() | Submit the work item and wait for the completion of its execution |
| wait() | Wait for existing work item to complete |
| query() | Query for an existing work item by ID |
| find() | Find and existing work item by the TargetNodeName, ModuleName, or typeId. |

### PowerShell Batch APIs

If you need to run the same script on multiple nodes, then a batch PowerShell session can be used. For example:

```ts
const batchSession = this.appContextService.powerShell.createBatchSession(['{!TargetNode1}', '{!TargetNode2}', sessionKey);
  this.appContextService.powerShell.runBatchSingleCommand(batchSession, command).subscribe((responses: PowerShellBatchResponseItem[]) => {for (const response of responses) {  if (response.error || response.errors) {    //handle error  } else {    const results = response.properties && response.properties.results;    //response.nodeName    //results[0]  }}
     },
     Error => { /* handle error */ });

```

#### PowerShellBatch options

| option | Explanation |
| --- | --- |
| runSingleCommand | Run a single command against all the nodes in the array |
| run | Run corresponding command on paired node |
| cancel | Cancel the command on all nodes in the array |