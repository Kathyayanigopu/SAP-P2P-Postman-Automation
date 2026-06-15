# SAP-P2P-Postman-Automation
Day-by-day API test automation for SAP Procure-to-Pay using Postman. Covers auto-increment scripts, assertions, data chaining, and reporting for SAP S/4HANA testing scenarios.


**Goal:** Replace 3 hours of manual SAP testing with 90-second automated runs.

### Progress
- [x] Day 1: Workspace + Collection Setup
- [x] Day 2: GET/POST Requests
- [x] Day 3: Environment Variables
- [x] Day 4: Auto-Increment PO Numbers
 ### Evidence
See `/Day-4-Auto-Increment/screenshots/` for execution proof.
- [ ] Day 5: Test Assertions + Reports
- [ ] Day 6: PO → GR → IR Data Chaining

Each Day folder has code, screenshots, and results.


# Day 4: Auto-Incrementing IDs in Postman

### Goal
Automate ID generation so each API request uses a unique number without manual updates. Example: PO-1001, PO-1002, PO-1003...

### Key Concepts Used
1. **Environment Variables** - Store and update `requestId` between runs
2. **Post-response Script** - JavaScript that runs after API responds
3. **pm Object** - `pm.environment.get()` and `pm.environment.set()` 
4. **Collection Runner** - Test auto-increment with multiple iterations
5. **Dynamic Variables** - `{{requestId}}` in request body/URL

### Code Implemented
Location: `POST Request → Scripts → Post-response`

```javascript
let currentId = pm.environment.get("requestId"); 
currentId++; 
pm.environment.set("requestId", currentId);
console.log("Next ID set to: " + currentId);
