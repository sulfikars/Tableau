# Sales Comparison Based on Region Dashboard

## Overview

This project addresses a key request from the director of a leading organization: to **compare sales performance between two specific regions**. Regional operators have meticulously recorded sales data, and the upper management's goal is to visualize this data through an interactive dashboard to understand regional performance disparities and identify areas for improvement.

## Objective

The primary objective of this Tableau project is to **provide a clear and insightful dashboard** that facilitates the comparison of sales metrics between two user-selected regions. This visualization aims to empower the organization to make data-driven decisions and suggest necessary improvements in underperforming areas or replicate successes from high-performing regions.

-----

## Tableau Project Details

### Data Source

  * **Dataset:** Sample Superstore
  * **Sheet Used:** Orders

### Key Steps Performed

1.  **Data Organization:**

      * To enhance data readability and management, a folder named **'Customer and Order Details'** was created.
      * This folder segregates `Customer Name` and `Order ID` from the `Orders` sheet, ensuring a more organized data pane in Tableau.

2.  **Hierarchy Creation:**

      * A **'Location' hierarchy** was established, including relevant geographical fields, with `Country` as the top level. This allows for drill-down analysis of sales data by location.

3.  **Parameter Creation for Region Selection:**

      * Two critical parameters, **'Primary Region'** and **'Secondary Region'**, were created. Both parameters list all available regions, enabling users to dynamically select the two regions they wish to compare.
      * Corresponding **calculated fields** were created for both 'Primary Region' and 'Secondary Region' to filter and display data based on the parameter selections.

4.  **Key Performance Indicator (KPI) Calculations:**

      * Several calculated fields were developed to derive essential sales metrics for comparison:
          * **First Order Date:** Identifies the earliest order date within the selected regions.
            ```
            {FIXED [Region]: MIN([Order Date])}
            ```
          * **Total Sales:** Aggregates the total sales for the selected regions.
            ```
            IF [Region] = [Primary Region Parameter] THEN [Sales]
            ELSEIF [Region] = [Secondary Region Parameter] THEN [Sales]
            END
            ```
          * **Average Sales per Order:** Calculates the average sales amount per order.
            ```
            [Total Sales] / [Number of Orders]
            ```
          * **No. of Customers:** Counts the distinct number of customers.
            ```
            COUNTD(IF [Region] = [Primary Region Parameter] THEN [Customer Name]
            ELSEIF [Region] = [Secondary Region Parameter] THEN [Customer Name]
            END)
            ```
          * **No. of Orders:** Counts the distinct number of orders.
            ```
            COUNTD(IF [Region] = [Primary Region Parameter] THEN [Order ID]
            ELSEIF [Region] = [Secondary Region Parameter] THEN [Order ID]
            END)
            ```
          * **No. of Products in Sale:** Determines the distinct number of products sold.
            ```
            COUNTD(IF [Region] = [Primary Region Parameter] THEN [Product Name]
            ELSEIF [Region] = [Secondary Region Parameter] THEN [Product Name]
            END)
            ```

5.  **Dashboard Design and Alignment:**

      * A new dashboard was created to house all the visualizations.
      * All individual sheets (visualizing the calculated KPIs) were carefully **aligned and arranged** to provide a clear and intuitive side-by-side comparison of the 'Primary Region' and 'Secondary Region'.
      * Extensive **formatting** (colors, shading, fonts, borders) was applied to enhance readability and visual appeal, adhering to a consistent design.

### Dashboard Contents

The dashboard is partitioned to prominently display the following details for both the **Primary Region** and the **Secondary Region**:

  * **First Order Date**
  * **Total Sales**
  * **Average Sales per Order**
  * **No. of Customers**
  * **No. of Orders**
  * **No. of Products in Sale**

-----

## Access the Dashboard

You can access the live Tableau Public dashboard for this project by clicking here: [Tableau Public Dashboard Link](https://public.tableau.com/app/profile/sulfikar.shajimon/viz/FinalProject_17202047013560/Dashboard1)

-----

## How to Use the Dashboard

1.  **Select Regions:** Use the 'Primary Region' and 'Secondary Region' parameters at the top of the dashboard to choose the two regions you wish to compare.
2.  **Analyze Metrics:** Observe the key performance indicators (Total Sales, Average Sales per Order, etc.) for each selected region displayed side-by-side.
3.  **Identify Insights:** Leverage the visual comparisons to identify trends, disparities, and areas for potential improvement or further investigation within the organization's sales performance.

-----
