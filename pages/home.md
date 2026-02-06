---
name: Home
assetId: 7d62a7ae-504c-4c12-a4c3-71e0dcb8de20
type: page
---

# 📊 Demo Sales Report

{% big_value
  data="demo_daily_orders"
  value="sum(total_sales)"
  fmt="usd1m"
  title="Total Revenue"
  date_range={
    date="date"
    range="last 12 months"
  }
  comparison={
    compare_vs="prior year"
  }
/%}

{% big_value
  data="demo_daily_orders"
  value="sum(transactions)"
  fmt="#,##0"
  title="Total Transactions"
  date_range={
    date="date"
    range="last 12 months"
  }
  comparison={
    compare_vs="prior year"
  }
/%}

{% big_value
  data="demo_daily_orders"
  value="sum(total_sales) / sum(transactions) as avg_order_value"
  fmt="usd2"
  title="Avg Order Value"
  date_range={
    date="date"
    range="last 12 months"
  }
  comparison={
    compare_vs="prior year"
  }
/%}

## Monthly Sales Trend

{% line_chart
    data="demo_daily_orders"
    x="date"
    y="sum(total_sales)"
    y_fmt="usd"
    series="category"
    date_grain="month"
    title="Revenue by Category"
    subtitle="Monthly sales performance by product category"
/%}

## Sales by Category

{% bar_chart
    data="demo_daily_orders"
    x="category"
    y="sum(total_sales)"
    y_fmt="usd"
    order="sum(total_sales) desc"
    title="Total Revenue by Category"
/%}

## Sales by Channel

{% bar_chart
    data="demo_order_headers"
    x="sales_channel"
    y="count(*) as orders"
    order="count(*) desc"
    title="Orders by Sales Channel"
/%}

## Category Performance Detail

{% table
  data="demo_daily_orders"
%}
  {% dimension
    value="category"
  /%}
  {% measure
    value="sum(total_sales)"
    fmt="usd1m"
    title="Revenue"
    viz="bar"
  /%}
  {% measure
    value="sum(transactions)"
    fmt="#,##0"
    title="Transactions"
  /%}
  {% measure
    value="sum(total_sales) / sum(transactions) as avg_price"
    fmt="usd2"
    title="Avg Order Value"
  /%}
  {% measure
    value="sum(total_sales)"
    fmt="usd1m"
    title="Revenue Trend"
    viz="sparkline"
    sparkline_options={
      x="date"
      type="area"
    }
  /%}
{% /table %}
