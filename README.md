# 🛡️ Security Incident Dashboard (Power BI)

An interactive Power BI report that simulates a mini Security Operations Center (SOC) view of cybersecurity incidents from January to May.

![Dashboard preview](preview.png)

## What it shows
- **Total, open and critical incidents** at a glance
- **Average resolution time** in hours
- **Threat Level** indicator (Normal / Elevated / High Alert) driven by a DAX measure
- **Attack types** (phishing, malware, ransomware, DDoS, password attacks, insider threats)
- **Monthly trend** broken down by severity
- **Incidents by department**
- **Slicers** to filter by severity and status

## Built with
- Power BI Desktop
- Power Query (M) to create the dataset
- DAX measures: Total Incidents, Critical Incidents, Open Incidents, Avg Resolution Hrs, Threat Level

## Key DAX measures
```dax
Total Incidents = COUNTROWS(SecurityIncidents)

Critical Incidents =
CALCULATE([Total Incidents], SecurityIncidents[Severity] = "Critical")

Open Incidents =
CALCULATE([Total Incidents], SecurityIncidents[Status] <> "Resolved")

Threat Level =
IF([Critical Incidents] >= 3, "🔴 HIGH ALERT",
IF([Critical Incidents] >= 1, "🟠 ELEVATED", "🟢 NORMAL"))
```

## How to use
1. Download `Security Dashboard.pbix`
2. Open it in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
3. Click items in the slicers to explore the data

## Note
The data is fictional and was created for learning and portfolio purposes.
