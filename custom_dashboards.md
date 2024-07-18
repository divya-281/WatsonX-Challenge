
# Building Custom Dashboards in Instana

Instana offers pre-built dashboards for common monitoring scenarios, but also empowers you to create custom dashboards for specific needs. Here's a breakdown of the available options: 

**1. Native Custom Dashboards:**
Instana allows you to build custom dashboards directly within the platform. This is ideal for:
- Focusing on specific applications or services.
- Combining different metrics for a holistic view.
- Tailoring dashboards to individual user roles.

**Key Features:**
- Drag-and-drop widget creation for easy customization.
- Diverse widget types (charts, single values, text) for versatile data presentation.
- Filters and grouping options to refine the displayed data.
- Sharing capabilities to collaborate with colleagues.
- TV Mode for optimized big-screen viewing.

**2. Grafana Integration:**
Instana provides a Grafana plugin, enabling you to:
- Combine Instana data with metrics from other sources within Grafana.
- Leverage Grafana's advanced visualization capabilities for deeper analysis.

**3. Web REST API Integration:**
For maximum flexibility, Instana offers a Web REST API. This allows you to:
- Query Instana data programmatically.
- Build dashboards in your preferred visualization tool.

**Best for:**
- Developers comfortable with API integration.
- Highly customized monitoring solutions.

**Choosing the Right Option:**
The best approach depends on your specific needs and skillset. Native dashboards offer a user-friendly starting point, while Grafana and API integrations provide advanced customization possibilities.

## Create a Custom Dashboard: A Step-by-Step Guide

Instana allows you to create custom dashboards tailored to your specific monitoring needs. Here's a breakdown of the process, presented in clear points:

1.  **Access the Dashboard Creation Menu:** Navigate to the Instana platform's landing page. Locate the dropdown menu associated with the "Instana" logo. Click on this dropdown to reveal additional options.

1.  **Initiate Dashboard Creation:** Within the dropdown menu, select the option for creating a new dashboard. This might be labeled as "New Dashboard" or something similar.

1.  **Name Your Masterpiece:** Assign a descriptive and memorable name to your dashboard. Choose a name that clearly reflects the purpose of the dashboard and the data it will display. Consider the intended audience when selecting a name. If you plan to share the dashboard with others, ensure the name conveys its function effectively.

1.  **Start Building (Adding Widgets):** Instana provides a "**+ Add Widget**" button within the custom dashboard interface. Clicking this button allows you to choose the type of widget you want to include on your dashboard. Common widget types include charts, single number displays, and markdown text sections.


**Additional Tips:**

-  **Dashboard Sharing:** While new dashboards are initially private by default, Instana allows you to share them with other users within your organization. This can be helpful for collaborating on monitoring tasks or providing broader visibility into key performance metrics.
-  **Advanced Customization:** Instana offers a variety of advanced customization options for your dashboards. Explore these functionalities after familiarizing yourself with the basic creation process. You can adjust the layout, add filters to refine the displayed data, and leverage features like time shifting for comparisons.

By following these steps and exploring Instana's customization options, you can create informative and visually appealing custom dashboards that effectively monitor and communicate your application's health and performance.

## Adding Widgets

Once you've created your custom dashboard in Instana, it's time to populate it with informative widgets. Here's a breakdown of the process:

**1. Unleashing the Widget Arsenal:**
Locate the "**+ Add Widget**" button within your custom dashboard. This button acts as the gateway to adding various data visualization elements to your dashboard.

**2. Widget Selection Symphony:**
Instana offers a growing selection of widget types, allowing you to present your data in the most effective way. Some common widget options include:

-  **Charts:** Line graphs, bar charts, pie charts, and more to visualize trends and relationships.
-  **Big Numbers:** Prominently display key metrics like average response time or error rate.
-  **Markdown Text:** Include descriptive text or notes to provide context or explanations within your dashboard.

**3. Widget Placement and Customization:**
After selecting a widget type, you can freely drag and drop it onto your dashboard to position it strategically. Instana allows you to resize the widget to fit your layout needs, ensuring optimal use of dashboard space.

**4. Stay Tuned for More:**
Instana actively expands its widget library. Keep an eye out for new additions that might be particularly suited to your monitoring requirements.

**By strategically adding and customizing widgets, you can create custom dashboards in Instana that effectively communicate critical performance insights for your applications.**

## Selecting the Data Spotlight
Once you've chosen the type of widget for your custom dashboard in Instana, it's time to select the data it will display. Here's a breakdown of the process:

**1. Unleashing the Data Powerhouse:**
Instana custom dashboards allow you to leverage a vast amount of monitoring data, including high-cardinality data and insights from the Dynamic Graph. This empowers you to create comprehensive and informative dashboards.

**2. Multi-Dataset Mastery (For Specific Widget Types):**
Certain widget types offer the capability to display multiple datasets. This allows for even more intricate data visualization and analysis. Each dataset within the widget can have its own distinct data source.

  

**3. Data Source & Metric Selection:**
To configure your widget's data display, you'll need to select the following:
-  **Data Source:** Choose the source of the data you want to visualize. This might be Applications, Events, Websites, Mobile Apps, or Infrastructure & Platforms Metrics.
-  **Metric:** Once you've selected the data source, a dropdown list will appear. This list displays the available metrics relevant to your chosen source. Select the specific metric you want to visualize within the widget.

  **4. Real-time Preview:**
As you make your data source and metric selections, a preview will automatically appear at the bottom of the widget configuration dialog. This preview provides a real-time glimpse of how the data will be visualized within the widget. Use this preview to refine your selections and ensure the widget effectively presents the desired information.

**5. Infrastructure & Platforms Metric Nuances:**
For Infrastructure & Platforms Metrics, Instana offers a dedicated catalog for metric selection. Not all metrics might be listed initially, so you can utilize the search bar to locate a specific metric you're interested in. Additionally, the widget's filter can be used to narrow down the catalog and display only relevant metrics.

**By carefully selecting the data source and metric, you can ensure your Instana custom dashboard widgets effectively portray the performance insights you need to monitor your applications and infrastructure.**

## Selecting the Right Aggregation

Within Instana's custom dashboards, selecting an appropriate data aggregation method is crucial for interpreting the data effectively. Here's a breakdown of this vital step:

**Understanding Aggregation:**
Aggregation acts as a way to condense multiple data points representing the chosen metric. It transforms raw data into a single, more manageable value for visualization.

**Aggregation Choices:**

The specific aggregation method you select depends on the widget type and the insights you want to glean. Here are some common choices:

-  **mean:** Calculates the average value across the chosen timeframe (ideal for understanding typical behavior).
-  **min:** Displays the minimum value within the timeframe (useful for identifying potential bottlenecks).
-  **max:** Highlights the maximum value within the timeframe (valuable for spotting performance spikes).
-  **sum:** Calculates the total sum of all values within the timeframe (helpful for understanding overall resource consumption).
-  **percentile (25th, 50th, ...):** Indicates the value where a specific percentage (percentile) of data points fall below (useful for analyzing distribution).

**Timeframe vs. Buckets:**

-  **Single Value Widgets & Pie Charts:** For these elements, aggregation applies to the entire chosen timeframe.
-  **Time Series Widgets:** Aggregation happens per individual data point "bucket" within the timeframe. This allows for visualization of trends over time.

**Infrastructure Data Source Specificity:**
When working with the Infrastructure & Platforms Metrics data source, you have the option to perform a "sum" aggregation across all data series included in your chart. Imagine visualizing CPU usage for Docker containers. You might want to calculate the mean CPU usage per container within a time bucket, but then display the total sum of those values across all containers.

**Leveraging Additional Resources:**
For an in-depth exploration of aggregation techniques, refer to the dedicated Instana aggregation documentation. This documentation will provide further details and guidance on selecting the most suitable aggregation methods for your specific monitoring needs.

**By choosing the appropriate aggregation method, you can ensure your Instana custom dashboards effectively communicate the underlying trends and patterns within your application and infrastructure performance data.**

For more details, see the [aggregation documentation](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/custom_dashboards/aggregation.html).

## Add a filter

Data rendered by widgets can be filtered on specific tags using the query builder.

The following widget is filtered on the Test application for service cart on the GET /card/:id endpoint and only for successful HTTP calls with a status of 200.

## Select a group

Depending on the type of widget, it may be possible to display groups.

After choosing a tag to group by, you can specify whether you want to show the top or bottom results in the chart. The groups are sorted by the metric and aggregation that are displayed on the chart. You may also choose to show the aggregation of all other groups (that are not part of the Top or Bottom groups) as a separate value on the chart. The other groups are also aggregated using this metric and aggregation.

**Note**
Grouping is disabled when configuring non-stacked charts or when configuring multiple metrics for one chart.

## Advanced Features

Instana's custom dashboards offer functionalities beyond basic data visualization, empowering you to personalize your experience, collaborate with colleagues, and manage your widgets efficiently.

**Personalization:**

-  **Set a Default Dashboard:** Designate a frequently used custom dashboard as your default, making it the first thing you see upon logging in.

**Sharing:**

-  **Public Dashboards:** Make your dashboard publicly accessible within your organization for anyone to view.
-  **Editor Access:** Grant specific users editor permissions, allowing them to modify and update the dashboard, fostering collaborative monitoring efforts.

**Widget Management:**

-  **Copy Widgets:** Easily duplicate individual widgets between different custom dashboards. Simply access the widget overflow menu and select "Copy."
-  **Copy All Widgets:** Quickly replicate all widgets from a single dashboard to another by using the "Copy All Widgets" option within the dashboard overflow menu.
- To paste your widgets, go to the target custom dashboard, and use the paste shortcut CTRL-V for Windows or CMD-V for Mac OS.

## Displaying a Custom Dashboard on a Big Screen or TV

Instana offers a TV Mode to optimize your custom dashboards for large-format displays like TVs. When enabled, this mode hides the main navigation and header, providing a clean and focused view of your chosen metrics.

Here's how to activate TV Mode:
1.  **Open the menu:** Locate the menu button near the "Add Widget" option on your custom dashboard.
1.  **Select TV Mode:** Choose "TV Mode" from the available options within the menu.

By following these steps, your dashboard will switch to TV Mode, presenting your data in a full-screen layout suitable for big screen viewing. This can be useful for sharing critical performance insights in conference rooms, operations centers, or other shared display environments.

## Custom dashboards API

You can use the [Web Rest API](https://www.ibm.com/links?url=https%3A%2F%2Finstana.github.io%2Fopenapi%2F%23tag%2FCustom-Dashboards) to manage custom dashboards. We recommend that you leverage the Edit as JSON feature found within our user interface to construct the desired request payloads. Specifically to help you build correct widget configurations and access rules