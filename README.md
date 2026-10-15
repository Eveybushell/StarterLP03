# Number of Nights

| Classification   | Partition             | Range or Condition  | Expected Result                     |
| ---------------- | --------------------- | ------------------- | ----------------------------------- |
| Number of nights | Invalid low           | Fewer than 1 night  | `ValueError`                        |
| Number of nights | Valid  | 1–31 nights          | $200 per night           |
| Number of nights | Invalid high          | More than 31 nights | `ValueError`                        |

# Number of Guests

| Classification   | Partition             | Range or Condition  | Expected Result                     |
| ---------------- | --------------------- | ------------------- | ----------------------------------- |
| Number of guests | Invalid low           | Fewer than 1 guest  | `ValueError`                        |
| Number of guests | Valid, standard rate  | 1–5 guests          | No additional guest fee             |
| Number of guests | Valid, additional fee | 6–12 guests         | Additional $25 per guest, per night |
| Number of guests | Invalid high          | More than 12 guests | `ValueError`                        |

# Checkin and Checkout Dates

| Classification 1 | Classification 2 | Partition | Range or Condition | Expected Result |
| --- | --- | --- | --- | --- |
| Checkin Date | Checkout Date | Invalid | Checkin Date same as Checkout Date | `ValueError` |
| Checkin Date | Checkout Date | Valid | Checkin Date before Checkout Date | $200 per night excluding Checkout Date |


# Availability

| Classification 1 | Classification 2 | Partition | Range or Condition | Expected Result |
| --- | --- | --- | --- | --- |
| Checkin Date | Checkout Date | Invalid | Date unavailable in range | `UnavailableError` |
| Checkin Date | Checkout Date | Valid | All Dates are available | $200 per night excluding Checkout Date |

# TCNON01, Valid Number of Nights

- **Classification:** Number of nights
- **Partition:** Valid
- **Input:** `1` nights
- **Expected Result:** The reservation is accepted

# TCNON02, Invalid Low Number of Nights

- **Classification:** Number of nights
- **Partition:** Invalid low
- **Input:** `0` nights
- **Expected Result:** `ValueError`

# TCNON03, Invalid High Number of Nights

- **Classification:** Number of nights
- **Partition:** Invalid high
- **Input:** `32` nights
- **Expected Result:** `ValueError`

# TCNOG01, Valid Standard Number of Guests

- **Classification:** Number of guests
- **Partition:** Valid, standard rate
- **Input:** `3` guests
- **Expected Result:** The reservation is accepted, and no additional guest fee is added.

# TCNOG02, Valid Extra Number of Guests

- **Classification:** Number of guests
- **Partition:** Valid, additional fee
- **Input:** `6` guests
- **Expected Result:** The reservation is accepted, and the fee is increased by $25 per night.

# TCNOG03, Invalid Low Number of Guests

- **Classification:** Number of guests
- **Partition:** Invalid low
- **Input:** `0` guests
- **Expected Result:** `ValueError`

# TCNOG04, Invalid High Number of Guests

- **Classification:** Number of guests
- **Partition:** Invalid high
- **Input:** `13` guests
- **Expected Result:** `ValueError`

# TCCICO01, Valid Checkin and Checkout Dates

- **Classification:** Checkin and Checkout Dates
- **Partition:** Valid
- **Inputs:** `2026-10-15` checkIn, `2026-10-16` checkOut
- **Expected Result:** The reservation is accepted

# TCCICO02, Invalid Checkin and Checkout Dates

- **Classification:** Checkin and Checkout Dates
- **Partition:** Invalid
- **Input:** `2026-10-15` checkIn, `2026-10-15` checkOut
- **Expected Result:** `ValueError`

# TCA01, Valid Availability

- **Classification:** Availability
- **Partition:** Valid
- **Input:** `2026-10-15` checkIn, `2026-10-16` checkOut
- **Expected Result:** The reservation is accepted

# TCA02, Invalid Availability
- **Classification:** Availability
- **Partition:** Invalid
- **Input:** `2026-10-15` checkIn, `2027-10-15` checkOut
- **Expected Result:** `UnavailableError`