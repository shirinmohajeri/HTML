<h1>
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-html-48.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Logbot Custom Web Panel
</h1>

This document explains how to build **custom dashboards** using the **Logbot Custom Web Panel**.

It is designed for users who want to:
- Build dashboards using **HTML, CSS, and JavaScript**
- Use **dashboard template variables** (plants, gateways, devices)
- Read **tables, rows, and columns** returned by Logbot queries
- Access the **dashboard time range**
- Create custom layouts and visualizations beyond standard panels

---

<h1>
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-dashboard-100.png"
       height="40"
       style="vertical-align:center; margin-left:20px;">
  Creating a New Dashboard
</h1>

This section explains how to create a new dashboard and prepare it for using **Logbot Custom Web Panel** and **dashboard variables**.

### Step 1: Open Dashboards

1. From the left sidebar, click **Dashboards**.
2. Open the **Manage** section.

---

### Step 2: Create a New Dashboard

1. Click the **New Dashboard** button.
2. A new empty dashboard will be created and opened automatically.

---

### Step 3: Add a New Panel

1. Inside the new dashboard, click **Add Panel**.
2. When the panel dialog opens, select **Choose Visualization**.

---

### Step 4: Select Logbot Custom Web Panel

1. From the list of visualizations, select **Logbot Custom Web Panel**.
2. The panel editor will open with:

   * HTML Editor
   * CSS Editor
   * JavaScript Editor

This panel is used to render custom HTML content and access Logbot variables.

---

### Step 5: Open Dashboard Settings

1. In the top-right corner of the dashboard, click the **gear icon** (⚙️).
2. Select **Dashboard settings**.

---

### Step 6: Configure Dashboard Variables

1. In **Dashboard settings**, open the **Variables** tab.
2. Click **Add variable** to create dashboard variables such as:

   * `$plants`
   * `$gateways`
   * `$devices`

These variables will appear as dropdowns at the top of the dashboard and will be used by the Logbot Custom Web Panel to filter data dynamically.

3. After creating the variables, click **Save dashboard**.

---
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/Presentation.jpg"
       height="350"
       style="vertical-align:middle; margin-right:10px;">
<h1>
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-variable-48.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Template Variable Rendering (HTML)
</h1>

📌 **Purpose**

Verify how template variables are rendered inside the HTML editor panel.

<span style="color:#71B4B5;">**Steps:**</span>

1. Open the panel in edit mode.
2. Select **HTML Editor panel** as visualization.
3. Write the following code:
   ```html
   <div>
     Plant: <b>$plant</b><br>
     Gateway: <b>$gateway</b><br>
     Device: <b>$device</b>
   </div>

3. Save the panel.

✔️ Expected Result:

* Variable placeholders are rendered as plain text.
* No runtime replacement happens at this stage.

✔️ Actual Result:

<span style="color:#FF7F02;">🔑 **"$plant, $gateway, $device"**</span> are displayed as text.

 Notes:

* Template variables are not automatically resolved in HTML.
* Resolution depends on Logbot helpers or data queries.

---
<img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/Slide1.jpg"
  height="350"
  style="vertical-align: middle; margin-right: 10px;">


---
<h1>
      <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-variable-48.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Template Variables Autocomplete
</h1>
💫 Preconditions:

1. A dashboard panel is opened in Edit mode
2. Visualization is set to HTML Editor panel
3. Template variables (**Plants, Gateway, Device**) exist in the dashboard

✅ ️(values may be set to All)

#  Autocomplete Trigger (- logbot) 

<span style="color:#71B4B5;">**Steps:**</span>

1. Click inside the HTML Editor area.
2. Type:

   ```html
    **logbot**

3. Wait for the autocomplete dropdown to appear.

✔️ Expected Result

✅ An autocomplete dropdown is displayed.

💫 The list includes entries such as:

1. logbot-templateVariables
2. logbot-tables
3. logbot-timeRange
4. logbot-timeSeries


<h1>
        <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-variable-48.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Template Variables Autocomplete (logbot-templateVariables)
</h1>

📌 **Purpose** 

Verify that template variable helpers are suggested by autocomplete after selecting
<code>**logbot-templateVariables**</code>,
and that their properties
(<code>**name**</code>, <code>**label**</code>, <code>**value**</code>, <code>**text**</code>)
are discoverable.

💫 Preconditions:

1. A dashboard panel is open in Edit mode
2. Visualization is set to HTML Editor panel
3. Template variables exist in the dashboard:

               ☑️$plant ☑️$gateway ☑️ $device
        
<span style="color:#71B4B5;">**Steps:**</span>

1. Click inside the HTML Editor input area.
2. Type:

   ```html
     logbot
3. From the autocomplete list, select:
<span style="color:#027733;">
  ✔️ <code>logbot-templateVariables</code>
</span>

**An autocomplete dropdown is displayed with template variable helpers, such as:**

* `logbot-templateVariables-plants-(name, value, text, label)`
* `logbot-templateVariables-gateways-(name, value, text, label)`
* `logbot-templateVariables-devices-(name, value, text, label)`


## <span style="color:#FF7F02;">🔑 These entries indicate:</span>

* **Name**  → internal variable name
* **Label** → UI label shown in dropdown
* **Value** → selected value
* **Text**  → displayed text (if different from value)

<span style="color:#027733;">
  ✔️ <code>logbot-templateVariables</code>
</span>


**Entries are listed:**

- [ ] $plant
- [ ] $gateway
- [ ] $device

<h1>
   <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-variable-48.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  How Template Variables, Autocomplete, and Queries Work Together
</h1>


**Describe the relationship between template variables, autocomplete, and panel queries (A, B) prior to working with Tables or Time Series.**


## Simple Mental Model
```
Template Variables  →  Queries (A, B)  →  Tables / Time Series
(dashboard)            (panel)           (output)
```
**Each part has a different role.**

---

<h1>
   <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-variable-48.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Template Variables (Dashboard Level)
</h1>

Template variables are defined at the **dashboard level**.

They store user selections (for example:☑️ plant, ☑️  gateway, ☑️ device)

* They do **not** fetch data
* They do **not** have queries (A, B)
* They are used as **inputs** for queries

🔑 **In short:**
*Template variables = **filters / parameters***

---

<h1>
   <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-helper-96.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Autocomplete (Editor Help)
</h1>

Autocomplete helps users **see available options** while typing.

* It does **not** run queries
* It does **not** return data
* It only shows **what can be used** in the editor

Autocomplete depends on the **current panel configuration**.

---

## Queries (Panel Level)

Queries are defined **inside a panel** and are labeled:

* A
* B
* C
* …

Queries:

* Fetch real data
* Can return **Table** or **Time Series**
* Can use template variables as input
---
<h1>
   <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-time-limit-96.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Tables and Time Series
</h1>

Tables and Time Series are the **results of queries**.

* Tables show rows and columns
* Time Series show values over time
* They exist only if a query is configured

**How Variables Are Used (in This Test):**

* **Plants / Devices / Gateways** are **dashboard template variables**
* These variables are passed to the datasource as **scoped variables**
* When the user selects **All**, the variable value is sent as an **array** (multi-select)

### 🔑 Conceptual Model

* **Variables** → filters / parameters
* **Queries (A / B / C)** → data producers
* **Tables** → structured outputs consumed by `logbot-tables-*`

---

## <span style="color:#71B4B5;">**Steps**</span>

1. Open the panel → **Edit**

2. Set **Visualization** to **HTML Editor panel**

3. Configure panel queries:

   * **A** → Table → Metric `_plants`
   * **B** → Table → Metric `_gateways`
   * **C** → Table → Metric `_devices`
  
   <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/metric.jpg"
     height="150" weight="20">
4. In **HTML Editor**, add the required table helpers (A / B / C)
<img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/T1.jpg"
     height="150" weight="20">
     <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/tab.jpg"
     height="150" weight="20">

5. **Save** the panel
---
<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-note-100.png"
       height="36"
       style="vertical-align:middle; margin-right:10px;">
  Notes / Troubleshooting
</h2>

* If you see **`Unknown metric`**, the metric name is incorrect.

  * For Logbot JSON datasource system endpoints, use:

    * `_plants`
    * `_gateways`
    * `_devices`

* Template variables **do not generate tables by themselves**.

  * Tables exist **only if Query A / B / C returns a table output**.
  

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-variable-48.png"
       height="36"
       style="vertical-align:middle; margin-right:10px;">
  Table Rows Rendering + Variable Filtering (Plants / Gateways / Devices)
</h2>  
💫  Goal

**Verify that:**

* Table **rows** render correctly (not only table name/columns)
* Selecting dashboard variables (**Plants / gateways / devices**) changes the returned rows
* Multi-select (**All**) is handled as an **array** (scopedVars)

---

## 1) Preconditions

* Dashboard variables exist: **Plants**, **gateways**, **devices**
* Panel visualization: **HTML Editor panel**
* Queries exist:

  * **A** → Table → Metric `_plants`
  * **B** → Table → Metric `_gateways`
  * **C** → Table → Metric `_devices`

---

## 2) What to test:

1. Set all variables to **All**
2. Confirm A/B/C return **many rows**
3. Change **Plants** to a *single* plant (example: `Plant_1`)
4. Confirm:

   * Table A rows shrink to that plants
   * Table B/C rows also update (depending on datasource logic)
5. Change **gateways** to a single gateway
6. Change **devices** to a single device
7. Set one variable to **multi-select (2 values)** and confirm it still returns results
---

## 3) Expected Result

* `logbot-tables-table-rowCount` returns a number (not empty)
* `logbot-tables-table-row[0]` shows a real row string (not “Unknown metric”)
* Changing **Plants / gateways / devices** changes rowCount and visible rows

## If something fails (fast troubleshooting)

* If you see **Unknown metric** → query metric is wrong (must be `_plants/_gateways/_devices`)
* If `rowCount` is empty but name/columns work → datasource returns schema but not rows (filter/permissions/time range)
* If variables don’t affect rows → datasource may ignore scopedVars or variable name mismatch (`Plants` vs `plants`)

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h1>
   <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-time-limit-96.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Logbot Table Template Helpers
</h1> 

This section explains the **table helper variables** available in the HTML Editor when using **Logbot Tables**.

These helpers expose **query results (A / B / C)** as readable values for visualization and debugging.

---

## 1. Naming Convention

All table helpers follow this pattern:

```
logbot-tables-table-<ID>-<property>
```

Where:
<table class="parts-table">
  <thead>
    <tr>
      <th>Part</th>
      <th>Meaning</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>table</code></td>
      <td>Refers to a table query</td>
    </tr>
    <tr>
      <td><code>&lt;ID&gt;</code></td>
      <td>Query letter (<code>A</code>, <code>B</code>, <code>C</code>, …)</td>
    </tr>
    <tr>
      <td><code>&lt;property&gt;</code></td>
      <td>What you want to access (Name, Text, Label, Value, etc.)</td>
    </tr>
  </tbody>
</table>

---

## 2. Table-Level Helpers

These helpers describe the **table structure**, not the data itself.

### 🔹 Table name

```
logbot-tables-table-A-name
```
Returns:

* The internal table identifier
* Example: 

Returns:

```
table-A
```

---

### 🔹 Table columns

* Example:

```
logbot-tables-table-A-columns
```

Returns:

```
Plant Name, Description, Address
```

Useful for:

* Debugging schema
* Showing table metadata in documentation panels

---

## 3. Row-Level Helpers (Most Important)

These helpers expose **actual data rows**.

### 🔹 Single row (by index)

```
logbot-tables-table-A-row[0]
```

Returns:

* The **raw row string** at index `0`

Example:

```
logbot-plant, Logbot plant di ceccolin, Padua, Italy
```

---

### 🔹 Multiple rows

```
logbot-tables-table-A-row[1]
logbot-tables-table-A-row[2]
logbot-tables-table-A-row[3]
```

Notes:

* Index starts at `0`
* If index does not exist → returns empty or `N/A`

---

### 🔹 When variables change…

If the user changes dashboard variables (`plants`, `gateways`, `devices`):

* `rowCount` changes
* `row[x]` values change
* This confirms **row-level filtering works**

---

## 4. Relationship with Queries (A / B / C)

<table class="query-table">
  <thead>
    <tr>
      <th>Query</th>
      <th>Table helpers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>A</strong></td>
      <td><code>logbot-tables-table-A-</code></td>
    </tr>
    <tr>
      <td><strong>B</strong></td>
      <td><code>logbot-tables-table-B-</code></td>
    </tr>
    <tr>
      <td><strong>C</strong></td>
      <td><code>logbot-tables-table-C-</code></td>
    </tr>
  </tbody>
</table>

**Each query exposes its own independent table helpers.**

Example:

```
logbot-tables-table-B-row[0]
logbot-tables-table-A-row[0]-column[1]
```
---

## 5. Mental Model (For Users)

```
Dashboard variables
        ↓
Datasource filtering
        ↓
Query A / B / C
        ↓
logbot-tables-table-*-helpers
        ↓
HTML visualization
```
---

<h1>
   <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-helper-96.png"
       height="30"
       style="vertical-align:center; margin-left:10px;">
  Template variable helpers in HTML Editor
</h1>

Inside the HTML Editor panel, the current variable selections can be read using helper placeholders.

These helpers reflect the user’s current selection.

**Examples**

- `logbot-templateVariables-plants-value`
- `logbot-templateVariables-gateways-value`
- `logbot-templateVariables-devices-value`

Optional helpers (if configured):

- `logbot-templateVariables-<variable>-text`
- `logbot-templateVariables-<variable>-label`

These helpers update automatically when the user changes the dashboard dropdowns.

---

##  Table helpers used in this test

The panel contains three table queries:

- **Query A** → `_plants`
- **Query B** → `_gateways`
- **Query C** → `_devices`

Each query returns a table that can be accessed using table helpers.
The panel contains three table queries, so Logbot exposes three independent helper namespaces:

- **Query A** → logbot-tables-table-A

- **Query B** → logbot-tables-table-B

- **Query C** → logbot-tables-table-C

Each namespace provides:

- **Table-level** helpers (metadata: name, columns, row count)

- **Row-level** helpers (actual returned rows)

- **Column helpers** (column metadata and indexed access)

---

### - Table-level helpers

These helpers describe the structure of the returned table.

**Examples (Table A)**

- `logbot-tables-table-A-name`  
  Returns the internal table name.

- `logbot-tables-table-A-columns`  
  Returns a list of column names.

- `logbot-tables-table-A-row[0]-column[0]`  
  Returns the number of rows and Columns returned by the query.

The same helper pattern applies to Table B and Table C.

---

## - Variable Format

Table helpers follow a predictable format based on the **query letter** (A/B/C) and the **value you want to read**.

**Pattern**

`logbot-tables-table-<ID>-<property>`

**Where**

* `<ID>` is the query letter: `A`, `B`, or `C`
* `<property>` is the value you want to read (for example `name`, `columns`, `rowCount`)

**Example**

`logbot-tables-table-A-row[0]colum[0]

This prints the number of rows returned by **Query A**.

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/Slide2.1.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>  

---
## Table-level helpers

Use table-level helpers when you need **metadata about the whole table** returned by a query (A / B / C).  
These helpers do **not** return a specific row value (for example, a plant name from one row).

---

### Where to write

Open your panel → **Visualization: Logbot Custom Web Panel** → use:

- **HTML Editor** (paste the helper strings here)
- **CSS Editor** (optional styling for screenshots)
- **JavaScript Editor** (not needed in this section)

---

## Table name

### Helper
- `logbot-tables-table-A-name`
- `logbot-tables-table-B-name`
- `logbot-tables-table-C-name`

### Quick test (HTML Editor)

```html
<div>Table A name: <b>logbot-tables-table-A-name</b></div>
<div>Table B name: <b>logbot-tables-table-B-name</b></div>
<div>Table C name: <b>logbot-tables-table-C-name</b></div>
```
---
## Row helpers

Row helpers let you print the **full row**, usually as a comma-separated string.

### Read a row by index

**Helper**

* `logbot-tables-table-A-row[<rowIndex>]`

**Examples**

* `logbot-tables-table-A-row[0]`
* `logbot-tables-table-A-row[1]`

**Quick test**

```html
<div>Row #0: <b>logbot-tables-table-A-row[0]</b></div>
<div>Row #1: <b>logbot-tables-table-A-row[1]</b></div>
```

**Expected output**

* A readable row string for each index that exists.
* If the index is out of range, it may render empty / `N/A` depending on data availability.

---

## Cell helpers (row + column by index)

Use this when you need a **single value** from a row.

**Helper**

* `logbot-tables-table-A-row[<rowIndex>]-column[<columnIndex>]`

**Examples**

* `logbot-tables-table-A-row[0]-column[0]`
* `logbot-tables-table-A-row[0]-column[2]`

**Quick test**

```html
<div>
  Row #0 / Col #0: <b>logbot-tables-table-A-row[0]-column[0]</b><br/>
  Row #0 / Col #1: <b>logbot-tables-table-A-row[0]-column[1]</b>
</div>
```
---

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/tableVarib.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>  

## Column helpers (column metadata)

Column helpers describe the returned columns (name/type).
Autocomplete is the easiest way to discover the exact column keys.

### Column name

**Helper**

* `logbot-tables-table-A-column-<ColumnKey>-name`

**Example**

* `logbot-tables-table-A-column-Plant_Name-name`

**What it returns**

* The column display name.

---

### Column type

**Helper**

* `logbot-tables-table-A-column-<ColumnKey>-type`

**Example**

* `logbot-tables-table-A-column-Plant_Name-type`

**What it returns**

* The column type.


<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/Columntype.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>  

* Row count changes when you change variables.
* First row changes accordingly.

---
## Column helpers: **Column metadata (name + type)**

Column helpers let you read **metadata about a single column** inside a query result table (Table A / B / C).
Metadata means: *“what the column is”*, not *the row data inside the column*.

You typically use these helpers when you want to:

* verify which columns are available,
* print a column label,
* check the column data type,
* debug a query result.

---

### Helper naming pattern

Use this pattern:

```
logbot-tables-table-<TABLE_ID>-column-<COLUMN_NAME>-<PROPERTY>
```

Where:

* `<TABLE_ID>` is the query letter: `A`, `B`, or `C`
* `<COLUMN_NAME>` is the exact column name (example: `Plant_Name`, `Address`, `Description`)
* `<PROPERTY>` tells what you want from that column

---

## A) Column **name**

### What it does

Returns the **display name** of the column (the column title).
Example: if the column is `Plant_Name`, it returns something like:

* `Plant Name` (or the platform’s label for that field)

### Helper syntax

```
logbot-tables-table-A-column-Plant_Name-name
```

### What you should expect
* <span style="color:gray;">**A**</span> text value
* Not empty **if the table exists and contains that column**

**Expected output**
* <span style="color:gray;">**A**</span> readable column name, for example: `Plant Name`
---

## B) Column **type**

### What it does

Returns the **data type** of the column (metadata type, not the value).
Examples:

* `string`
* `number`
* `boolean`
* `timestamp`

### Helper syntax

```
logbot-tables-table-A-column-Plant_Name-type
```

### What you should expect

*  <span style="color:gray;">**A**</span> **type string**
* Not empty **if the column exists**


<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-test-96.png"
       height="30"
       style="vertical-align:middle; margin-right:10px;">
       Quick test (HTML Editor)
</h2>

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/CL.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>  

## Common reasons it returns nothing (empty)

If you see empty output, usually one of these is true:
1. **The query for Table  <span style="color:gray;">**A****</span>  returns no data / no schema**

   * Example: query is not configured or returns error

2. **The column name is not exact**

   * `Plant_Name` must match exactly (including `_` and case)

3. **You are using the wrong table ID**

   * Column exists in B, but you’re calling `table-A`

4. **The table doesn’t contain that column**

   * Example: `Address` is not part of Table A in your query result

---
##  Column helpers: **Reference ID (refId)**

### What is `refId`?

`refId` stands for **Reference ID**.

It is the identifier of a **query**, not of a column value.

Each query in a dashboard has a unique `refId`:

* Query A → `A`
* Query B → `B`
* Query C → `C`

---

### Important note

Columns **do not normally expose a `refId`**.

For this reason, using `refId` at column level often returns **no value**, and this is **expected behavior**.

---

### What does column `refId` return?

* In most datasources: **nothing (empty output)**
* This is **not an error**
* It simply means the column does not have its own reference ID

---

### When should `refId` be used?

`refId` is useful when:

* You need to know **which query produced a table**
* You are debugging dashboards with **multiple queries**
* You are writing **advanced JavaScript logic**

It is **not required** for normal data visualization.

---

### Example (HTML Editor)

```html
<div>
  Column refId:
  <b>logbot-tables-table-A-column-Plant_Name-refId</b>
</div>
```

---

### Expected output

```text
(empty)
```

This is the **correct and expected result**.

---

### Why is the output empty?

Because:

* `refId` belongs to the **query**
* Columns do not carry their own `refId`

```html
<div>
  Table refId:
  <b>logbot-tables-table-A-refId</b>
</div>
```

#### Expected output

```text
A
```
<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/refid.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>  

---
## Column `type`

### What is `type`?

`type` tells you the **data type of a column** returned by the query (for example: text and number).
This is useful when you want to format values or decide how to handle them in JavaScript.

---

### Helper pattern

```text
logbot-tables-table-{ID}-column-{ColumnName}-type
```

Example (Table A, column `Plant_Name`):

```text
logbot-tables-table-A-column-Plant_Name-type
```

---

### What it returns

A short text value like:

* `string` (text values)
* `number` (numeric values)
* sometimes other types depending on datasource/query

> If your column type is not recognized, you may see an empty value. That usually means the datasource is not providing a type.

---

### Quick test (HTML Editor)

```html
<div style="margin-bottom:8px;">
  Column type (Plant_Name):
  <b>logbot-tables-table-A-column-Plant_Name-type</b>
</div>

<div>
  Column type (Address):
  <b>logbot-tables-table-A-column-Address-type</b>
</div>
```

---

### Expected output

You should see something like:

```text
Column type (Plant_Name): string
Column type (Address): string
```

If you test a numeric column (example: temperature, power, etc.), you will likely get:

```text
Number
```
---

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/type2.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>  
---

## Column `rows` (values from one column)


This helper is used when you want to read **cell values** from the query result table (not metadata).

### 🙎  How it works (Row + Column indexing)

When Logbot runs your queries, each query returns a **table**:

* **Table A** = result of Query A
* **Table B** = result of Query B
* **Table C** = result of Query C

Each table contains:

* **Rows** = records returned by the query (0-based index)
* **Columns** = fields inside each row (0-based index)

✅ The syntax to read a single cell is:

```text
logbot-tables-table-<ID>-row[<rowIndex>]-column[<columnIndex>]
```

Where:

* `<ID>` is `A` / `B` / `C`
* `row[0]` = first row, `row[1]` = second row, etc.
* `column[0]` = first column, `column[1]` = second column, etc.

### Important notes

* Indices are **0-based** (start from 0).
* If the query returns **only 1 row**, then `row[1]` will be empty.
* The **order of columns** depends on your query output (the same order you see in the table result).
* This helper returns the **actual value in the cell** (example: `logbot-plant`, `warehouse`, an address, etc.).

---

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/Rowandcol.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>

### What you should see

* `Plant Name1` shows the first plant name (row 0, col 0)
* `Plant Name2` shows the second plant name (row 1, col 0)

If you only have 1 plant returned by Query A, then `Plant Name2` will be empty.

---

### Meaning of the mapping (based on your table)

* `column[0]` → Name
* `column[1]` → Description
* `column[2]` → Address

---
## Template variables (Dashboard variables)

Template variables come from the **dashboard variable dropdowns** (top of the dashboard).
Example dropdowns:

* `plants`
* `gateways`
* `devices`

These helpers let you read what the user selected.

---

## Template variable helper format

```text
logbot-templateVariables-<variableName>-<property>
```

Where:

* `<variableName>` = your variable name (example: `plants`)
* `<property>` = one of:

  * `label`
  * `name`
  * `text`
  * `value`

---

## What each property returns

Assume the user selected **logbot-plant** in the `plants` dropdown:

<table class="custom-table">
  <thead>
    <tr>
      <th>Helper</th>
      <th>Returns</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>logbot-templateVariables-plants-name</code></td>
      <td><code>plants</code></td>
    </tr>
    <tr>
      <td><code>logbot-templateVariables-plants-value</code></td>
      <td>the real selected value (example: <code>logbot-plant</code>)</td>
    </tr>
    <tr>
      <td><code>logbot-templateVariables-plants-text</code></td>
      <td>display text (often same as value)</td>
    </tr>
    <tr>
      <td><code>logbot-templateVariables-plants-label</code></td>
      <td>may be empty / undefined depending on variable config</td>
    </tr>
  </tbody>
</table>

---

## Quick test (HTML Editor)

```html
<div class="lb-card">
  <div class="lb-title">Selected Plant</div>

  <div class="lb-row">
    <span class="lb-label">Label:</span>
    <span class="lb-value">logbot-templateVariables-plants-label</span>
  </div>

  <div class="lb-row">
    <span class="lb-label">Name:</span>
    <span class="lb-value">logbot-templateVariables-plants-name</span>
  </div>

  <div class="lb-row">
    <span class="lb-label">Text:</span>
    <span class="lb-value">logbot-templateVariables-plants-text</span>
  </div>

  <div class="lb-row">
    <span class="lb-label">Value:</span>
    <span class="lb-value">logbot-templateVariables-plants-value</span>
  </div>
</div>
```
<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/property.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/icons8-time-machine-96.png
"
height="30"
       style="vertical-align:middle; margin-right:10px;">
       Time range helpers
</h2>


Time range helpers read the selected time range from the dashboard time picker (example: **Last 6 hours**).

These are useful when you want to show or debug the time window used by queries.

---

## Helpers

```text
logbot-timeRange-from
logbot-timeRange-to
logbot-timeRange-raw
```

What they return:

* `from` → formatted start time
* `to` → formatted end time
* `raw` → raw object (sometimes prints `[object Object]` in HTML)

---

## Quick test (HTML Editor)

```html
<div class="lb-card">
  <div class="lb-title"> Time range </div>

  <div class="lb-row">
    <span class="lb-label">From:</span>
    <span class="lb-value">logbot-timeRange-from</span>
  </div>

  <div class="lb-row">
    <span class="lb-label">To:</span>
    <span class="lb-value">logbot-timeRange-to</span>
  </div>

  <div class="lb-row">
    <span class="lb-label">Raw:</span>
    <span class="lb-value">logbot-timeRange-raw</span>
  </div>
</div>
```

Expected output:

* `From` and `To` should show readable timestamps
* `Raw` may display `[object Object]` (normal when rendered directly)

---

<h2 align="center">
  <img src="https://git.logbotiot.cloud/s.mohajeri/html-plugin/-/raw/main/HTML%20plugin/timerange.jpg"
       height="250" weight="250"
       style="vertical-align:middle; margin-right:10px;">
</h2>
