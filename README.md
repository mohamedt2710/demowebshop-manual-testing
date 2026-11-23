# E-Commerce Manual Testing - Demo Web Shop

Manual end-to-end testing of [Demo Web Shop](https://demowebshop.tricentis.com/), a demo e-commerce site by Tricentis. I tested the full customer journey from registration to placing a paid order.

This is my third portfolio project. After testing Swag Labs manually and practicing API testing with Postman, I wanted to practice on a store with a complete checkout flow: account registration, product search and filtering, cart, shipping options and a payment step.

## What I tested

- Account registration (valid and invalid data)
- Login and logout
- Product search (valid keyword, no results, too-short keyword, script injection attempt)
- Category browsing and sorting by price
- Cart: add product, update quantity, discount codes
- Checkout: terms of service check, billing and shipping address, shipping methods, payment methods, order confirmation
- Order history in My Account
- Extra: newsletter signup, community poll, gift card validation

## Documents

| File | Contents |
|---|---|
| [test-plan.md](test-plan.md) | Scope, approach, environment and entry/exit criteria |
| [test-cases.md](test-cases.md) | 25 executed test cases with steps and results |
| [bug-reports.md](bug-reports.md) | 2 bugs found during testing |
| [test-summary-report.md](test-summary-report.md) | Results overview and conclusion |

## Results in short

- 25 test cases executed: 24 passed, 1 failed
- 2 bugs reported (1 Medium, 1 Low)
- A real order was placed end to end (order #2421203, total 50.00)

## Environment

- Chrome browser, November 24, 2026
- Test account registered with my own email
- No real payment was made: Demo Web Shop is a practice site and the card used is the standard test card number
