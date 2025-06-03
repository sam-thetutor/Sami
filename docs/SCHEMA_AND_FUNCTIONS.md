# Backend Data Schema & Functions for Sami (Stellar Integration)

## 1. Data Schema (Entities & Fields)

### User
- `id`: string (UUID)
- `twitter_handle`: string
- `twitter_id`: string
- `stellar_address`: string
- `is_verified`: boolean
- `created_at`: datetime

### Project
- `id`: string (UUID)
- `name`: string
- `description`: string
- `owner_id`: string (User.id)
- `token_code`: string (Stellar asset code)
- `token_issuer`: string (Stellar issuer address)
- `created_at`: datetime

### Campaign
- `id`: string (UUID)
- `project_id`: string (Project.id)
- `title`: string
- `description`: string
- `start_date`: datetime
- `end_date`: datetime
- `total_allocation`: number (amount of tokens)
- `status`: enum (draft, active, ended, cancelled)
- `created_at`: datetime

### Submission
- `id`: string (UUID)
- `campaign_id`: string (Campaign.id)
- `user_id`: string (User.id)
- `tweet_url`: string
- `tweet_id`: string
- `submitted_at`: datetime
- `engagement_score`: number (calculated)
- `reward_amount`: number (tokens, calculated/distributed)
- `status`: enum (pending, approved, rejected, rewarded)

---

## 2. Backend Functions (API/Service Layer)

### User Management
- `registerUser(twitter_handle, twitter_id, stellar_address)`
- `verifyUser(user_id, verification_data)`
- `getUser(user_id)`

### Project & Campaign Management
- `createProject(owner_id, name, description, token_code, token_issuer)`
- `getProjects()`
- `createCampaign(project_id, title, description, start_date, end_date, total_allocation)`
- `getCampaigns(project_id)`
- `updateCampaignStatus(campaign_id, status)`

### Submission & Engagement
- `submitPost(user_id, campaign_id, tweet_url, tweet_id)`
- `getSubmissions(campaign_id)`
- `updateEngagement(submission_id, engagement_data)` (periodically fetches and updates engagement metrics)
- `calculateRewards(campaign_id)` (runs at end of campaign)

### Blockchain Interactions (Stellar)
- `allocateTokensToCampaign(project_id, campaign_id, amount)` (locks tokens for rewards)
- `distributeRewards(campaign_id)` (sends tokens to users' Stellar addresses based on engagement)
- `getUserBalance(stellar_address, token_code, token_issuer)`

### Admin/Utility
- `getLeaderboard(campaign_id)`
- `getUserRewards(user_id)`

---

## 3. Notes on Stellar Integration

- Token allocation and reward distribution should use Stellar's asset transfer operations.
- You may need to manage a "campaign escrow" account for each campaign or use multi-signature accounts for security.
- All token transfers (allocation, distribution) should be recorded on-chain and referenced in your backend for auditability. 