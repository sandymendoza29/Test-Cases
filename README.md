# Test-Cases
TEST SUITE FOR SAUCE DEMO SITE

https://www.saucedemo.com/

I've created a Test Suite for SauceDemo site using Claude. In the prompt I included the Happy Paths, Negative test cases and Edge cases (This is basically for Manual Testing). The file is attached as saucedemo_test_suite.csv
----------------------------------------------------------------------------------------------------------------------------------------------------------------

A few notes on approach:
- SauceDemo's exact behavior here can shift between deployments, so worth confirming against the live site before automating.
- The *problem_user* and *error_user* cases are especially useful since they're designed to expose bugs — good candidates for your negative/edge suite.

I also converted the highest-priority (P1) cases into actual automated test code for Playwright.
----------------------------------------------------------------------------------------------------------------------------------------------------------------
Structure:
 
  *pages/ — Page Object Model for Login, Inventory, Cart, Checkout
  
  *tests/ — one spec file per suite area, test names tagged with their original Test ID (e.g. CHK-04) for traceability back to the CSV
  
  *playwright.config.ts — points at the live saucedemo.com, HTML + list reporters
  
  *README.md — setup and run instructions

**To run it:**
npm install,
npx playwright install chromium,
npm test

One design note: CHK-04 computes expected otals dynamically (sum of item prices vs. displayed subtotal/tax/total) instead of hardcoding prices, so it won't break if SauceDemo changes product pricing.

The file is attached as saucedemo-playwright-suite.zip.
