# supply-chain-analytics
Power BI Supply Chain dashboard analyzing 11,257+ records across 8 datasets | Delivery Rate · Supplier KPIs · Warehouse Inventory · Transportation | Power Query · DAX · Custom Theme
# 🔗 Supply Chain & Logistics Analytics — Power BI Portfolio Project

## 📌 Project Overview
A full end-to-end Supply Chain analytics project built with **Power Query** and **Power BI**, covering order fulfillment, supplier performance, transportation tracking, and warehouse inventory across 8 real-world datasets with 11,257+ rows of data.

---

## 📂 Datasets Used

| Table | Rows | Description |
|-------|------|-------------|
| Customer Sales Orders | 5,000 | Sales orders and products |
| Fulfillment Status | 2,500 | Order fulfillment tracking |
| Purchase Orders | 1,200 | Procurement transactions |
| Shipment Tracking | 1,500 | Transportation and delivery |
| Supplier Performance | 4 | Supplier KPI scores |
| Supplier Master | 10 | Supplier reference data |
| Warehouse Inventory | 500 | Stock levels by warehouse |
| Warehouse Master | 3 | Warehouse reference data |

**Total: 11,257+ rows of Supply Chain data**

---

## 🔧 Tools & Skills

- **Power Query** — Multi-sheet Excel import, data cleaning, custom columns
- **Power BI** — Star Schema modeling, DAX measures, interactive dashboards
- **Custom Theme** — JSON-based theme for professional Supply Chain styling
- **DAX** — CALCULATE, COUNTROWS, SUM, AVERAGE, DIVIDE
- **Supply Chain KPIs** — Delivery Rate, Lead Time, On-Time Rate, Quality Score

---

## 🧹 Data Cleaning (Power Query)

- Imported 8 tables from multi-sheet Excel files
- Changed data types (Date, Whole Number, Decimal)
- Applied Text.Trim to all text columns
- Replaced null values with "Unknown"
- Removed errors with Remove Rows → Remove Errors
- Fixed DateTime vs Date mismatch using "Using Locale" conversion
- Added calculated columns:

**Customer Sales Orders:**
- `Order Value Band` = Small / Medium / Large / Bulk

**Fulfillment Status:**
- `Fulfillment Label` = ✅ Fulfilled / ⏳ Pending / ❌ Cancelled / ⚠️ Unknown

**Shipment Tracking:**
- `Shipment Status Label` = ✅ Delivered / 🚚 In Transit / ⏳ Processing

**Purchase Orders:**
- `Lead Time Days` = ExpectedDeliveryDate - OrderDate
- `Cost Band` = Low / Medium / High

**Supplier Performance:**
- `Quality Label` = Excellent / Good / Average / Poor

---

## 🗂️ Data Model — Star Schema

**Date Table:** 2020–2026

**Relationships via Date:**
- Date → Customer Sales Orders (OrderDate)
- Date → Fulfillment Status (via Customer Sales Orders)
- Date → Shipment Tracking (ShipDate)
- Date → Purchase Orders (OrderDate)

**Relationships via Keys:**
- Customer Sales Orders → Fulfillment Status (SalesOrderID)
- Supplier Master → Purchase Orders (SupplierID)
- Supplier Master → Supplier Performance (SupplierID)
- Warehouse Master → Warehouse Inventory (WarehouseID)
- Warehouse Master → Shipment Tracking (OriginWarehouseID)

---

## 📊 DAX Measures

```dax
Total Orders      = COUNTROWS('Customer Sales Orders')
Total Quantity    = SUM('Customer Sales Orders'[Quantity])
Delivery Rate     = Fulfilled / Total Fulfillment * 100
Cancelled Rate    = Cancelled / Total Fulfillment * 100
Total PO Cost     = SUM('Purchase Orders'[TotalCost])
Avg Lead Time     = AVERAGE('Purchase Orders'[Lead Time Days])
Avg Quality Score = AVERAGE('Supplier Performance'[QualityScore])
Avg On Time Rate  = AVERAGE('Supplier Performance'[OnTimeDeliveryRate]) * 100
Total Shipments   = COUNTROWS('Shipment Tracking')
Total Stock       = SUM('Warehouse Inventory'[QuantityOnHand])
Total Materials   = COUNTROWS('Warehouse Inventory')
```

---

## 📈 Dashboards

### 1️⃣ Supply Chain Overview
- KPI Cards: Total Orders · Total Quantity · Delivery Rate · Total PO Cost
- Orders Trend by Month (Line Chart)
- Fulfillment Status Distribution (Pie Chart)
- Order Value Band (Bar Chart)
- Top Products by Quantity (Bar Chart)
- Year Slicer

### 2️⃣ Supplier & Procurement
- KPI Cards: Total PO Cost · Avg Lead Time · Avg Quality Score · Avg On Time Rate
- PO Cost by Supplier (Bar Chart)
- Quality Score by Supplier (Bar Chart)
- Lead Time by Supplier (Bar Chart)
- Cost Band Distribution (Pie Chart)
- Supplier Slicer

### 3️⃣ Transportation & Delivery
- KPI Card: Total Shipments
- Shipments by Status (Pie Chart)
- Shipments by Carrier (Bar Chart)
- Shipments by Warehouse (Bar Chart)
- Shipments Trend by Month (Line Chart)
- Shipment Status Slicer

### 4️⃣ Warehouse & Inventory
- KPI Cards: Total Stock · Total Materials
- Stock by Warehouse (Bar Chart)
- Stock by Material (Bar Chart)
- Inventory by Warehouse (Bar Chart)
- Warehouse Location Slicer

---

## 💡 Key Business Insights

1. **Delivery Rate is 96.56%** — near-perfect fulfillment performance, indicating a highly reliable supply chain operation.

2. **Carriers are evenly balanced** — Carrier 01 and Carrier 03 handle approximately equal shipment volumes (~10 each), suggesting no single carrier dependency risk.

3. **Berlin is the largest warehouse** — handling the highest stock volume across all warehouse locations.

4. **Unknown supplier accounts for 29.65% of spend** — a significant data quality issue requiring supplier master data cleanup to ensure accurate procurement reporting.

5. **SUP-03 is the largest identified supplier** at 28.26% of spend — critical vendor requiring close relationship management.

6. **Medium orders dominate** — the majority of sales orders fall in the Medium value band, suggesting a consistent mid-market customer base.

---

## 🧠 Lessons Learned

- Multi-sheet Excel files require careful sheet selection during import in Power Query.
- DateTime vs Date type mismatch between fact tables and Date Table causes (Blank) in visuals — solved using "Using Locale" conversion.
- Fulfillment Status has no date column — connected via SalesOrderID to Customer Sales Orders instead of Date Table directly.
- Canvas Background in Power BI must be set manually per page — Themes only affect chart colors.
- Custom JSON Themes provide consistent color palette across all visuals.
- "Unknown" values in supplier data highlight the importance of master data governance in real supply chain systems.

---

## 👤 Author
**AbdelHassib Essayad**
Data Management Analyst & Accounting Specialist | 15+ Years Experience
Power BI · Power Query · DAX · Supply Chain Analytics

🔗 [GitHub Portfolio](https://github.com/hassib-essayad)
📧 essayad@gmail.com
