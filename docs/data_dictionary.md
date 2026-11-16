
# Data Dictionary
## Digital Wallet Fraud Risk & Financial Performance Intelligence

**Dataset:** Onyx DataDNA — African Gig-Economy and Digital Wallet Risk

**Business Scenario:** PayPesa

**Purpose:** Document the tables, columns, and business meanings of the dataset.

---

## 1. fact_transactions

**Description:** Records individual digital-wallet transactions.

**Grain:** One row per transaction.

**Primary Key:** `transaction_id`

| Column Name | Meaning |
|---|---|
| `transaction_id` | Unique identifier for each transaction. |
| `worker_id` | Identifies the worker associated with the transaction. |
| `date_id` | Identifies the date on which the transaction was recorded. |
| `channel_id` | Identifies the payment channel used. |
| `market_id` | Identifies the country or market associated with the transaction. |
| `transaction_type` | Type of transaction, such as Cash-In, Cash-Out, or Peer Transfer. |
| `amount_local` | Transaction amount recorded in the local currency. |
| `amount_usd` | Transaction amount recorded in US dollars. |
| `transaction_outcome` | Recorded transaction result, such as Completed, Failed, or Reversed. |
| `is_fraud_flagged` | Indicates whether the transaction was flagged as potentially fraudulent. |
| `is_disputed` | Indicates whether the transaction has a dispute flag. |
| `is_reversed` | Indicates whether the transaction has a reversal flag. |
| `velocity_score` | Recorded transaction-activity score; calculation method is unspecified. |
| `fraud_loss_usd` | Recorded fraud-related loss or financial exposure in USD; exact definition requires clarification. |
| `processing_time_ms` | Recorded transaction processing duration in milliseconds. |

---

## 2. dim_worker

**Description:** Stores information about gig-economy workers.

**Grain:** One row per worker.

**Primary Key:** `worker_id`

| Column Name | Meaning |
|---|---|
| `worker_id` | Unique identifier for each worker. |
| `worker_name` | Recorded name of the worker. |
| `gig_segment` | Type of gig-economy work performed by the worker. |
| `account_tenure_days` | Recorded age of the worker's account in days. |
| `kyc_tier` | Recorded Know Your Customer (KYC) verification level. |
| `gender` | Recorded gender of the worker. |
| `age_band` | Age group to which the worker belongs. |
| `risk_score` | Recorded account risk score; calculation method is unspecified. |
| `is_active` | Indicates whether the worker's account is recorded as active. |
| `preferred_channel` | Worker's preferred payment channel. |

---

## 3. dim_channel

**Description:** Stores information about the payment channels.

**Grain:** One row per payment-channel record.

**Primary Key:** `channel_id`

| Column Name | Meaning |
|---|---|
| `channel_id` | Unique identifier for each channel record. |
| `channel_type` | Main payment channel, such as USSD, POS, Agent, or Mobile App. |
| `channel_subtype` | More specific classification of the payment channel. |
| `is_digital` | Indicates whether the channel is classified as digital. |
| `avg_fraud_rate` | Source-labelled historical fraud-rate measure; calculation and scale require clarification. |
| `requires_internet` | Indicates whether the channel is classified as requiring internet connectivity. |

---

## 4. dim_market

**Description:** Stores information about the countries or markets in which transactions are recorded.

**Grain:** One row per market.

**Primary Key:** `market_id`

| Column Name | Meaning |
|---|---|
| `market_id` | Unique identifier for each market. |
| `country` | Name of the country, such as Ghana, Kenya, Nigeria, or South Africa. |
| `iso_code` | Two-letter country code, such as GH or NG. |
| `local_currency` | Local currency code, such as GHS, KES, NGN, or ZAR. |
| `dominant_channel` | Source-labelled most commonly used payment channel within the market. |
| `regulatory_tier` | Recorded classification of the market's regulatory environment. |
| `usd_fx_rate` | Recorded foreign-exchange rate associated with the market; conversion method requires clarification. |
| `market_fraud_index` | Recorded market-level fraud-risk index; calculation and scale are unspecified. |

---

## 5. dim_date

**Description:** Stores calendar information used to analyze transactions over time.

**Grain:** One row per calendar date.

**Primary Key:** `date_id`

| Column Name | Meaning |
|---|---|
| `date_id` | Unique identifier for a calendar date in YYYYMMDD format. |
| `full_date` | Complete calendar date. |
| `year` | Calendar year. |
| `month` | Name of the month. |
| `quarter` | Calendar quarter, such as Q1 or Q2. |
| `day_of_week` | Name of the day, such as Monday or Tuesday. |
| `is_weekend` | Indicates whether the date falls on a weekend. |
| `is_month_end` | Indicates whether the date is the last day of the month. |
| `week_number` | Intended week-of-year value; currently missing for all records in the uploaded file. |

---

## Important Notes

- The dataset contains 5 tables and 48 columns.
- The fact table records one transaction per row.
- Fraud-flagged transactions are not necessarily confirmed fraud.
- Transaction amounts do not represent company revenue.
- Some source definitions require further clarification.
- Original data values should be preserved until validated.
