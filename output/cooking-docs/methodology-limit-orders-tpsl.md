# Methodology for Implementing Limit Orders with Take Profit and Stop Loss — QA Test Cases

---

# Limit Orders with Take Profit and Stop Loss – Position-Centric Implementation
**ID:** TC-COOK-methodology-limit-orders-tpsl-001  
**Requirement:** cooking-docs/04-knowledge-base/business/requirements/Methodology for Implementing Limit Orders with Take Profit and Stop Loss  
**Type:** Positive

## Preconditions
- User has an active account
- Trading pair supports limit orders
- Market data indexer is operational

## Steps
1. Create BUY limit order with TP and SL
2. Wait for trigger
3. Primary order executes

## Expected Result
- Position opens
- TP and SL orders are created

## Open Questions
None

---

# Stop Loss Execution Cancels Take Profit Order
**ID:** TC-COOK-methodology-limit-orders-tpsl-002  
**Type:** Positive

## Steps
1. Market falls below stopLossValue

## Expected Result
- SL executes
- TP is cancelled

---

# Take Profit Execution Cancels Stop Loss Order
**ID:** TC-COOK-methodology-limit-orders-tpsl-003  
**Type:** Positive

## Steps
1. Market rises above takeProfitValue

## Expected Result
- TP executes
- SL is cancelled

---

# Cancel Primary Before Execution
**ID:** TC-COOK-methodology-limit-orders-tpsl-004  
**Type:** Negative

## Steps
1. User cancels primary order

## Expected Result
- No TP/SL created

---

# Market Gap Slippage Handling
**ID:** TC-COOK-methodology-limit-orders-tpsl-005  
**Type:** Edge

## Steps
1. Market gaps over TP

## Expected Result
- Executes at best price
- Slippage logged

---

# Insufficient Liquidity Partial Fill
**ID:** TC-COOK-methodology-limit-orders-tpsl-006  
**Type:** Edge

## Steps
1. Trigger order with low liquidity

## Expected Result
- Partial fill
- Remaining order active

---
# SELL Order with SL Only
**ID:** TC-COOK-methodology-limit-orders-tpsl-007  
**Type:** Positive

## Steps
1. Create SELL limit order

## Expected Result
- Executes at main trigger
- SL configured

---

# TTL Inheritance
**ID:** TC-COOK-methodology-limit-orders-tpsl-008  
**Type:** Edge

## Steps
1. Primary fills near TTL expiry

## Expected Result
- Secondary orders inherit TTL

---

# FIFO Trigger Execution
**ID:** TC-COOK-methodology-limit-orders-tpsl-009  
**Type:** Edge

## Steps
1. Trigger two orders same tick

## Expected Result
- FIFO execution

---

# Cancel TP Leaves SL Active
**ID:** TC-COOK-methodology-limit-orders-tpsl-010  
**Type:** Negative

## Steps
1. Cancel TP only

## Expected Result
- SL remains active

---

# Manual Close Cancels All Orders
**ID:** TC-COOK-methodology-limit-orders-tpsl-011  
**Type:** Positive

## Steps
1. Close position

## Expected Result
- All TP/SL cancelled

---

# Insufficient Funds Reject
**ID:** TC-COOK-methodology-limit-orders-tpsl-012  
**Type:** Negative

## Steps
1. Create order without funds

## Expected Result
- Order rejected

---

# Invalid TP/SL Fields
**ID:** TC-COOK-methodology-limit-orders-tpsl-013  
**Type:** Negative

## Steps
1. Leave TP/SL empty

## Expected Result
- Validation error

---

# Contradictory TP/SL Thresholds
**ID:** TC-COOK-methodology-limit-orders-tpsl-014  
**Type:** Edge

## Steps
1. Configure invalid thresholds

## Expected Result
- Reject or warn user

---
