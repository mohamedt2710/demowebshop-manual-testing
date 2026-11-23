# Test Plan - Demo Web Shop E-Commerce Testing

## 1. Objective

Test the complete customer journey of Demo Web Shop (https://demowebshop.tricentis.com/) as an end user: create an account, find products, manage the cart and finish a paid order. The goal is to confirm the main flow works and to find and report defects.

## 2. Scope

**In scope:**
- Registration and login
- Product search and sorting
- Shopping cart (add, update quantity, discount code)
- Full checkout: terms of service, billing/shipping address, shipping method, payment method, order confirmation
- Order history
- Newsletter, community poll, gift cards (quick checks)

**Out of scope:**
- Admin panel (not available to customers)
- Real payment processing (the site is a demo, no real charges)
- Performance and load testing
- Mobile testing (desktop browser only)
- Security testing beyond a basic input-injection check on the search field

## 3. Approach

Black-box manual testing. I wrote test cases before/during execution based on the requirements a normal store should meet, then executed each one in the browser and recorded the actual result. Bugs are reported with steps to reproduce, expected vs actual result, severity and a screenshot where useful.

Test data:
- Registered account with my own email
- Test product: "Health Book" (price 10.00)
- Standard test card number 4111 1111 1111 1111 (no real charge is possible on this site)

## 4. Environment

- Site: https://demowebshop.tricentis.com/ (production demo instance)
- Browser: Chrome (desktop)
- Date of execution: November 24, 2026

## 5. Entry criteria

- Site is reachable and the catalog loads
- Registration is open for new accounts

## 6. Exit criteria

- All planned test cases executed
- All defects found are documented in bug-reports.md
- Results summarized in test-summary-report.md

## 7. Risks

- The demo site resets or changes data over time, so exact product names or prices may differ on a later run
- Because it is a shared demo, other users' data (poll votes, orders) is visible and cannot be controlled
