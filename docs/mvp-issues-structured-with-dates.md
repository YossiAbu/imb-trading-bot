# IMB Trading Bot – MVP Issues (Structured Format)

This file defines all GitHub Issues to be generated automatically by an Agent.
It includes:
- Parent issues (one per Phase)
- Sub-issues (each task)
- Milestone assignment
- Labels
- Descriptions (for every task)
- Start/Due date placeholders (to be set in the Project)

---

# PHASE 0 – Pre-Development Requirements (Parent Issue)

## Parent Issue: [P0] Phase 0 – Pre-Development Requirements

### Metadata
Start Date: 2025-12-01
Due Date: 2025-12-03

Milestone: Phase 0 – Pre-Development  
Labels: ["MVP", "infra"]  
Description:  
  This phase includes tasks that must be completed by the founders before development begins (access, decisions, and input data).

### Subtasks (Checklist inside parent issue)
- [ ] [T0.1] Provide AWS credentials (IAM user with EC2, S3, CloudWatch)
- [ ] [T0.2] Choose exchange for MVP (Binance Testnet recommended)
- [ ] [T0.3] Provide API Keys for chosen Testnet (Read + Trade, No Withdraw)
- [ ] [T0.4] Decide if Dashboard is included in MVP

#### [T0.1] Provide AWS credentials (IAM user with EC2, S3, CloudWatch)

### Metadata
Start Date: 2025-12-01
Due Date: 2025-12-03


**Goal**  
Ensure the developer has secure access to AWS resources required for the MVP (EC2, S3, CloudWatch).

**Steps**  
- Create or choose an AWS account for the project.  
- Create an IAM user or role dedicated to the IMB Trading Bot project.  
- Grant permissions for EC2, S3, IAM (limited), and CloudWatch Logs/Metrics.  
- Share access credentials (access key / role assumption details) securely with the developer.

**Definition of Done**  
- The developer can log in or assume the IAM role.  
- The developer can start/stop EC2 instances.  
- The developer can read/write to S3 in the designated bucket.  
- The developer can view CloudWatch logs and metrics.

---

#### [T0.2] Choose exchange for MVP (Binance Testnet recommended)

### Metadata
Start Date: 2025-12-01
Due Date: 2025-12-03


**Goal**  
Select a single crypto exchange for the MVP (Testnet environment), so all technical integration work focuses on one platform.

**Steps**  
- Review candidate exchanges (e.g., Binance, Bybit, Coinbase).  
- Validate availability of Spot Testnet API.  
- Confirm the business and technical team agree on the chosen exchange.  
- Document the chosen exchange and relevant links (API docs, Testnet URLs).

**Definition of Done**  
- One exchange is officially selected for the MVP.  
- The selection is documented and shared with the developer.  
- API documentation links and Testnet URLs are available.

---

#### [T0.3] Provide API Keys for chosen Testnet (Read + Trade, No Withdraw)

### Metadata
Start Date: 2025-12-01
Due Date: 2025-12-03


**Goal**  
Provide secure and limited API keys for Testnet trading: read balances/market data and place test trades, with no withdrawal permissions.

**Steps**  
- Create a Testnet account on the chosen exchange.  
- Generate API keys with the minimum required permissions (Read + Trade, no Withdraw).  
- Verify that the keys work by performing a simple API call.  
- Share the keys securely with the developer (never via plain chat/email if possible).

**Definition of Done**  
- Testnet API key and secret are created and tested.  
- Permissions are limited to read/trade only.  
- Developer confirms successful connection using the keys.

---

#### [T0.4] Decide if Dashboard is included in MVP

### Metadata
Start Date: 2025-12-01
Due Date: 2025-12-03


**Goal**  
Clarify whether a customer-facing or internal dashboard is part of the month-1 MVP scope.

**Steps**  
- Discuss with founders/product which views are needed (if any) in month 1.  
- Decide between: no dashboard, internal-only dashboard, or minimal external dashboard.  
- Document the decision clearly.  
- Update the MVP scope and timeline accordingly.

**Definition of Done**  
- There is a clear yes/no decision on including a dashboard in the MVP.  
- If “yes”, basic dashboard requirements are documented.  
- The developer knows whether to implement Phase 7 in this milestone or postpone it.

---

# PHASE 1 – Setup & Infrastructure

## Parent Issue: [P1] Phase 1 – Project Setup & Infrastructure

### Metadata
Start Date: 2025-12-04
Due Date: 2025-12-08

Milestone: Phase 1 – Setup & Infrastructure  
Labels: ["MVP", "backend", "infra"]  
Description:  
  Initial setup of the backend system, project structure, Docker, CI/CD and server environment for the IMB Trading Bot MVP.

### Subtasks (Checklist inside parent issue)
- [ ] [T1.1] Create Git repository and initialize backend project
- [ ] [T1.2] Define project folder structure (core/, exchange/, config/, api/)
- [ ] [T1.3] Add Dockerfile + docker-compose with backend container
- [ ] [T1.4] Launch AWS EC2 instance for DEV environment
- [ ] [T1.5] Setup basic CI/CD pipeline (GitHub Actions: tests + build + deploy)

#### [T1.1] Create Git repository and initialize backend project

### Metadata
Start Date: 2025-12-04
Due Date: 2025-12-08


**Goal**  
Create the backend codebase for the IMB Trading Bot with a clean, minimal starting point (FastAPI or Django).

**Steps**  
- Initialize a new Git repository (if not already created on GitHub).  
- Create a minimal backend project using FastAPI or Django REST.  
- Add a simple health-check endpoint (e.g., `/health`) that returns a static response.  
- Commit the initial codebase and push it to GitHub.

**Definition of Done**  
- Backend project builds and runs locally.  
- `/health` endpoint responds successfully (HTTP 200).  
- Code is committed and available in the `imb-trading-bot` repository on GitHub.

---

#### [T1.2] Define project folder structure (core/, exchange/, config/, api/)

### Metadata
Start Date: 2025-12-04
Due Date: 2025-12-08


**Goal**  
Define a clear, extendable folder structure for the backend code that matches the planned architecture.

**Steps**  
- Create top-level folders such as: `core/`, `exchange/`, `config/`, `api/`, `tests/`.  
- Add `__init__.py` files where needed to make packages importable.  
- Document the structure briefly in a README or developer note.  
- Ensure imports work correctly for a minimal module in each folder.

**Definition of Done**  
- The repository has a well-defined folder structure.  
- Python modules import correctly without errors.  
- Structure matches the expected architecture (Trading Core, Exchange Connector, API layer, config).

---

#### [T1.3] Add Dockerfile + docker-compose with backend container

### Metadata
Start Date: 2025-12-04
Due Date: 2025-12-08


**Goal**  
Containerize the backend application so it can run consistently across environments using Docker.

**Steps**  
- Create a `Dockerfile` that builds the backend image (install Python dependencies, copy source code, run app).  
- Create a `docker-compose.yml` that starts the backend container (and any basic dependencies if needed).  
- Verify that the backend runs correctly using `docker-compose up`.  
- Adjust any environment variables needed for local development inside Docker.

**Definition of Done**  
- `docker-compose up` successfully starts the backend service.  
- The health-check endpoint is reachable from the host machine through the container’s port.  
- The Dockerfile is optimized enough for development use (no obvious issues).

---

#### [T1.4] Launch AWS EC2 instance for DEV environment

### Metadata
Start Date: 2025-12-04
Due Date: 2025-12-08


**Goal**  
Create a development EC2 instance on AWS to host the backend and possibly other components for the MVP.

**Steps**  
- Choose an appropriate EC2 instance type (e.g., t3.small or similar).  
- Configure security groups to allow necessary ports (e.g., SSH, HTTP/HTTPS).  
- Install Docker and Docker Compose on the EC2 instance.  
- Test pulling the backend image and running the backend container on EC2.

**Definition of Done**  
- EC2 instance is up and reachable via SSH.  
- Docker and Docker Compose are installed and working.  
- Backend container can run on EC2 and respond to requests (at least internally).

---

#### [T1.5] Setup basic CI/CD pipeline (GitHub Actions: tests + build + deploy)

### Metadata
Start Date: 2025-12-04
Due Date: 2025-12-08


**Goal**  
Automate the build and basic testing of the backend with GitHub Actions and optionally auto-deploy to the DEV EC2.

**Steps**  
- Create a GitHub Actions workflow YAML file (e.g., `.github/workflows/backend-ci.yml`).  
- Add steps for: checkout code, install dependencies, run tests (or at least `pytest` placeholder).  
- Add steps to build the Docker image.  
- (Optional) Add a deployment step to push the image or deploy to EC2.  
- Ensure the workflow runs on each push to `main` (or selected branches).

**Definition of Done**  
- CI pipeline runs automatically on new commits/pull requests.  
- Build stage passes without errors.  
- At least one basic test step is executed (even if minimal).  
- Failures are visible in the GitHub Actions interface.

---

# PHASE 2 – Exchange Connector

## Parent Issue: [P2] Phase 2 – Exchange Connector

### Metadata
Start Date: 2025-12-09
Due Date: 2025-12-13

Milestone: Phase 2 – Exchange Connector  
Labels: ["MVP", "exchange", "backend"]  
Description:  
  Implement the connection to the chosen exchange using ccxt, including basic market data retrieval and health-check.

### Subtasks (Checklist inside parent issue)
- [ ] [T2.1] Install ccxt library for exchange integration
- [ ] [T2.2] Implement basic ExchangeConnector including API key loading
- [ ] [T2.3] Implement get_ohlcv and get_ticker functions
- [ ] [T2.4] Implement exchange health-check function
- [ ] [T2.5] Create API endpoint to return market data from ExchangeConnector

#### [T2.1] Install ccxt library for exchange integration

### Metadata
Start Date: 2025-12-09
Due Date: 2025-12-13


**Goal**  
Add the `ccxt` library to the project to simplify integration with the chosen exchange.

**Steps**  
- Add `ccxt` to the project dependencies (requirements file or pyproject).  
- Install the library locally and confirm it imports successfully.  
- Commit the updated dependency configuration.

**Definition of Done**  
- `import ccxt` works without errors.  
- Dependency file includes `ccxt` and is committed.  
- CI pipeline passes with the new dependency.

---

#### [T2.2] Implement basic ExchangeConnector including API key loading

### Metadata
Start Date: 2025-12-09
Due Date: 2025-12-13


**Goal**  
Create a reusable ExchangeConnector module responsible for initializing the ccxt client with proper API keys and configuration.

**Steps**  
- Create an `ExchangeConnector` class or module in `exchange/`.  
- Load API keys and configuration from environment variables or config files.  
- Initialize the ccxt client for the chosen exchange (Testnet).  
- Provide a simple method (e.g., `ping` or `get_status`) to verify connectivity.

**Definition of Done**  
- ExchangeConnector initializes successfully with valid Testnet keys.  
- No secrets are hard-coded in the source code.  
- A simple connectivity check works (e.g., fetching server time or balance).

---

#### [T2.3] Implement get_ohlcv and get_ticker functions

### Metadata
Start Date: 2025-12-09
Due Date: 2025-12-13


**Goal**  
Provide reusable methods for retrieving OHLCV candles and the latest ticker from the exchange via the ExchangeConnector.

**Steps**  
- Add a method `get_ohlcv(symbol, timeframe, limit)` using ccxt.  
- Add a method `get_ticker(symbol)` using ccxt.  
- Handle basic error cases (e.g., invalid symbol, network issues).  
- Ensure both methods return data in a consistent internal format.

**Definition of Done**  
- Calling `get_ohlcv` returns a valid candle list for a known symbol.  
- Calling `get_ticker` returns current price information.  
- Errors are logged and do not crash the process unexpectedly.

---

#### [T2.4] Implement exchange health-check function

### Metadata
Start Date: 2025-12-09
Due Date: 2025-12-13


**Goal**  
Provide a dedicated health-check function to verify that the ExchangeConnector and exchange API are operational.

**Steps**  
- Implement a `health_check()` method that performs a minimal API call (e.g., server time or ping).  
- Wrap the call in try/except to catch network/API errors.  
- Return a structured result (e.g., `{ "status": "ok" | "error", "details": ... }`).  
- Integrate it with the backend health-check endpoint if needed.

**Definition of Done**  
- `health_check()` reports “ok” when the exchange is reachable.  
- Failure cases return “error” with diagnostics instead of raising unhandled exceptions.  
- The backend can expose an endpoint reflecting exchange health if applicable.

---

#### [T2.5] Create API endpoint to return market data from ExchangeConnector

### Metadata
Start Date: 2025-12-09
Due Date: 2025-12-13


**Goal**  
Expose an HTTP endpoint so external tools or dashboards can access market data via the backend.

**Steps**  
- Add a new route (e.g., `/market-data`) in the API layer.  
- Use the ExchangeConnector to fetch ticker/ohlcv for requested symbols.  
- Define request/response models if using FastAPI (Pydantic).  
- Add basic parameter validation (symbol, timeframe, limit).  
- Test the endpoint manually (e.g., with Postman).

**Definition of Done**  
- `/market-data` endpoint returns valid market data.  
- Invalid inputs return proper error responses (HTTP 4xx).  
- Endpoint is documented or discoverable (e.g., via OpenAPI in FastAPI).

---

# PHASE 3 – Trading Core (Rule-Based + Paper Trading)

## Parent Issue: [P3] Phase 3 – Trading Core

### Metadata
Start Date: 2025-12-14
Due Date: 2025-12-19

Milestone: Phase 3 – Trading Core  
Labels: ["MVP", "backend"]  
Description:  
  Implement strategy logic, risk management, execution engine, and a paper-trading loop to simulate trading without real funds.

### Subtasks (Checklist inside parent issue)
- [ ] [T3.1] Implement simple rule-based strategy (RSI/EMA)
- [ ] [T3.2] Implement Risk Manager (basic rules: max trades/day etc.)
- [ ] [T3.3] Implement Execution Engine (build order objects)
- [ ] [T3.4] Implement Paper Trading (simulate trades without real API calls)
- [ ] [T3.5] Create trading loop: Fetch → Strategy → Risk → Execute

#### [T3.1] Implement simple rule-based strategy (RSI/EMA)

### Metadata
Start Date: 2025-12-14
Due Date: 2025-12-19


**Goal**  
Create a basic rule-based strategy module that generates BUY/SELL/HOLD signals based on technical indicators like RSI or EMA.

**Steps**  
- Define a common signal format (e.g., action, symbol, size_type, size_value, stop_loss, take_profit).  
- Implement indicator calculation logic (using OHLCV data).  
- Implement simple rules (e.g., RSI < 30 → BUY, RSI > 70 → SELL).  
- Make strategy parameters configurable (timeframe, thresholds).

**Definition of Done**  
- Strategy module can be called with market data and returns a well-structured signal.  
- Signals conform to the agreed format.  
- Strategy behavior can be easily changed via parameters (not hard-coded only).

---

#### [T3.2] Implement Risk Manager (basic rules: max trades/day etc.)

### Metadata
Start Date: 2025-12-14
Due Date: 2025-12-19


**Goal**  
Add a Risk Manager component that validates strategy signals against risk constraints before execution.

**Steps**  
- Implement rules such as: max trades per day, max open positions, max daily loss.  
- Create a method like `validate_signal(signal)` that returns approved/rejected + reason.  
- Track relevant metrics in memory or storage (trades count, realized PnL, etc.).  
- Integrate Risk Manager into the trading flow before Execution Engine.

**Definition of Done**  
- Risk Manager can reject unsafe signals and provide a reason.  
- Risk constraints are configurable.  
- Trading flow uses Risk Manager consistently before placing orders.

---

#### [T3.3] Implement Execution Engine (build order objects)

### Metadata
Start Date: 2025-12-14
Due Date: 2025-12-19


**Goal**  
Implement an Execution Engine that receives validated signals and converts them into standardized order objects ready for execution.

**Steps**  
- Define an internal Order object/structure (symbol, side, quantity, price, type, metadata).  
- Implement a method `build_order_from_signal(signal)` that calculates quantity based on strategy configuration and account info (for now, can use fixed size or percent).  
- Ensure the engine does not yet call the exchange (that is for later phases).  
- Add logging for each built order.

**Definition of Done**  
- Execution Engine outputs valid Order objects for BUY/SELL signals.  
- Quantity calculation logic is clear and configurable.  
- No external side effects (no live orders yet).  
- At least one unit test verifies order creation logic.

---

#### [T3.4] Implement Paper Trading (simulate trades without real API calls)

### Metadata
Start Date: 2025-12-14
Due Date: 2025-12-19


**Goal**  
Simulate trade execution using order objects without interacting with the real exchange, for safe MVP testing.

**Steps**  
- Create a Paper Trading module that receives Order objects and simulates fills based on market prices.  
- Maintain in-memory or simple in-file portfolio (positions, cash, PnL).  
- Apply basic trading costs (e.g., fees, spread simulation if desired).  
- Log all simulated trades and results.

**Definition of Done**  
- Orders sent to Paper Trading produce simulated trades with entry price and quantity.  
- Portfolio state updates correctly after each trade.  
- It is possible to inspect paper-trading results (logs or in-memory data).

---

#### [T3.5] Create trading loop: Fetch → Strategy → Risk → Execute

### Metadata
Start Date: 2025-12-14
Due Date: 2025-12-19


**Goal**  
Build a continuous or scheduled trading loop that orchestrates the full flow of data: market data → strategy → risk → execution (paper).

**Steps**  
- Implement a loop or scheduled task that periodically fetches market data.  
- Call the strategy to generate signals.  
- Pass signals through Risk Manager.  
- Convert approved signals into orders via Execution Engine.  
- Route orders to Paper Trading module.  
- Add logging around each loop iteration.

**Definition of Done**  
- The trading loop can run for multiple iterations without crashing.  
- Logs show the full flow from data to simulated trades.  
- There is a simple way to start/stop the loop (e.g., CLI command, flag, or API call).

---

# PHASE 4 – Live Testnet Integration

## Parent Issue: [P4] Phase 4 – Live Testnet Integration

### Metadata
Start Date: 2025-12-20
Due Date: 2025-12-23

Milestone: Phase 4 – Live Testnet  
Labels: ["MVP", "exchange"]  
Description:  
  Enable live trading on Testnet by integrating real order placement while keeping the option for paper trading.

### Subtasks (Checklist inside parent issue)
- [ ] [T4.1] Add mode switching: PAPER vs LIVE_TESTNET
- [ ] [T4.2] Implement place_order on Testnet using ExchangeConnector
- [ ] [T4.3] Perform live Testnet trade tests with minimal amounts

#### [T4.1] Add mode switching: PAPER vs LIVE_TESTNET

### Metadata
Start Date: 2025-12-20
Due Date: 2025-12-23


**Goal**  
Allow the system to run either in paper-trading mode or Testnet live-trading mode using a configuration flag.

**Steps**  
- Introduce a configuration setting (env var or config file) for `TRADING_MODE`.  
- Update the trading loop or execution pipeline to branch between paper and live modes.  
- Ensure the code path is clear and safe (no accidental live trading when PAPER is expected).  
- Log which mode is currently active on startup.

**Definition of Done**  
- It is possible to select PAPER or LIVE_TESTNET via configuration.  
- Paper mode behaves exactly as before.  
- Live mode does not affect real funds (Testnet only).  
- The current mode is visible in logs.

---

#### [T4.2] Implement place_order on Testnet using ExchangeConnector

### Metadata
Start Date: 2025-12-20
Due Date: 2025-12-23


**Goal**  
Connect the Execution Engine to the exchange to place real Testnet orders when in LIVE_TESTNET mode.

**Steps**  
- Add a method to ExchangeConnector to place Spot orders on Testnet.  
- Map internal Order objects to ccxt order parameters.  
- Handle success and error responses (e.g., insufficient balance, invalid symbol).  
- Log all placed orders and responses (without exposing secrets).

**Definition of Done**  
- A valid Testnet order can be placed via the Execution Engine + ExchangeConnector.  
- Errors are handled and logged properly.  
- Orders created in LIVE_TESTNET mode appear in the Testnet account order history.

---

#### [T4.3] Perform live Testnet trade tests with minimal amounts

### Metadata
Start Date: 2025-12-20
Due Date: 2025-12-23


**Goal**  
Verify that the live Testnet integration behaves as expected by running a few real Testnet trades.

**Steps**  
- Choose a low-value symbol and minimal trade size suitable for Testnet.  
- Run the trading loop in LIVE_TESTNET mode for a short period.  
- Verify that trades appear in the Testnet account.  
- Review logs to confirm correct behavior of strategy, risk, and execution.

**Definition of Done**  
- At least a few Testnet trades are successfully executed.  
- No unexpected large trades or errors occur.  
- Logs confirm that the full trading flow in LIVE_TESTNET mode works as intended.

---

# PHASE 5 – Database Layer

## Parent Issue: [P5] Phase 5 – Database Layer

### Metadata
Start Date: 2025-12-24
Due Date: 2025-12-27

Milestone: Phase 5 – Database  
Labels: ["MVP", "database", "backend"]  
Description:  
  Add persistent storage using PostgreSQL RDS for orders, trades, and positions, and expose them via API endpoints.

### Subtasks (Checklist inside parent issue)
- [ ] [T5.1] Deploy PostgreSQL RDS instance
- [ ] [T5.2] Create DB models: Orders, Trades, Positions
- [ ] [T5.3] Save Orders and Trades to DB
- [ ] [T5.4] Store and update Position states in DB
- [ ] [T5.5] Add API endpoint to fetch orders/trades history

#### [T5.1] Deploy PostgreSQL RDS instance

### Metadata
Start Date: 2025-12-24
Due Date: 2025-12-27


**Goal**  
Provision a managed PostgreSQL database on AWS RDS for storing trading data.

**Steps**  
- Create a PostgreSQL RDS instance with appropriate size and storage.  
- Configure security groups to allow access from the EC2 instance only.  
- Store DB credentials securely (env vars, secrets manager, etc.).  
- Test connectivity from the backend container to the RDS instance.

**Definition of Done**  
- RDS instance is running and reachable from the backend.  
- DB credentials are not hard-coded.  
- Basic SQL connection test succeeds (e.g., simple SELECT 1).

---

#### [T5.2] Create DB models: Orders, Trades, Positions

### Metadata
Start Date: 2025-12-24
Due Date: 2025-12-27


**Goal**  
Define the schema and ORM models (if using ORM) for Orders, Trades, and Positions.

**Steps**  
- Design table structures for Orders, Trades, and Positions (fields, keys, relationships).  
- Implement models using an ORM (e.g., SQLAlchemy) or raw SQL.  
- Apply migrations (if using a migration tool).  
- Document the schema briefly in a developer note.

**Definition of Done**  
- The database contains tables for Orders, Trades, and Positions.  
- Models can be imported and used in the backend code.  
- Migrations apply cleanly without errors.

---

#### [T5.3] Save Orders and Trades to DB

### Metadata
Start Date: 2025-12-24
Due Date: 2025-12-27


**Goal**  
Persist Orders and Trades to the database whenever simulated or live trades occur.

**Steps**  
- Integrate DB writes into the Execution Engine / trading pipeline.  
- Save all relevant fields for each order (symbol, side, quantity, timestamps, mode).  
- Save trade execution information (fill price, quantity, fees if available).  
- Ensure that write failures are logged and handled gracefully.

**Definition of Done**  
- New orders result in rows in the Orders table.  
- Completed trades result in rows in the Trades table.  
- DB writes do not significantly slow down the trading loop.

---

#### [T5.4] Store and update Position states in DB

### Metadata
Start Date: 2025-12-24
Due Date: 2025-12-27


**Goal**  
Maintain an up-to-date representation of open and closed positions in the database.

**Steps**  
- Define logic for opening, updating, and closing positions based on trades.  
- Update positions table whenever a trade is executed.  
- Track metrics like average entry price, current size, realized PnL.  
- Ensure consistency between Orders, Trades, and Positions.

**Definition of Done**  
- Positions table accurately reflects open positions.  
- Closing a position updates the position state and realized PnL.  
- There are no obvious mismatches between Trades and Positions.

---

#### [T5.5] Add API endpoint to fetch orders/trades history

### Metadata
Start Date: 2025-12-24
Due Date: 2025-12-27


**Goal**  
Expose an API endpoint that returns historical Orders and Trades for review or for a dashboard.

**Steps**  
- Add an endpoint (e.g., `/history/orders` and/or `/history/trades`).  
- Implement pagination or filtering (by date, symbol, etc.) as needed.  
- Serialize DB models to JSON response.  
- Test the endpoint manually.

**Definition of Done**  
- API endpoint returns historical data correctly.  
- Invalid queries are handled with proper error responses.  
- Endpoint is safe to expose (no secrets, no unnecessary internal fields).

---

# PHASE 6 – Logging, Monitoring, Security

## Parent Issue: [P6] Phase 6 – Monitoring & Security

### Metadata
Start Date: 2025-12-28
Due Date: 2026-01-01

Milestone: Phase 6 – Monitoring & Security  
Labels: ["MVP", "infra"]  
Description:  
  Configure logging, monitoring, alerts, and secure key management to ensure stability and safety of the MVP.

### Subtasks (Checklist inside parent issue)
- [ ] [T6.1] Send backend logs to CloudWatch Logs
- [ ] [T6.2] Add CloudWatch metrics (CPU, errors, trade count)
- [ ] [T6.3] Setup CloudWatch alerts for critical failures
- [ ] [T6.4] Implement secure storage for API keys (KMS or encrypted file)

#### [T6.1] Send backend logs to CloudWatch Logs

### Metadata
Start Date: 2025-12-28
Due Date: 2026-01-01


**Goal**  
Centralize backend logs in AWS CloudWatch for easier debugging and monitoring.

**Steps**  
- Configure application logging to write to stdout/stderr in a structured way.  
- Setup CloudWatch Logs agent or integration for the EC2 instance / container.  
- Create a dedicated log group for the IMB Trading Bot.  
- Verify that logs appear in CloudWatch.

**Definition of Done**  
- Backend logs are visible in CloudWatch Logs.  
- Log groups and streams are organized logically.  
- It is possible to search for specific errors or events.

---

#### [T6.2] Add CloudWatch metrics (CPU, errors, trade count)

### Metadata
Start Date: 2025-12-28
Due Date: 2026-01-01


**Goal**  
Monitor key metrics (resource usage and trading behavior) using CloudWatch Metrics.

**Steps**  
- Ensure EC2-level metrics (CPU, memory if available) are tracked.  
- Expose custom application metrics (e.g., trade count, error count) via CloudWatch.  
- Define metric namespaces and dimensions.  
- Confirm that metrics appear and update over time.

**Definition of Done**  
- CPU and basic resource metrics are visible in CloudWatch.  
- Custom metrics such as trade count and error count are tracked.  
- Metrics can be graphed over time.

---

#### [T6.3] Setup CloudWatch alerts for critical failures

### Metadata
Start Date: 2025-12-28
Due Date: 2026-01-01


**Goal**  
Create alerts to notify about critical conditions such as high error rates or system failures.

**Steps**  
- Define thresholds for critical metrics (e.g., error count over X in Y minutes).  
- Create CloudWatch Alarms for these metrics.  
- Configure notifications (e.g., email, SNS topic).  
- Test alarms by simulating an error condition.

**Definition of Done**  
- CloudWatch Alarms are created for key metrics.  
- Notifications are delivered when thresholds are exceeded.  
- The system can be monitored without manually checking logs all the time.

---

#### [T6.4] Implement secure storage for API keys (KMS or encrypted file)

### Metadata
Start Date: 2025-12-28
Due Date: 2026-01-01


**Goal**  
Ensure that API keys and other secrets are stored and accessed securely, not hard-coded or exposed.

**Steps**  
- Choose a secure storage mechanism (AWS KMS, Secrets Manager, or encrypted config file).  
- Update the ExchangeConnector and related modules to load keys from this secure source.  
- Remove any plain-text secrets from code and config files.  
- Document the secret management approach.

**Definition of Done**  
- No secrets are stored in plain text in the repository.  
- API keys are loaded from a secure location at runtime.  
- The chosen method complies with basic security best practices.

---

# PHASE 7 – Dashboard (Optional)

## Parent Issue: [P7] Phase 7 – Dashboard (Optional)

### Metadata
Start Date: 2026-01-02
Due Date: 2026-01-10

Milestone: Phase 7 – Dashboard  
Labels: ["MVP", "dashboard"]  
Description:  
  If included in MVP, implement a basic dashboard for monitoring bot activity, orders, and status.

### Subtasks (Checklist inside parent issue)
- [ ] [T7.1] Create basic frontend project (React/Next)
- [ ] [T7.2] Add page to show orders/trades from API
- [ ] [T7.3] Add bot status page (running / stopped / errors)

#### [T7.1] Create basic frontend project (React/Next)

### Metadata
Start Date: 2026-01-02
Due Date: 2026-01-10


**Goal**  
Initialize a minimal frontend project to serve as a dashboard for the IMB Trading Bot.

**Steps**  
- Create a new React or Next.js project in a `frontend/` directory or separate repo.  
- Configure basic routing and layout.  
- Integrate environment configuration for API base URL.  
- Commit and push the initial frontend code.

**Definition of Done**  
- Frontend project runs locally with `npm run dev` or equivalent.  
- Basic home page is accessible in the browser.  
- Project is under version control (GitHub).

---

#### [T7.2] Add page to show orders/trades from API

### Metadata
Start Date: 2026-01-02
Due Date: 2026-01-10


**Goal**  
Display historical orders and trades fetched from the backend API.

**Steps**  
- Create a page (e.g., `/orders` or `/history`) in the frontend.  
- Call the backend history API endpoints (orders/trades).  
- Render the data in a table or list with basic columns (symbol, side, size, time).  
- Handle loading and error states gracefully.

**Definition of Done**  
- The dashboard shows a list of orders/trades pulled from the backend.  
- Errors are handled with user-friendly messages.  
- The UI is clear enough for internal users.

---

#### [T7.3] Add bot status page (running / stopped / errors)

### Metadata
Start Date: 2026-01-02
Due Date: 2026-01-10


**Goal**  
Provide a simple page showing the current status of the bot (running, stopped, last error).

**Steps**  
- Expose a backend endpoint that returns bot status (mode, last run, any recent error).  
- Create a frontend page (e.g., `/status`) that calls this endpoint.  
- Display key information (mode: PAPER/LIVE_TESTNET, last trade time, status text).  
- Update automatically every X seconds (optional).

**Definition of Done**  
- Status page shows whether the bot is running and in which mode.  
- Errors or abnormal states are visible on the page.  
- The page is accessible from the dashboard navigation.

---

# AGENT INSTRUCTIONS

For each Parent Issue section:
- Create a new GitHub Issue with the title:
  - e.g., `[P1] Phase 1 – Project Setup & Infrastructure`
- Use the "Description" paragraph under the parent.
- Assign the Milestone specified for that phase.
- Apply the Labels listed for that parent.
- In the parent issue body, include the checklist under "Subtasks".

For each Subtask section:
- Create a separate GitHub Issue with title:
  - `<Task ID> – <Task Description>`
  - e.g., `T1.1 – Create Git repository and initialize backend project`
- Use the **Goal**, **Steps**, and **Definition of Done** as the issue body.
- Assign the same Milestone as the corresponding parent phase.
- Apply the Labels from the parent issue (and add more if desired, e.g., "backend", "infra", "exchange", "database", "dashboard").
- In the corresponding parent issue, link each subtask using GitHub task-list syntax (`- [ ]`).

Start Date / Due Date:
- For each issue, set "Start Date" and "Due Date" fields according to the planned Gantt timeline.
- All created issues should be added to the GitHub Project:
  - Project: **"IMB Trading Bot – MVP"**
  - Column: **"Todo"**