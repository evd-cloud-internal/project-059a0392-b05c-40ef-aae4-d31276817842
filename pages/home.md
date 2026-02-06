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