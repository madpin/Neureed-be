# NeuReed Backend

A powerful, AI-enhanced RSS feed aggregator backend built with Python and FastAPI. NeuReed intelligently organizes, analyzes, and personalizes your content consumption experience using machine learning and semantic search.

## 🚀 Overview

NeuReed is a next-generation RSS feed reader backend that goes beyond simple feed aggregation. It leverages modern AI/ML techniques including vector embeddings, semantic search, and personalized content scoring to help users discover and consume content more effectively.

With **51 comprehensive backend features**, NeuReed provides enterprise-grade functionality including advanced search capabilities, AI-powered personalization, system monitoring, database maintenance, robust logging and admin tooling for a complete content aggregation platform.

## ✨ Key Features

### 🔐 Authentication & Authorization
- **OAuth Integration**: Google, GitHub, and generic OAuth2 providers
- **JWT Session Management**: Secure token-based authentication
- **Multi-tenancy**: Complete user data isolation
- **Role-Based Access Control**: ADMIN, USER, and GUEST roles with role assignment and permission checking
- **API Key Management**: Encrypted API key storage and management
- **User Role Management**: Dynamic role updates and role-based endpoint protection

### 📰 Smart Feed Management
- **Universal Feed Support**: RSS and Atom feed parsing
- **Feed Health Monitoring**: Automatic health tracking and status updates
- **Conditional Requests**: Efficient fetching with ETag and Last-Modified headers
- **Auto-disable**: Configurable failure thresholds with automatic feed disabling
- **Feed Deduplication**: Intelligent URL-based duplicate detection
- **Custom Settings**: Per-user feed naming and configuration
- **Manual Article Refresh**: Force article re-fetch per feed with refresh statistics and job queueing

### 📊 Article Management
- **Smart Deduplication**: GUID/URL/content hash-based duplicate detection
- **Rich Metadata**: Automatic extraction of title, author, excerpt, images, and dates
- **Read/Unread Tracking**: Per-user article status management
- **Retention Policies**: Age-based and count-based article cleanup
- **Content Extraction**: Multiple extraction strategies with fallback support:
  - **Newspaper3k**: Fast, multi-language article extraction
  - **Trafilatura**: High-quality content extraction optimized for accuracy
  - **readability-lxml**: Mozilla Readability port for clean content
  - **Goose3**: Advanced article extraction with metadata
  - **Playwright**: Optional JavaScript-rendered content support for dynamic sites
- **Selective Deletion**: Feed-specific article deletion and manual pruning with deletion statistics
- **Intelligent Update Detection**: Checks for article updates before extraction; only extracts data if not already extracted, but automatically re-extracts when article updates are detected

### 🔍 Advanced Search & Discovery
- **Full-Text Search**: Search across titles, content, and authors
- **Semantic Search**: Vector-based similarity search using embeddings
- **Hybrid Search**: Combined semantic + keyword search with weighted scoring and result merging
- **Search Templates**: Pre-defined query templates for common use cases (technology, news, research, jobs)
- **Autocomplete & Suggestions**: Real-time search query suggestions with partial matching
- **Related Articles**: AI-powered content recommendations
- **Recency Scoring**: Configurable time-based relevance decay
- **Search Ranking**: Multi-factor relevance scoring with duplicate detection

### 💾 Saved Searches
- **Complex Query Syntax**: Support for AND, OR, NOT operators and phrase matching
- **AST-Based Parsing**: Abstract Syntax Tree generation for query optimization
- **Automatic Matching**: Real-time article matching against saved searches
- **Relevance Scoring**: 0-1 scale relevance with match reason tracking
- **Daily Digests**: Automated digest generation for matched content

### 🤖 AI/ML Capabilities

#### Vector Embeddings
- **Multi-Provider Support**: OpenAI and local embedding models
- **Efficient Storage**: PostgreSQL pgvector with HNSW indexing
- **Batch Processing**: Optimized bulk embedding generation
- **Streaming Embeddings**: Memory-efficient processing with 80% peak memory reduction
- **Cost Tracking**: Per-user embedding cost monitoring
- **Smart Fallback**: Provider cascade (user → admin → system)
- **Progressive Generation**: Small batch processing with immediate writes for large datasets

#### Content Summarization
- **On-Demand Summaries**: AI-generated article summaries
- **Key Point Extraction**: 3-5 main takeaways per article
- **Topic Detection**: Automatic tagging and categorization
- **Multiple LLM Providers**: OpenAI (GPT-4o, GPT-4o-mini) and Ollama (Llama 3.1, Qwen 2.5)
- **Token Tracking**: Detailed usage and cost analytics

#### Personalization
- **Pattern Learning**: TF-IDF-based user preference detection
- **Feedback Integration**: Explicit (thumbs up/down) and implicit (reading time, bounce rate) learning
- **Time Decay**: 10% pattern weight decay per 30 days
- **Relevance Scoring**: Personalized article ranking with score explanations
- **Adaptive Learning**: Continuous improvement based on user behavior
- **Pattern Reset**: User-initiated preference clearing with backup capability

### 📁 Organization

#### Categories
- **Hierarchical Structure**: Parent-child category relationships
- **Visual Customization**: Icons, colors, and custom ordering
- **Settings Cascade**: Category-level configuration inheritance
- **Feed Assignment**: Flexible feed-to-category mapping
- **Drag-and-Drop Support**: Custom category ordering with persistence

#### Tags
- **User-Defined Tags**: Custom tagging system for feeds
- **Tag-Based Filtering**: Fast GIN-indexed tag queries
- **Bulk Operations**: Multi-feed tag management

### 🔄 Bulk Operations
- **Multi-Feed Updates**: Batch category, tag, and settings changes
- **Partial Failure Handling**: Robust error handling with detailed results
- **Authorization Verification**: Secure bulk operation execution
- **Result Aggregation**: Success/failure statistics

### 📤 OPML Import/Export
- **OPML 2.0 Support**: Full standard compliance
- **Category Preservation**: Maintain feed organization during import/export
- **Deduplication**: Smart feed duplicate handling during import
- **Import Validation**: Comprehensive feed validation and error reporting

### ⏰ Job Scheduling System
- **Cron-Based Scheduling**: Flexible job timing with cron expressions
- **Distributed Locking**: Prevention of duplicate job execution
- **Job Monitoring**: Status tracking, duration measurement, and history
- **Multiple Job Types**:
  - Feed refresh and article extraction
  - Article cleanup and retention enforcement
  - Pattern decay calculation
  - Embedding generation
  - Daily digest creation

### 🔔 Notification System
- **In-App Notifications**: Rich, metadata-enabled notifications
- **Multiple Types**: Feed refresh, health alerts, errors, and info messages
- **Smart Batching**: Max 1 notification per feed per hour
- **Notification Management**: Mark as read, bulk operations, and automatic cleanup

### ⚙️ Configuration & Settings

#### User Preferences
- **UI Customization**: Theme, font size, article layout
- **Behavior Settings**: Auto-mark as read, articles per page, default views
- **AI Configuration**: LLM provider and model selection
- **Display Options**: Reading panel, sidebar state, typography

#### LLM Configuration
- **Multi-Level Setup**: User and admin-level configurations
- **Provider Management**: Enable/disable providers, API key storage
- **Model Selection**: Per-feature model configuration (summary, embedding, digest)
- **Cost Controls**: Rate limiting and cost limit enforcement

#### Settings Cascade
- **Priority Resolution**: Feed → Category → User → System
- **Configurable Options**: Refresh intervals, retention periods, extraction methods
- **Default Management**: System-wide default values

### 💰 Cost Tracking & Analytics
- **Per-User Tracking**: Detailed embedding and summarization costs
- **Token Counting**: Input/output token usage monitoring
- **Provider Pricing**: Real-time cost calculation
- **Analytics Dashboard**: Daily/monthly cost aggregation and reporting
- **Redis-Based Storage**: High-performance cost data management

### 🗄️ Caching System
- **Redis Integration**: Cache-aside pattern with TTL-based expiration
- **Pattern-Based Invalidation**: Smart cache clearing strategies
- **Multiple Cache Types**:
  - Article scores (1 hour)
  - Feed data (5 minutes)
  - Query AST (24 hours)
  - Summarization results (1 hour)
- **Performance Monitoring**: Cache hit/miss statistics
- **LRU Eviction**: Automatic cache size management with quota monitoring

### 🛡️ Security Features
- **Input Validation**: Zod schema-based request validation
- **HTML Sanitization**: XSS prevention for user content
- **SSRF Protection**: Safe URL fetching with validation
- **Encryption**: API key and cookie encryption at rest
- **SQL Injection Prevention**: Parameterized queries throughout
- **Rate Limiting**: API request throttling
- **CORS Configuration**: Secure cross-origin resource sharing

### 📝 Logging & Monitoring
- **Centralized Logging**: Comprehensive system-wide logging infrastructure
- **Log Levels**: ERROR, WARNING, INFO, and DEBUG level support
- **Admin Dashboard**: Easy-to-use interface for log access and analysis
- **Advanced Filtering**: Filter logs by level, timestamp, service, user, or custom criteria
- **Debug Control**: Admin-configurable debug logging toggle for production environments
- **Log Retention**: Configurable log retention policies with automatic cleanup
- **Structured Logging**: JSON-formatted logs for easy parsing and analysis
- **Real-Time Viewing**: Live log streaming for active monitoring
- **Search Capabilities**: Full-text search across log messages
- **Export Options**: Download logs for external analysis and archiving

### 👨‍💼 Admin Features
- **System Management**: Global settings and configuration with validation rules
- **User Administration**: User management, role assignment, and monitoring
- **Job Monitoring**: Dashboard for scheduled job oversight with manual triggering
- **Cost Visibility**: Cross-user cost analytics and reporting
- **Health Monitoring**: System-wide health checks and error logs
- **Manual Controls**: Job triggering and system maintenance
- **Database Maintenance**: VACUUM, ANALYZE, REINDEX operations with scheduling
- **Redis Maintenance**: FLUSHDB, SAVE, BGSAVE, BGREWRITEAOF operations
- **Memory Monitoring**: Real-time heap, RSS, and memory pressure tracking with analytics dashboard
- **Database Reset**: Admin-triggered database reset with seed data generation
- **System Configuration**: Constraint enforcement and default value management
- **Centralized Logging System**: Robust logging with easy admin access, filterable by level (ERROR, WARNING, INFO, DEBUG) with admin-controlled debug logging toggle

### 🚄 Performance Optimization
- **Database Optimization**: Connection pooling, query optimization, strategic indexing
- **Batch Processing**: Efficient bulk operations with streaming support
- **Vector Search**: HNSW index for fast semantic search with index rebuilding
- **Lazy Loading**: On-demand content loading
- **Caching Strategies**: Multi-layer caching for frequently accessed data
- **Content Proxy**: CORS-safe content fetching with in-memory LRU cache (10MB limit, configurable TTL)
- **Memory Efficiency**: Streaming embeddings for 80% memory reduction on large datasets

### 📈 Analytics & Insights
- **Engagement Tracking**: User behavior and interaction patterns
- **Feed Metrics**: Popularity, read counts, and success rates
- **Search Analytics**: Query patterns and results effectiveness
- **Cost Analytics**: Detailed AI/ML usage and costs
- **Performance Metrics**: Response times and error rates
- **Job Statistics**: Success rates and execution times
- **Database Analytics**: Table sizes, index usage, bloat detection, autovacuum statistics
- **Redis Analytics**: Memory usage by pattern, key counts, eviction stats, hit/miss ratios
- **System Metrics**: Database growth tracking, connection pool stats, cache performance
- **Memory Trends**: Historical memory usage and uptime tracking

### 🔧 System Operations & Maintenance
- **Database Maintenance**: Per-table and database-wide VACUUM, ANALYZE, REINDEX operations
- **Redis Operations**: FLUSHDB, FLUSHALL, SAVE, BGSAVE, BGREWRITEAOF with duration tracking
- **Memory Management**: Real-time monitoring, garbage collection triggering, pressure detection
- **Health Checks**: System-wide health monitoring with detailed diagnostics
- **Maintenance Scheduling**: Automated maintenance job scheduling and execution
- **Operation Logging**: Detailed logging for all maintenance operations

### 🌐 Content Proxy Service
- **CORS Bypass**: Safe cross-origin content fetching
- **Smart Caching**: In-memory LRU cache with TTL (static: 15min, HTML: 5min)
- **URL Rewriting**: Automatic URL transformation for proxied resources
- **Size Limits**: 10MB response limit with configurable constraints
- **SSRF Protection**: Secure URL validation and timeout handling (30s)
- **Cache Statistics**: HIT/MISS tracking with automatic cleanup
- **Content Type Handling**: Differentiated caching for HTML vs static resources

## 🎯 Complete Feature Set

NeuReed includes **51 comprehensive backend feature categories**:

1. Authentication & Authorization
2. Feed Management
3. Feed Health & Monitoring
4. Article Management
5. Content Extraction
6. Search & Discovery
7. Saved Searches
8. AI/ML - Embeddings
9. AI/ML - Summarization
10. Personalization & Machine Learning
11. Category Management
12. Bulk Operations
13. OPML Import/Export
14. Cron Job System
15. Feed Refresh Pipeline
16. Notification System
17. User Preferences
18. LLM Configuration Management
19. Cost Tracking
20. Caching System
21. Settings Cascade
22. Tag Management
23. Default Content Provisioning
24. Article Cleanup
25. Admin Features
26. Security Features
27. Logging & Monitoring
28. API Endpoints
29. Database Operations
30. Offline Support
31. Error Handling & Logging
32. Performance Optimization
33. Analytics & Insights
34. Search Query Templates
35. Article Suggestions & Autocomplete
36. Hybrid Search
37. Memory Monitoring & Management
38. Database Maintenance Operations
39. Redis Maintenance Operations
40. System Metrics & Monitoring
41. Content Proxy Service
42. Database Statistics & Analytics
43. Redis Statistics & Analytics
44. Streaming Embeddings
45. Database Reset & Seeding
46. User Role Management
47. System Configuration Constraints
48. Feed Article Deletion
49. User Pattern Reset
50. Category Reordering
51. Feed Article Refresh

Each feature is production-ready with comprehensive error handling, logging, monitoring, and optimization.

## 🛠️ Technology Stack

- **Framework**: FastAPI (Python 3.10+)
- **Database**: PostgreSQL with pgvector extension
- **Caching**: Redis
- **Authentication**: OAuth2, JWT
- **AI/ML**: OpenAI API, Ollama (local LLMs)
- **Feed Parsing**: feedparser
- **Content Extraction**: 
  - Newspaper3k (fast, multi-language)
  - Trafilatura (high-quality)
  - readability-lxml (Mozilla Readability)
  - Goose3 (advanced metadata)
  - Playwright (optional, for JavaScript-rendered content)
- **Vector Search**: pgvector with HNSW indexing
- **Job Scheduling**: Custom cron-based system
- **Monitoring**: psutil for memory tracking
- **Testing**: pytest
- **Validation**: Pydantic schemas

## 📋 Prerequisites

- Python 3.10 or higher
- PostgreSQL 14+ with pgvector extension
- Redis 6+
- (Optional) Playwright browsers for JavaScript-rendered content extraction
- Sufficient system memory for AI operations (recommended: 8GB+)

## 🚀 Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/neureed-be.git
cd neureed-be
```

2. **Create and activate virtual environment**
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **(Optional) Install Playwright browsers**

If you need to extract content from JavaScript-rendered websites:

```bash
playwright install chromium
```

> **Note**: Playwright is optional. The system will use other extraction methods (Newspaper3k, Trafilatura, readability-lxml, Goose3) by default, which don't require browser automation.

5. **Set up PostgreSQL with pgvector**
```sql
CREATE DATABASE neureed;
\c neureed
CREATE EXTENSION vector;
```

6. **Configure environment variables**
```bash
cp .env.example .env
# Edit .env with your configuration
```

7. **Run database migrations**
```bash
alembic upgrade head
```

8. **Seed default data** (optional)
```bash
python scripts/seed.py
```

## ⚙️ Configuration

Create a `.env` file in the project root with the following variables:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/neureed

# Redis
REDIS_URL=redis://localhost:6379/0

# Authentication
SECRET_KEY=your-secret-key-here
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# OAuth Providers
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
GITHUB_CLIENT_ID=your-github-client-id
GITHUB_CLIENT_SECRET=your-github-client-secret

# OpenAI (optional)
OPENAI_API_KEY=your-openai-api-key

# Ollama (optional, for local LLMs)
OLLAMA_BASE_URL=http://localhost:11434

# Application Settings
CORS_ORIGINS=http://localhost:3000
MAX_ARTICLES_PER_FEED=1000
DEFAULT_REFRESH_INTERVAL=3600
FEED_FAILURE_THRESHOLD=5

# Content Extraction
# Available extractors: newspaper3k, trafilatura, readability-lxml, goose3, playwright
# Multiple extractors can be specified with fallback order (comma-separated)
DEFAULT_CONTENT_EXTRACTOR=trafilatura,newspaper3k,readability-lxml
ENABLE_PLAYWRIGHT_EXTRACTION=false  # Set to true if you installed Playwright

# Job Scheduling
ENABLE_CRON_JOBS=true
FEED_REFRESH_CRON=0 */1 * * *  # Every hour
CLEANUP_CRON=0 2 * * *  # Daily at 2 AM

# Cost Limits (optional)
MAX_MONTHLY_COST_PER_USER=10.00

# Content Proxy
PROXY_CACHE_MAX_SIZE_MB=100
PROXY_MAX_RESPONSE_SIZE_MB=10
PROXY_REQUEST_TIMEOUT=30

# Memory Monitoring
ENABLE_MEMORY_MONITORING=true
MEMORY_CHECK_INTERVAL=60

# Logging
LOG_LEVEL=INFO  # Options: DEBUG, INFO, WARNING, ERROR
ENABLE_DEBUG_LOGGING=false  # Can be toggled by admins
LOG_FORMAT=json  # Options: json, text
LOG_RETENTION_DAYS=30
MAX_LOG_FILE_SIZE_MB=100

# Search Features
ENABLE_HYBRID_SEARCH=true
ENABLE_SEARCH_SUGGESTIONS=true
MIN_SUGGESTION_QUERY_LENGTH=2
```

## 🏃 Running the Application

### Development Mode

```bash
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### Production Mode

```bash
gunicorn app.main:app -w 4 -k uvicorn.workers.UvicornWorker --bind 0.0.0.0:8000
```

### With Docker

```bash
docker-compose up -d
```

## 📚 API Documentation

Once the application is running, visit:

- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc
- **OpenAPI JSON**: http://localhost:8000/openapi.json

### API Feature Highlights

The API includes endpoints for:
- **User Operations**: Authentication, preferences, role management
- **Feed Operations**: CRUD, health checks, refresh, OPML import/export
- **Article Operations**: Read/unread tracking, search, suggestions, summarization
- **Search**: Full-text, semantic, hybrid, saved searches, templates
- **Admin Operations**: System metrics, maintenance, database/Redis operations, memory monitoring
- **AI/ML Operations**: Embedding generation, summarization, personalization
- **System Operations**: Job management, notifications, cost tracking

## 🧪 Testing

Run the test suite:

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=app --cov-report=html

# Run specific test file
pytest tests/test_feeds.py

# Run with verbose output
pytest -v
```

## 🗂️ Project Structure

```
neureed-be/
├── app/
│   ├── api/              # API routes and endpoints
│   ├── core/             # Core configuration and utilities
│   ├── db/               # Database models and connections
│   ├── services/         # Business logic and services
│   ├── schemas/          # Pydantic models for validation
│   ├── ml/               # Machine learning and AI features
│   ├── workers/          # Background job workers
│   └── main.py           # FastAPI application entry point
├── tests/                # Test suite
├── migrations/           # Database migrations (Alembic)
├── scripts/              # Utility scripts
├── requirements.txt      # Python dependencies
├── docker-compose.yml    # Docker configuration
├── .env.example          # Environment variables template
└── README.md            # This file
```

## 🔧 Development

### Code Style

This project follows PEP 8 guidelines with Black formatting:

```bash
# Format code
black app/

# Lint code
flake8 app/

# Type checking
mypy app/
```

### Database Migrations

Create a new migration:

```bash
alembic revision --autogenerate -m "Description of changes"
```

Apply migrations:

```bash
alembic upgrade head
```

Rollback migration:

```bash
alembic downgrade -1
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- FastAPI for the excellent web framework
- pgvector for efficient vector similarity search
- OpenAI for embeddings and LLM capabilities
- Ollama for local LLM support
- PostgreSQL for robust database operations
- Redis for high-performance caching
- Content extraction libraries:
  - Newspaper3k for fast multi-language article extraction
  - Trafilatura for high-quality content extraction
  - readability-lxml for Mozilla Readability implementation
  - Goose3 for advanced article extraction
  - Playwright for JavaScript-rendered content (optional)
- feedparser for RSS/Atom feed parsing
- The open-source community for various libraries and tools

## 📞 Support

For questions, issues, or feature requests, please open an issue on GitHub or contact the maintainers.

---

**Built with ❤️ using FastAPI and AI**

