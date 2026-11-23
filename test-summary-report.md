# Test Summary Report - Demo Web Shop

**Date:** November 24, 2026
**Tester:** Mohamed Tantawy
**Application:** Demo Web Shop (Tricentis) - https://demowebshop.tricentis.com/
**Type:** Manual black-box testing, desktop Chrome

## Scope covered

Registration, login, product search, sorting, cart management, discount codes, and the complete checkout flow through the payment step and order confirmation, plus quick checks on the newsletter, community poll and gift cards.

## Execution results

| Result | Count |
|---|---|
| Test cases executed | 25 |
| Passed | 24 |
| Failed | 1 |
| Bugs reported | 2 (1 Medium, 1 Low) |

## Defects found

- **BUG-01 (Medium):** the credit card expiry validation accepts a past date. The default expiry offered at checkout (01/2026) was already expired at test time and the order was placed with it.
- **BUG-02 (Low):** a billing validation error message stays on screen after the billing step has already passed.

## What went well

The complete happy path works: I registered, logged in, searched, filtered, managed the cart and placed a real order end to end (order #2421203, Health Book x3 = 30.00, 2nd Day Air shipping 20.00, total 50.00). The order appeared correctly in My Account. Input validation is good in most places: registration, login, billing address, card fields, coupon codes, newsletter and gift cards all reject bad input with clear messages. Order total math was correct at every step.

## Observations (not bugs)

- The search field requires at least 3 characters and handles a script payload safely (treated as plain text).
- The demo store is shared, so catalog data and poll numbers change over time.

## Conclusion

The store's main customer journey is usable end to end. The one failed test (BUG-01) is in payment validation and should be fixed before this checkout code would be trusted with real payments. Everything else tested behaves as a customer would expect.

## Evidence

- Order in My Account: ![Orders list](https://github.com/user-attachments/assets/c13e2eb7-42c7-4a14-a08c-fb9320499025)
- Order details: ![Order details](https://github.com/user-attachments/assets/2ed244ca-9ac6-434a-9cfe-5383ac331a3b)
- BUG-01 screenshot: see bug-reports.md
