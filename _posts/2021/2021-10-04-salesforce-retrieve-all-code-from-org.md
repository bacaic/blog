---
title: Retrieve all source code from Salesforce Sales & Service via VS Code
categories: [salesforce]
---

<p class="text-center">🐍👑🌍</p>

<!--more-->

## Requirements

- a Salesforce org with admin access
- VS Code with SFDX extension

## Authorize an Org

From VS Code, `Ctrl`+`Shift`+`P` to open the Palette menu, then `SFDX: Authorize an Org`. It will open up the default browser to login.

VS Code `Output` tab will show:
```console
Starting SFDX: Authorize an Org

15:11:51.709 sfdx force:auth:web:login --setalias myorg --instanceurl https://myorg.my.salesforce.com --setdefaultusername
Successfully authorized fcourgey@example.com with org ID 0000000000000000
You may now close the browser
15:12:12.217 sfdx force:auth:web:login --setalias myorg --instanceurl https://myorg.my.salesforce.com --setdefaultusername
 ended with exit code 0
```

## Retrieve the source code

Create `/manifest/package.xml` with below content, then Right Click on `package.xml`>`SFDX: Retrieve Source in Manifest from Org`:

Output:
```console
15:13:23.156 Starting SFDX: Retrieve Source from Org

=== Retrieved Source
FULL NAME                                                                 TYPE                      PROJECT PATH                                                                                                                                          
────────────────────────────────────────────────────────────────────────  ────────────────────────  
```

`/manifest/package.xml`:
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
  <types>
    <members>*</members>
    <name>ApexClass</name>
  </types>
  <types>
    <members>*</members>
    <name>ApexComponent</name>
  </types>
  <types>
    <members>*</members>
    <name>ApexPage</name>
  </types>
  <types>
    <members>*</members>
    <name>ApexTrigger</name>
  </types>
  <types>
    <members>*</members>
    <name>AssignmentRule</name>
  </types>
  <types>
    <members>*</members>
    <name>AuraDefinitionBundle</name>
  </types>
  <types>
    <members>*</members>
    <name>AuthProvider</name>
  </types>
  <types>
    <members>*</members>
    <name>BrandingSet</name>
  </types>
  <types>
    <members>*</members>
    <name>CallCenter</name>
  </types>
  <types>
    <members>*</members>
    <name>CampaignInfluenceModel</name>
  </types>
  <types>
    <members>*</members>
    <name>CleanDataService</name>
  </types>
  <types>
    <members>*</members>
    <name>Community</name>
  </types>
  <types>
    <members>*</members>
    <name>CompactLayout</name>
  </types>
  <types>
    <members>*</members>
    <name>ConnectedApp</name>
  </types>
  <types>
    <members>*</members>
    <name>CorsWhitelistOrigin</name>
  </types>
  <types>
    <members>*</members>
    <name>CustomApplication</name>
  </types>
  <types>
    <members>*</members>
    <name>CustomField</name>
  </types>
  <types>
    <members>*</members>
    <name>CustomNotificationType</name>
  </types>
  <types>
    <members>*</members>
    <name>CustomObject</name>
  </types>
  <types>
    <members>*</members>
    <name>CustomSite</name>
  </types>
  <types>
    <members>*</members>
    <name>CustomTab</name>
  </types>
  <types>
    <members>*</members>
    <name>Dashboard</name>
  </types>
  <types>
    <members>*</members>
    <name>Document</name>
  </types>
  <types>
    <members>*</members>
    <name>DuplicateRule</name>
  </types>
  <types>
    <members>*</members>
    <name>EmailServicesFunction</name>
  </types>
  <types>
    <members>*</members>
    <name>EmailTemplate</name>
  </types>
  <types>
    <members>*</members>
    <name>EscalationRule</name>
  </types>
  <types>
    <members>*</members>
    <name>FlexiPage</name>
  </types>
  <types>
    <members>*</members>
    <name>Flow</name>
  </types>
  <types>
    <members>*</members>
    <name>FlowDefinition</name>
  </types>
  <types>
    <members>*</members>
    <name>Group</name>
  </types>
  <types>
    <members>*</members>
    <name>HomePageLayout</name>
  </types>
  <types>
    <members>*</members>
    <name>Layout</name>
  </types>
  <types>
    <members>*</members>
    <name>Letterhead</name>
  </types>
  <types>
    <members>*</members>
    <name>LightningComponentBundle</name>
  </types>
  <types>
    <members>*</members>
    <name>LightningExperienceTheme</name>
  </types>
  <types>
    <members>*</members>
    <name>ListView</name>
  </types>
  <types>
    <members>*</members>
    <name>MatchingRule</name>
  </types>
  <types>
    <members>*</members>
    <name>MatchingRules</name>
  </types>
  <types>
    <members>*</members>
    <name>PathAssistant</name>
  </types>
  <types>
    <members>*</members>
    <name>PermissionSet</name>
  </types>
  <types>
    <members>*</members>
    <name>PlatformCachePartition</name>
  </types>
  <types>
    <members>*</members>
    <name>Profile</name>
  </types>
  <types>
    <members>*</members>
    <name>ProfilePasswordPolicy</name>
  </types>
  <types>
    <members>*</members>
    <name>ProfileSessionSetting</name>
  </types>
  <types>
    <members>*</members>
    <name>Queue</name>
  </types>
  <types>
    <members>*</members>
    <name>QuickAction</name>
  </types>
  <types>
    <members>*</members>
    <name>RecordType</name>
  </types>
  <types>
    <members>*</members>
    <name>RemoteSiteSetting</name>
  </types>
  <types>
    <members>*</members>
    <name>Report</name>
  </types>
  <types>
    <members>*</members>
    <name>ReportType</name>
  </types>
  <types>
    <members>*</members>
    <name>Role</name>
  </types>
  <types>
    <members>*</members>
    <name>SharingRules</name>
  </types>
  <types>
    <members>*</members>
    <name>StaticResource</name>
  </types>
  <types>
    <members>*</members>
    <name>TopicsForObjects</name>
  </types>
  <types>
    <members>*</members>
    <name>TransactionSecurityPolicy</name>
  </types>
  <types>
    <members>*</members>
    <name>ValidationRule</name>
  </types>
  <types>
    <members>*</members>
    <name>WebLink</name>
  </types>
  <types>
    <members>*</members>
    <name>WorkflowAlert</name>
  </types>
  <types>
    <members>*</members>
    <name>WorkflowFieldUpdate</name>
  </types>
  <types>
    <members>*</members>
    <name>WorkflowRule</name>
  </types>
  <version>47.0</version>
</Package>
```