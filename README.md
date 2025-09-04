# Jira-Graphana-Integration

### Step 1: Install the Infinity Data Source Plugin

First, you need to add the plugin to your Grafana instance. You can do this using the Grafana CLI.

1.  Open your command line interface.
2.  Run the following command: `grafana-cli plugins install yesoreyeram-infinity-datasource`
3.  After the installation is complete, **restart your Grafana server** to ensure the new plugin is loaded.

### Step 2: Configure the Data Source

Once the plugin is installed, you'll configure it to connect to your Jira instance.

1.  Log in to your Grafana dashboard.
2.  In the left-hand navigation menu, go to **Connections** > **Data sources**.
3.  Click **Add new data source**. 
4.  Search for and select **Infinity**.
5.  Give your data source a name, for example, "Jira Data."
6.  In the **URL** field, enter your Jira instance URL (e.g., `https://your-company.atlassian.net`).
7.  In the **Authentication** section, choose **Basic Auth**.
8.  Enter your Jira email address as the username and your Jira API token as the password.
9.  Click **Save & Test**. You should see a "Data source is working" message.

### Step 3: Create a Dashboard Panel

Now you're ready to create a panel and query the Jira API.

1.  Create a new dashboard or open an existing one.
2.  Add a new panel and select the **Jira Data** source you just created.
3.  In the Query Editor, set the **Type** to **JSON**.
4.  Set the **Parser** to **Backend JSONata**.
5.  Choose a **Format** (e.g., `Table` or `Time series`) depending on what you're trying to display.
6.  Construct your query using a Jira REST API endpoint and JQL in the `URL` field. You will likely use the `/rest/api/3/search` endpoint. For example, to get all open issues, your URL would be `https://your-company.atlassian.net/rest/api/3/search?jql=statusCategory%20in%20('To%20Do',%20'In%20Progress')`.
7.  Use the JSONata parser to select the specific data fields you need from the JSON response, like `total` or individual issue details.

### Step 4: Build Queries for Your Specific Needs

* **Total Projects:** Query the `/rest/api/3/project/search` endpoint.
* **Total Open Issues/Tasks:** Query the `/rest/api/3/search` endpoint and use JQL to filter by issue type and status.
* **Per-Project Breakdowns:** Use Grafana's template variables to dynamically query each project, as discussed previously.

You can learn more about how to set up the Infinity plugin with JSON data by watching [this video on the Grafana Infinity Data Source Plugin](https://www.youtube.com/watch?v=BxWw4BWY5ns).
http://googleusercontent.com/youtube_content/2
