### Step 1: Chart Events by Day

Run the following query to group events by day and count them:

```
index=main sourcetype=web_traffic | timechart span=1d count
```

- This produces a daily count of all `web_traffic` events.
- The results highlight which days had unusually high log volumes.
![[Pasted image 20251208154213.png]]
---

### Step 2: Use the Visualization Tab

- Switch to the **Visualization** tab to see the results as a graph.
- The chart makes spikes in activity easier to spot compared to raw numbers.
![[Pasted image 20251208154218.png]]
---

### Step 3: Sort Results in Descending Order

To quickly identify the busiest day, append `sort` and `reverse`:

```
index=main sourcetype=web_traffic | timechart span=1d count | sort by count | reverse
```

- This reorders the output so the day with the **maximum events appears first**.
- Useful for triage when you want to immediately focus on the attack window.
![[Pasted image 20251208154222.png]]
---

### Step 4: Key Observation

The timeline reveals a **clear period of intense activity** — the attack phase attributed to _King Malhare_. This spike marks the critical window for deeper investigation into suspicious IPs, user agents, and paths.