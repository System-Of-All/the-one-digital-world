-# Data Models — The One Digital World  
### Based on The One Law  
### Part of the System Of All Organization

This document defines the core data models used across The One Digital World ecosystem. These models form the structural backbone of the platform, enabling consistent data flow across the World Problem Board, Oracle prediction engine, SALL token economy, Play‑to‑Earn, Watch‑to‑Earn, governance, and jurisdiction collaboration.

All models are designed to be:

- Modular  
- Extensible  
- Secure  
- Auditable  
- Compliant with The One Law  



# 1. User Model

Represents a human participant, institution, or jurisdiction entity.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| user_id | UUID | Unique identifier |
| name | String | Display name |
| email | String | Optional, for login |
| wallet_address | String | Multi‑chain wallet |
| role | Enum(user, contributor, institution, government, admin) | Access level |
| reputation_score | Float | Contribution‑based score |
| sall_balance | Float | Current SALL token balance |
| created_at | Timestamp | Account creation |
| updated_at | Timestamp | Last update |

### Notes

- Wallet-based login supported  
- Reputation influences rewards  
- Institutions/governments have extended permissions  



# 2. Problem Model (World Board)

Represents a real-world challenge.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| problem_id | UUID | Unique identifier |
| title | String | Problem name |
| category | Enum(climate, environment, health, poverty, education, digital-divide, etc.) | Problem type |
| severity | Integer (1–10) | Impact level |
| progress | Integer (0–100) | Solution progress |
| region | String | Global or specific region |
| description | Text | Detailed explanation |
| created_by | user_id | Creator |
| created_at | Timestamp | Creation time |
| updated_at | Timestamp | Last update |

### Relationships

- Has many **solutions**  
- Has many **contributors**  
- Can be linked to **jurisdictions**  
- Can receive **funding**  



# 3. Solution Model

Represents a proposed solution to a problem.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| solution_id | UUID | Unique identifier |
| problem_id | UUID | Linked problem |
| title | String | Solution name |
| description | Text | Detailed proposal |
| created_by | user_id | Author |
| status | Enum(proposed, in-progress, completed, rejected) | Lifecycle |
| funding_required | Float | Optional |
| funding_received | Float | Optional |
| jurisdiction_partner | String | Optional |
| created_at | Timestamp | Creation time |
| updated_at | Timestamp | Last update |



# 4. Oracle Market Model

Represents a prediction market.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| market_id | UUID | Unique identifier |
| question | String | Prediction question |
| type | Enum(yes-no, milestone, time-based) | Market type |
| creator_id | user_id | Market creator |
| status | Enum(open, locked, resolved, disputed) | Market state |
| resolution | Enum(yes, no, unresolved) | Final outcome |
| pool_yes | Float | Total SALL staked on "yes" |
| pool_no | Float | Total SALL staked on "no" |
| created_at | Timestamp | Creation time |
| closes_at | Timestamp | Market lock time |
| resolved_at | Timestamp | Resolution time |

### Relationships

- Has many **stakes**  
- Has one **resolution authority** (automated or admin)  



# 5. Stake Model (Oracle)

Represents a user’s stake in a prediction market.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| stake_id | UUID | Unique identifier |
| market_id | UUID | Linked market |
| user_id | UUID | Staker |
| choice | Enum(yes, no) | Prediction |
| amount | Float | SALL staked |
| created_at | Timestamp | Stake time |



# 6. Game Session Model (Play‑to‑Earn)

Represents a user’s game activity.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| session_id | UUID | Unique identifier |
| user_id | UUID | Player |
| game_type | Enum(trivia, memory, spin, scramble, puzzle) | Game |
| score | Integer | Game score |
| reward | Float | SALL earned |
| created_at | Timestamp | Session time |



# 7. Ad Watch Model (Watch‑to‑Earn)

Represents a user watching an advertisement.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| watch_id | UUID | Unique identifier |
| user_id | UUID | Viewer |
| ad_id | UUID | Advertisement |
| watch_time | Integer | Seconds watched |
| reward | Float | SALL earned |
| verified | Boolean | Anti‑fraud check |
| created_at | Timestamp | Watch time |



# 8. Wallet Transaction Model

Represents any SALL token movement.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| tx_id | UUID | Unique identifier |
| user_id | UUID | Owner |
| type | Enum(earn, stake, withdraw, deposit, reward, purchase) | Transaction type |
| amount | Float | SALL amount |
| chain | String | Blockchain used |
| status | Enum(pending, completed, failed) | Transaction state |
| created_at | Timestamp | Time of transaction |



# 9. Governance Proposal Model

Represents a governance action.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| proposal_id | UUID | Unique identifier |
| title | String | Proposal name |
| description | Text | Details |
| created_by | user_id | Author |
| status | Enum(open, voting, approved, rejected) | Lifecycle |
| created_at | Timestamp | Creation time |
| closes_at | Timestamp | Voting deadline |



# 10. Vote Model

Represents a user’s vote on a proposal.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| vote_id | UUID | Unique identifier |
| proposal_id | UUID | Linked proposal |
| user_id | UUID | Voter |
| choice | Enum(yes, no, abstain) | Vote |
| weight | Float | Voting power (SALL or reputation) |
| created_at | Timestamp | Vote time |



# 11. Jurisdiction Model

Represents a government or institutional entity.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| jurisdiction_id | UUID | Unique identifier |
| name | String | Country, region, or institution |
| type | Enum(government, agency, institution) | Entity type |
| contact | String | Optional |
| region | String | Geographic region |
| created_at | Timestamp | Registration time |



# 12. Audit Log Model

Tracks all critical actions for transparency.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| log_id | UUID | Unique identifier |
| user_id | UUID | Actor |
| action | String | Action performed |
| target_type | String | Affected model |
| target_id | UUID | Affected record |
| timestamp | Timestamp | Time of action |
| metadata | JSON | Additional details |



# 13. Alignment With The One Law

All data models are designed to support:

- Transparency  
- Fairness  
- Accountability  
- Universal access  
- Non‑exclusion  
- Benefit to all humanity  

The One Law governs:

- Data visibility  
- Access control  
- Reward fairness  
- Governance participation  
- Institutional collaboration  



# 14. Summary

These data models form the structural foundation of The One Digital World.  
They ensure consistency, scalability, and integrity across all modules of the ecosystem.



## © 2026 System Of All  
**The One System for All Humanity.**  
**Based on The One Law.**
