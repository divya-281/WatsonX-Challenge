### Application performance management (agent based)

An Application Perspective (AP) is a power tool for monitoring, alerting, and analysis of a microservice environment. Each AP auto-generates a feature rich monitoring dashboard for the [golden signals](https://sre.google/sre-book/monitoring-distributed-systems/#xref_monitoring_golden-signals) and more. It organizes a team so they stay focused on the services they are interested in and aren’t distracted. Alerts, errors, and logs are scoped to an AP to focus the troubleshooting. From a security perspective, an organization can use an AP to limit visibility to infrastructure and services.

### Creating an Application

The Application Perspective is a unique capability of Instana. An AP creation wizard is       available for new users to easily create simple and frequently used types of APs. An advanced screen is available if you are familiar or proficient with Instana or you need to create a sophisticated AP. It is very easy to switch between these two modes without data loss.

To create an application perspective to view trace information that is gathered, complete either of the following steps:

Click Applications in the sidebar of the Instana UI, and then click +ADD > New Application Perspective.
Click New Application Perspective from the Applications pane in the Instana landing page.

### Simplified AP Creation using the Wizard

1. Simplified AP Creation using the Wizard
    * The AP Creation Wizard is an interactive, simple way to create an AP. It has three steps:
        1. Select a blueprint from the common use cases.
        2. Specify the application’s model by selecting the tags and values to identify the services or endpoints to include.
        3. Provide the final details to finish the creation.
    At any time you can switch to the advanced mode by selecting the button in the top right that says "Switch to Advanced Mode."

### Advanced AP Creation

All the data that is needed for an AP is entered in a single screen with the Advanced AP creation view. The steps within this view are:

1.  Enter a name for your application perspective.
2.  To define your application perspective using tags, click **Add filter.**

For tags to conjoin, choose between the AND or OR operator and use brackets. When using a mix of AND and OR conjunctions without brackets, AND conjunctions have the highest priority and are evaluated first. For example, the tag definitions tag.A AND tag.B OR tag.c AND tag.d is interpreted and processed as (tag.A AND tag.B) OR (tag.c AND tag.d).

Each call that matches the filters, including calls to any database or messaging services that are invoked within the application, is associated with this application perspective.

There is also an option to apply filters and group by the source or destination of a call.

Note: The service.name and endpoint.name tags, along with the infrastructure entity tags such as agent.tag or host.name can be applied to both the source and the destination of a call. By default, it's applied to the destination and it can be modified by using the edit filter dialog. An example for combining source and destination is for an application that groups calls which are issued from the agent.zone prod towards the agent.zone test.

* To include all the services that transitively fall downstream of those matched by the tags  you have specified, select **Include All Downstream Services**. Select **No Downstream Services** if only the filtered services are all to consider. Select **Immediate downstream database and messaging services** if the database or messaging services directly communicating with the selected services should be included in the AP.
* Select the default dashboard view

**Inbound calls:** Inbound calls are calls initiated from outside the application and where the destination service is part of the selected application perspective.

**All calls:** Results and metrics for not only calls at the application perspective boundary, but also those occurring within the application perspective.

By default, various dashboards such as the Summary tab, only show numbers for "Inbound Calls". Wherever the Inbound or All Calls selector is available on a dashboard, the perspective can be switched to All Calls. When selecting services and endpoints within an application perspective, the boundary setting is inherited.    

### Update an application perspective

Existing application perspectives can be updated or deleted. Note that once an application perspective is updated, the new configuration only applies to new incoming calls after the change. Calls and services that were included in the application before the change are not affected.

On the sidebar, click Applications and then select your application perspective.
Select the Configuration tab.

### Switching to Advanced Mode or back to Simple Mode

At any point you can switch from the simple wizard mode to the advanced mode using the button. In the Step 2 example above, selecting the advanced mode would present the screen shown as follows. All of the data that was previously entered is carried forward to this view. The reverse is also true -- if you were to select “Simple Mode” this data would not be lost either.

## See also

-   [How to create an application perspective in Instana](https://www.ibm.com/docs/en/instana-observability/current?topic=applications-application-perspectives)
