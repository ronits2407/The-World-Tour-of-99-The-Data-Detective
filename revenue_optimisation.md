NOTE:- This pdf was formatted using AI , as i asked in the group we are allowed to use AI for formatting , i have not used it for making new content out of the box
but just format the markdowns of my analysys pdf and write it here



# Revenue Optimization & Findings

## 1. Merch Sales Analysis
*Observations on the relationship between Crowd Energy and Merch Sales:*

* **V_Alpha:** Linear correlation observed.
    > `merch = 14.2 * energy + 32.99`
* **V_Delta:** Linear correlation observed.
    > `merch = 13.58 * energy + 78.53`
* **V_Gamma:** Linear correlation observed.
    > `merch = 15.68 * energy - 58.04`
* **V_Beta:**
        `merch = $609`
    > The R2 score was 0.2 which says that it is not linear.
    > *Action:* Change the merch_sales variable with the equations above, and just take median merch sales for V_Beta.

---

## 2. Pricing Strategy Conclusions
*(Non-formula based, trend-based approach)*

### **V_Gamma**
* **Recommended Price:** **$80 - $90**
* **Reasoning:** Keep ticket prices high. This venue sees a higher crowd when ticket prices are high, thereby maximizing profit.

### **V_Delta**
* **Recommended Price:** **$40 - $60**
* **Reasoning:** The crowd's reaction is the same for almost all types of prices except the extremes. We don't have to set the price too high, as we are already making a good amount with the merch.

### **V_Alpha**
* **Recommended Price:** **$50 - $70**
* **Reasoning:** The crowd's reaction is the same for almost all types of prices except the extremes. We have to cover for the less merch sales in Alpha compared to Delta and Gamma.

### **V_Beta**
* **Recommended Price:** **$70 - $80**
* **Reasoning:** Higher price point recommended again to cover up for the merch sales structure.


`Profit = Merch sales + (ticket_price * Crowdsize) - ($8 * corwd_size + $5,000)`

for *V_Alpha* : 
    profit = `14.2 * energy + 32.99 + (ticket_price * Crowdsize) - ($8 * corwd_size + $5,000)`

for *V_Beta* : 
    profit = `609 + (ticket_price * Crowdsize) - ($8 * corwd_size + $5,000)`

for *V_Delta* : 
    profit = `13.58 * energy + 78.53 + (ticket_price * Crowdsize) - ($8 * corwd_size + $5,000)`

for *V_Gamma* : 
    profit = `15.68 * energy - 58.04 + (ticket_price * Crowdsize) - ($8 * corwd_size + $5,000)`