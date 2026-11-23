# Test Cases - Demo Web Shop

Executed: November 24, 2026 | Browser: Chrome | Tester: Mohamed Tantawy

Test data: registered account (my own email), product "Health Book" (10.00), test card 4111 1111 1111 1111.

## Registration and login

| ID | Title | Steps | Expected result | Actual result | Status |
|---|---|---|---|---|---|
| TC-01 | Register with mismatched passwords | 1. Open Register 2. Fill all fields 3. Password "Test@12345", Confirm "Different@999" 4. Click Register | Registration is rejected with a clear message | Message shown: "The password and confirmation password do not match." | Pass |
| TC-02 | Register with valid data | 1. Open Register 2. Fill all fields with matching passwords 3. Click Register | Account is created | "Your registration completed" shown, account email appears in header | Pass |
| TC-03 | Login with wrong password | 1. Log in with registered email and a wrong password | Login rejected with an error | "Login was unsuccessful... The credentials provided are incorrect" | Pass |
| TC-04 | Login with valid credentials | 1. Log in with registered email and correct password | User is logged in | Header shows my email and "Log out" | Pass |

## Search and catalog

| ID | Title | Steps | Expected result | Actual result | Status |
|---|---|---|---|---|---|
| TC-05 | Search a valid keyword | Search for "computer" | Matching products listed | 4 products returned (Build your own cheap computer 800.00, Build your own computer 1200.00, Build your own expensive computer 1800.00, Simple Computer 800.00) | Pass |
| TC-06 | Search with no matches | Search for "zzxqwe" | Clear "no results" message | "No products were found that matched your criteria." | Pass |
| TC-07 | Search below minimum length | Search for "ab" (2 characters) | Search rejected with guidance | "Search term minimum length is 3 characters" | Pass |
| TC-08 | Search with a script payload | Search for `<script>alert(1)</script>` | Input is treated as text, no script runs | No script executed, page rendered normally | Pass |
| TC-09 | Sort books by price low to high | 1. Open Books category 2. Sort by "Price: Low to High" | Products ordered by ascending price | Order: 10.00, 10.00, 10.00, 24.00 ... ascending by the selling price | Pass |

## Cart

| ID | Title | Steps | Expected result | Actual result | Status |
|---|---|---|---|---|---|
| TC-10 | Add a product to the cart | 1. Open "Health Book" 2. Click Add to cart | Product added, confirmation shown | "The product has been added to your shopping cart", cart count becomes 1 | Pass |
| TC-11 | Update quantity | 1. In cart set Qty to 3 2. Click Update shopping cart | Line total recalculates (3 x 10.00) | Line total 30.00 | Pass |
| TC-12 | Apply an invalid discount code | 1. Enter coupon "FAKECODE20" 2. Apply | Coupon rejected with a message | "The coupon code you entered couldn't be applied to your order" | Pass |

## Checkout

| ID | Title | Steps | Expected result | Actual result | Status |
|---|---|---|---|---|---|
| TC-13 | Checkout without accepting terms of service | 1. In cart, leave the terms checkbox unticked 2. Click Checkout | Checkout blocked with a warning | Popup: "Please accept the terms of service before the next step." | Pass |
| TC-14 | Billing address with empty required fields | 1. At checkout, click Continue with Country, City, Address, Zip, Phone empty | Validation errors on each missing field | Errors shown: "Country is required.", "City is required", "Street address is required", "Zip / postal code is required", "Phone is required" | Pass |
| TC-15 | Billing address with valid data | 1. Fill country Egypt, city Giza, address, zip 12511, phone 2. Continue | Step completes, shipping address opens | Moved to Shipping address; note: a stale validation message stayed on screen (see BUG-02) | Pass |
| TC-16 | Choose a shipping method | Select "2nd Day Air (20.00)" and continue | Selection accepted, carried to totals | 2nd Day Air selected; shipping 20.00 shown on the confirm step | Pass |
| TC-17 | Choose Credit Card payment | Select "Credit Card" and continue | Card form opens | Form with card type, cardholder name, card number, expiry, card code shown | Pass |
| TC-18 | Submit empty card details | Click Continue with the card form empty | Validation errors, stay on the step | Errors: "Enter cardholder name", "Wrong card number", "Wrong card code" | Pass |
| TC-19 | Pay with an expired card date | 1. Fill valid cardholder/card number/code 2. Leave expiry at the default 01/2026 (already expired in Nov 2026) 3. Continue | Expired card rejected | Checkout accepted the expired date and moved to Confirm order (see BUG-01) | **Fail** |
| TC-20 | Confirm the order | Review the summary and click Confirm | Order placed, order number shown | "Your order has been successfully processed!", order #2421203 | Pass |
| TC-21 | Order totals are calculated correctly | On the confirm step, check the math | Sub-total + shipping + tax = total | Sub-total 30.00 + Shipping 20.00 + Tax 0.00 = Total 50.00 | Pass |
| TC-22 | Order appears in My Account | Open My account > Orders | The order is listed with correct total | Order #2421203, status Pending, total 50.00 ([screenshot 1](https://github.com/user-attachments/assets/c13e2eb7-42c7-4a14-a08c-fb9320499025), [screenshot 2](https://github.com/user-attachments/assets/2ed244ca-9ac6-434a-9cfe-5383ac331a3b)) | Pass |

## Extra checks

| ID | Title | Steps | Expected result | Actual result | Status |
|---|---|---|---|---|---|
| TC-23 | Newsletter with an invalid email | Enter "notanemail" and subscribe | Rejected with a message | "Enter valid email" | Pass |
| TC-24 | Newsletter with a valid email | Enter the registered email and subscribe | Signup accepted | "Thank you for signing up! A verification email has been sent." | Pass |
| TC-25 | Gift card without recipient details | Open the 25.00 Virtual Gift Card and click Add to cart with empty recipient fields | Validation requires recipient name and email | "Enter valid recipient name", "Enter valid recipient email" | Pass |

## Result

**25 executed - 24 passed - 1 failed.** The failed case produced BUG-01.
