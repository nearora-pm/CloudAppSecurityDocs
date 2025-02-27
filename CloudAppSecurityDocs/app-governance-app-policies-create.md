---
title: Create app policies
ms.date: 11/02/2021
ms.topic: how-to
description: Learn how to create app policies.
---

# Create app policies

>*[Microsoft 365 licensing guidance for security & compliance](https://aka.ms/ComplianceSD).*

Along with a built-in set of capabilities to detect anomalous app behavior and generate alerts, app policies in Microsoft app governance are a way for you to:

- Specify conditions by which app governance can alert you to app behavior for automatic or manual remediation.
- Implement the app compliance policies for your organization.

You can create app policies from provided templates that can be customized, or you can create your own custom app policy.

To create a new app policy, go to **Microsoft 365 Defender > App governance > Overview page > Policies**:

- To create a new app policy with templates designed for app usage, select **Create policy** under **Create an app usage policy**.
- To create a new app policy with templates designed for app permissions, select **Create policy** under **Create a permissions policy**.
- To create a new app policy for app certification or for a custom policy, select **Create new**.

## App policy templates

To create a new app policy based on an app policy template, on the **Choose App policy template page**, select a category of app template, select the name of the template, and then select **Next**.

App governance has three categories of app policy templates.

### App users and data access

App governance includes these templates to generate alerts for app usage.

<br>

****

|Template name|Description|
|---|---|
|New app with a high volume of data access|Highlights any recently registered apps with high volume data access to ensure those data patterns are expected. <p> By default, this policy will flag all apps that have been registered in the last seven days and that have had more than 1 GB in data access over that period. This policy can be customized with more conditions and actions.|
|||

### App Permissions

App governance includes these templates to generate alerts for app permissions.

<br>

****

|Template name|Description|
|---|---|
|Overprivileged apps|Highlights any apps with more granted permissions than are being used by those apps to identify opportunities for potential permission reduction. <p> By default, this policy will flag all apps that are marked as Overprivileged if not used for 90 days. This time period filter can be customized with more conditions and actions.|
|New app with high-privilege permissions|Highlights all new apps with high privilege permissions to identify potential high-footprint apps that may need further investigation. <p> By default, this policy will flag all apps registered within the last seven days that have high-scoped permissions.|
 |New app with non-Graph permissions|Highlights all new apps with permissions to non-Graph APIs to identify and review APIs that might not be getting the latest security updates or may not be supported in future. <p> By default, this policy will flag all apps registered within the last seven days that have non-Graph permissions.|

### Microsoft 365 certification

App governance includes these templates to generate alerts for Microsoft 365 certification.

<br>

****

|Template name|Description|
|---|---|
|New uncertified app|Highlights new apps that haven't been through the Microsoft 365 certification process to ensure that they're expected in the tenant. <p> By default, this policy will flag all apps that were registered in the last seven days and are uncertified.|
|||

## Custom app policies

Use a custom app policy when you need to do something not already done by one of the built-in templates.

1. To create a new custom app policy, first select **Create new** on the **Policies** page. On the **Choose App policy template page**, select the **Custom** category, the **Custom policy** template, and then select **Next**.

1. On the **Name and description** page, configure the following:

    - Policy Name
    - Policy Description
    - Select the policy severity, which sets the severity of alerts generated by this policy.
      - High
      - Medium
      - Low

1. On the **Choose Policy settings and conditions** page, for **Choose which apps this policy is applicable for**, select:

    - All Apps
    - Choose specific apps

1. A pane allows you to select one or more apps.
  Select **Add**.

1. Select **Next**.

1. On the **Choose Policy settings and conditions** page, select **Set new conditions for policy**, and then select **Next**.

1. The **Create rule** pane allows you to select conditions for a new rule. Select **Add condition** and select from the list of conditions, and then specify the value of the condition. You can add multiple conditions.

    Here are the available conditions for a custom app policy.

    |Condition|Condition values accepted|More information|
    |---|---|---|
    |App registration age|Within last X days||
    |App certification|Basic compliance, Defender for Cloud Apps Compliance, or N/A|[Microsoft 365 Certification](/microsoft-365-app-certification/docs/enterprise-app-certification-guide)|
    |Publisher verification|Yes or No|[Publisher Verification](/azure/active-directory/develop/publisher-verification-overview)|
    |Application Permission|Select one or more API permissions from list|[Microsoft Graph permissions reference](/graph/permissions-reference)|
    |Delegated Permission|Select one or more API permissions from list|[Microsoft Graph permissions reference](/graph/permissions-reference)|
    |High privilege|Yes or No|This is an internal designation based on the same logic used by Defender for Cloud Apps.|
    |Overprivileged app|Yes or No|Apps with more granted permissions than are being used by those apps.|
    |Non-Graph API permissions|Yes or No|Apps that have non-Graph API permissions.|
    |App data access|Greater than X GB data access per hour||
    |App data access trend|X% increase in data usage in last seven days||
    |App API Access|Greater than X API calls per hour||
    |App API Access trend|X% increase in API Calls in last seven days||
    |Users consented|(Greater than or Less than) X consented users||
    |Priority user consented|Yes or No|A user with a [priority account](/microsoft-365/admin/setup/priority-accounts).|
    |App consented by|Select user(s) from list||
    |Consenting user's role|Select one or more: Teams Administrator, Directory Readers, Security Reader, Compliance Administrator, Security Administrator, Helpdesk Administrator, SharePoint Administrator, Exchange Administrator, Global Reader, Global Administrator, Compliance Data Administrator, User Administrator, Service Support Administrator|Multiple selections allowed. <p> Any Azure AD role with assigned member should be made available in this list.|
    |Workload accessed|OneDrive and/or SharePoint and/or Exchange|Multiple selections allowed.|
    |Error rate|Error rate is greater than X% in the last seven days, where X is an admin-defined value||
    ||||

    All of the specified conditions must be met for this app policy to generate an alert.

1. When you're done specifying the conditions, select **Save**, and then select **Next**.

1. On the **Define Policy Actions** page, select **Disable app** if you want app governance to disable the app when an alert based on this policy is generated, and then select **Next**.

1. On the **Define Policy Status** page, select one of these options:

    - **Audit mode**: Policies are evaluated but configured actions won't occur. Audit mode policies appear with the status of **Audit** in the list of policies.
    - **Active**: Policies are evaluated and configured actions will occur.
    - **Inactive**: Policies aren't evaluated and configured actions won't occur.

## Create a custom policy

App governance provides some basic templates that make it easy to create useful policies for monitoring apps in your tenant.

1. On the app governance page, select the **Policy** tab.
1. Select **Create policy**.
1. Under **Categories** select **Custom**. Under **Templates** select **Custom policy**. Select **Next**.
1. Enter a name for your policy, type a description, and then in the **Policy severity** drop-down list, select a severity. Select **Next**.
1. Select **No, I want to customize the policy** and then select **Next**.
1. Choose whether you want this policy to apply to all apps in your tenant or choose specific apps. If you choose specific apps for this policy, select **Add apps** and select the desired apps from the list. In the **Choose apps** pane, you can select multiple apps to which this policy will be applied, and then select **Add**. Select **Next** when you're satisfied with the list.
1. Select **Set new conditions for the policy** and then select **Edit conditions**. Select **Add condition** and choose a condition from the list and then select the condition to apply. Repeat to add more conditions. Select **Save** to save the rule, and when you're finished adding rules, select **Next**.
1. By default, this policy will trigger alerts when the conditions are met. You can choose to take action when the policy triggers such as **Disable app**. Use caution when applying actions because a policy may affect users and legitimate app use. Select **Next**.
1. Choose the policy status:
    - **Audit** - policy evaluation is active but policy action is disabled.
    - **Active** - policy evaluation and action are active.
    - **Inactive** - policy evaluation and action are disabled.
  
    You should use Audit mode for testing a new policy. Select **Next**.
1. Carefully review all parameters of your custom policy. Select **Submit** when you're satisfied. You can also go back and change settings by selecting **Edit** beneath any of the settings.

## Test and monitor your new app policy

Now that your app policy is created, you should monitor it on the **Policies** page to ensure it's registering an expected number of active alerts and total alerts during testing.

:::image type="content" source="media\app-governance\mapg-cc-policies-policy.png" alt-text="The app governance policies summary page in the Microsoft 365 Defender with a highlighted policy." lightbox="media\app-governance\mapg-cc-policies-policy.png":::

If the number of alerts is an unexpectedly low value, edit the settings of the app policy to ensure you've configured it correctly before setting its status.

Here's an example of a process for creating a new policy, testing it, and then making it active:

1. Create the new policy with severity, apps, conditions, and actions set to initial values and the status set to **Audit mode**.
2. Check for expected behavior, such as alerts generated.
3. If the behavior isn't expected, edit the policy apps, conditions, and action settings as needed and go back to step 2.
4. If the behavior is expected, edit the policy and change its status to **Active**.

:::image type="content" source="media/app-governance/mapg-create-new-policy-process.png" alt-text="The create app policy workflow." lightbox="media/app-governance/mapg-create-new-policy-process.png":::

## Next step

[Manage your app policies.](app-governance-app-policies-manage.md)
