# 📐 DAX Measures Used

## 🔹 Total Revenue

Total Revenue = SUM(fact_bookings[revenue])

## 🔹 Total Bookings

Total Bookings = COUNT(fact_bookings[booking_id])

## 🔹 Occupancy Rate (%)

Occupancy % =
DIVIDE(
SUM(fact_aggregated_bookings[successful_bookings]),
SUM(fact_aggregated_bookings[capacity])
) * 100

## 🔹 Average Daily Rate (ADR)

ADR =
DIVIDE(
[Total Revenue],
SUM(fact_bookings[rooms_sold])
)

## 🔹 Revenue Per Available Room (RevPAR)

RevPAR =
DIVIDE(
[Total Revenue],
SUM(fact_aggregated_bookings[capacity])
)

## 🔹 Cancellation Rate (%)

Cancellation % =
DIVIDE(
SUM(fact_bookings[cancelled_bookings]),
COUNT(fact_bookings[booking_id])
) * 100

## 🔹 Weekend Indicator

Weekend =
IF(
WEEKDAY(dim_date[date]) IN {1,7},
"Weekend",
"Weekday"
)
