**Architecture:**
	•	Framework: FastAPI (Python)
	•	Containerization: Docker
	•	AWS Services:
	•	App Runner: Runs the containerized API.
	•	RDS (PostgreSQL): Main database for persistent data (donor/contact records, etc).
	•	ElastiCache (Redis): For fast caching and queueing needs.
	•	S3: Storage of raw data files (e.g., donor exports, receipts).
	•	Networking: App Runner is configured to communicate securely with RDS and ElastiCache using VPC and security groups.
	•	Environment Variables: Sensitive configuration (DB credentials, AWS keys, Redis URL) are injected at runtime for security.

**Basic Flow:**
	1.	API calls come in through App Runner.
	2.	FastAPI processes requests, interacts with PostgreSQL (RDS) for persistent data.
	3.	Caching/queueing or quick lookups use Redis (ElastiCache).
	4.	Any bulk/raw files are read from or stored to S3.
