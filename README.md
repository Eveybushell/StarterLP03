Number of Nights

| Classification   | Partition             | Range or Condition  | Expected Result                     |
| ---------------- | --------------------- | ------------------- | ----------------------------------- |
| Number of nights | Invalid low           | Fewer than 1 night  | `ValueError`                        |
| Number of nights | Valid  | 1–31 nights          | $200 per night           |
| Number of nights | Invalid high          | More than 31 nights | `ValueError`                        |

Number of Guests

| Classification   | Partition             | Range or Condition  | Expected Result                     |
| ---------------- | --------------------- | ------------------- | ----------------------------------- |
| Number of guests | Invalid low           | Fewer than 1 guest  | `ValueError`                        |
| Number of guests | Valid, standard rate  | 1–5 guests          | No additional guest fee             |
| Number of guests | Valid, additional fee | 6–12 guests         | Additional $25 per guest, per night |
| Number of guests | Invalid high          | More than 12 guests | `ValueError`                        |

Checkin and Checkout Dates

| Classification 1 | Classification 2 | Partition | Range or Condition | Expected Result |
| --- | --- | --- | --- | --- |
| Checkin Date | Checkout Date | Invalid | Checkin Date same as Checkout Date | `ValueError` |
| Checkin Date | Checkout Date | Valid | Checkin Date before Checkout Date | $200 per night excluding Checkout Date |


Availability

| Classification 1 | Classification 2 | Partition | Range or Condition | Expected Result |
| --- | --- | --- | --- | --- |
| Checkin Date | Checkout Date | Invalid | Date unavailable in range | `UnavailableError` |
| Checkin Date | Checkout Date | Valid | All Dates are available | $200 per night excluding Checkout Date |