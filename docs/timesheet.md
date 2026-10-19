# Frappe Timesheet Documentation

The **Timesheet** DocType in Frappe (ERPNext) tracks time spent by employees or contractors on specific activities, projects, and tasks. It serves as a foundation for both client billing and employee payroll.

---

## 1. Overview & Key Capabilities

* **Time Tracking:** Log exact start/end times or manual durations for any work activity.
* **Project Tracking:** Link time spent directly to internal or client-facing Projects and Tasks.
* **Client Billing:** Automatically calculate invoice amounts based on predefined activity rates.
* **Payroll Integration:** Compute hourly wages or overtime directly from submitted timesheets.

---

## 2. DocType Structure & Key Fields

### Main Document (Header)
* **Employee:** The individual executing and logging the work.
* **Company:** The organizational entity under which the work is registered.
* **Status:** Tracks the workflow state (`Draft`, `Submitted`, `Billed`).
* **Total Hours:** Automatically aggregated sum of all rows in the detail table.

### Timesheet Detail (Child Table)
Each Timesheet contains one or more rows in the time tracking table:
* **Activity Type:** Categorization of work (e.g., *Execution*, *Planning*, *Research*).
* **From Time / To Time:** Datetime stamps defining the exact work window.
* **Hours:** Automatically calculated duration based on the timestamps.
* **Is Billable:** Checkbox to determine if hours should be charged to a client.
* **Project / Task:** Relational links to track progress on specific goals.

---

## 3. Workflow & Usage

### Creating a Manual Entry
1. Navigate to **Timesheet List** and click **Add Timesheet**.
2. Select the **Employee** and **Company**.
3. In the **Time Logs** table, add a row and choose an **Activity Type**.
4. Set the **From Time** and **To Time**. 
5. Save and **Submit** the document.

### Using the Live Timer Feature
1. Open a new or existing draft **Timesheet**.
2. Click the **Start Timer** button in the top right.
3. In the prompt modal, select your **Activity Type**, **Project**, and **Task**.
4. Click **Start** to begin tracking.
5. Click **Complete** when the task is done to automatically inject the row into your table.

---

## 4. Downstream Integrations

### Sales Invoice (Client Billing)
* When creating a **Sales Invoice**, click **Get Items From** > **Timesheet**.
* Select the billable timesheets to pull line items and calculate costs based on the activity rate.

### Salary Slip (Payroll)
* In the **Salary Structure**, enable the **Salary Slip Based on Timesheet** checkbox.
* Specify the **Hour Rate** component.
* Creating a **Payroll Entry** will automatically pull approved timesheet hours for processing wages.
