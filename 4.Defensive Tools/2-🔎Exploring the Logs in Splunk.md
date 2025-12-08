In this Splunk instance, the data has already been ingested so we can begin investigating the incident.

### Step 1: Access Search & Reporting

- On the Splunk interface, click **Search & Reporting** in the left panel.
- This will open the search workspace.
![[Pasted image 20251208153317.png]]

### Step 2: Run the Initial Query

- In the search bar, type:
    
    ```
    index=main
    ```
    
- Change the time frame (top-right dropdown) to **All time** to ensure all logs are included.
![[Pasted image 20251208153330.png]]

### Step 3: Review the Results

- After running the query, Splunk will display the ingested datasets.
- To verify, click on the **sourcetype** field in the left-hand fields list.
![[Pasted image 20251208153338.png]]

### Step 4: Identify the Datasets

Splunk shows two main sources of data:

- **web_traffic** → Events related to web connections to and from the web server.
- **firewall_logs** → Firewall activity, showing allowed and blocked traffic.
    - Note: The web server’s local IP is **10.10.1.15**.