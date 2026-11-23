# Bug Reports - Demo Web Shop

Found during manual testing on November 24, 2026.

---

## BUG-01: Checkout accepts an expired credit card expiry date

**Severity:** Medium
**Priority:** High
**Status:** Open
**Found in:** TC-19 (checkout payment step)

**Description:**
On the payment information step, the expiration date dropdowns default to month 01 and year 2026, and the earliest selectable year is 2026. Testing was done on November 24, 2026, so the default expiry (01/2026) was already about 10 months in the past. The site accepted this expired date without any validation message and moved to the order confirmation step. I completed the order with it and the order was placed successfully (order #2421203).

**Steps to reproduce:**
1. Log in and add any product to the cart.
2. Go through checkout: billing address, shipping address, shipping method.
3. Choose "Credit Card" as the payment method.
4. Fill cardholder name, card number (4111 1111 1111 1111) and card code, and leave the expiration date at the default 01/2026 (a past date).
5. Click Continue, then Confirm the order.

**Expected:** The payment step rejects an expiry date in the past and asks for a valid date.

**Actual:** The expired date is accepted and the order is placed.

**Why it matters:** On a real store this would send orders to payment with a card that can never be charged, failing later or confusing the customer. The demo does not charge cards, but the validation should still exist.

**Evidence:**

![BUG-01: payment step with the default expiry 01/2026, already expired at test time](https://github.com/user-attachments/assets/c559fc5a-64d5-4e38-a588-920c0a95b9b4)

---

## BUG-02: Billing validation error stays on screen after the step succeeds

**Severity:** Low
**Priority:** Low
**Status:** Open
**Found in:** TC-14 / TC-15 (checkout billing step)

**Description:**
After clicking Continue on the billing address with empty required fields, validation messages appear (for example "Country is required."). After I filled the fields correctly and continued successfully to the shipping step, the "Country is required." message from the failed attempt was still visible on the page even though the step had passed.

**Steps to reproduce:**
1. Add a product to the cart and start checkout.
2. On Billing address, click Continue with required fields empty - validation errors appear.
3. Fill all required fields and click Continue again - the step passes.
4. Observe the page: the old "Country is required." message is still displayed.

**Expected:** Validation messages are cleared once the step passes.

**Actual:** The stale error message remains visible after a successful continue.

**Why it matters:** Cosmetic, but it can make a customer think something is still wrong during checkout.
