# Setu AI - Bridging Voices Across Languages
*"Where Every Voice Finds Its Bridge to Every Heart"*

## Design Document

**Setu AI** is the revolutionary communication bridge that transforms any content creator's voice into a natural, human-like experience across languages. Just as "Setu" means bridge in Sanskrit, our platform bridges the gap between creators and audiences, making every gaming stream, podcast, educational video, and entertainment content accessible to diverse linguistic communities with unprecedented authenticity and affordability.

### 1. System Architecture

#### High-Level Architecture Diagram (Text)

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Web Frontend  │    │   API Gateway    │    │  Step Functions │
│   (React SPA)   │◄──►│   (REST API)     │◄──►│  (Orchestrator) │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                │                        │
                                ▼                        ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   AWS Cognito   │    │   Lambda Layer   │    │   Amazon S3     │
│ (Authentication)│    │  (Business Logic)│    │ (File Storage)  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                │
                                ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│ Amazon Bedrock  │    │ Amazon Transcribe│    │  Amazon Polly   │
│ (AI Translation)│    │ (Speech-to-Text) │    │ (Text-to-Speech)│
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

#### Components and Responsibilities

**Frontend Layer:**
- **Web Application**: React-based SPA for all content creators (streamers, gamers, podcasters, educators) to upload and manage bidirectional conversions
- **Content Type Selection**: Interface optimized for different content categories with specialized settings
- **Language Selection**: Interface for choosing translation direction (English↔Hinglish) with content-aware optimization
- **Quality Preview**: Real-time preview of human-level dubbing quality with content-specific quality metrics
- **Creator Dashboard**: Analytics showing audience reach expansion and cost savings (90%+ reduction)

**API Layer:**
- **API Gateway**: RESTful endpoints for all client-server communication
- **Authentication**: JWT token validation and user session management
- **Rate Limiting**: Prevents abuse and manages concurrent processing loads

**Processing Layer:**
- **Step Functions**: Orchestrates the multi-step video conversion workflow
- **Lambda Functions**: Serverless compute for each processing stage
- **Error Handling**: Retry logic and failure notifications

**AI/ML Layer:**
- **Universal Bidirectional Transcription**: Handles both English and Hinglish speech-to-text with content-aware processing for gaming, podcasts, education, and entertainment
- **Human-Level Translation Engine**: Generates natural code-switched content that preserves creator personality across all content types
- **Adaptive Voice Synthesis**: Creates dubbed audio that maintains creator's unique energy, style, and personality whether gaming, teaching, or entertaining
- **Content-Aware Quality Assurance**: Real-time quality scoring optimized for different content types to ensure 95%+ human-level naturalness

**Storage Layer:**
- **S3 Buckets**: Secure storage for input videos, processed content, and metadata
- **Content Lifecycle**: Automatic cleanup after 30 days per requirements

### 2. Data Flow

#### Step-by-Step Processing Flow

**Step 1: Video Upload**
1. User authenticates via AWS Cognito
2. Frontend uploads video to S3 with pre-signed URL
3. API Gateway triggers Step Functions workflow
4. User receives upload confirmation and tracking ID

**Step 2: Universal Bidirectional Audio Extraction and Transcription**
1. Lambda function extracts audio from uploaded content (gaming streams, podcasts, educational videos, entertainment)
2. Amazon Transcribe processes audio (English OR Hinglish) with content-type awareness for specialized terminology
3. Language detection automatically identifies source language direction and content category
4. Transcript stored in S3 with confidence scores, timing data, emotional markers, and content-specific metadata

**Step 3: Content-Aware Human-Level Bidirectional Translation**
1. Lambda function sends transcript to Amazon Bedrock (Claude 3.5 Sonnet) with content type and direction context
2. AI model generates human-level translation (English→Hinglish OR Hinglish→English) maintaining:
   - Creator's unique personality and energy (gaming excitement, podcast conversational tone, educational authority)
   - Content-specific terminology (gaming slang, technical terms, cultural references)
   - Natural code-switching patterns appropriate for target audience and content type
   - Original creator's style markers and engagement techniques
3. Translation includes emotional markers and timing preservation for perfect synchronization across all content types

**Step 4: Creator-Focused Human-Level Neural Dubbing**
1. Translated text sent to Amazon Polly with advanced neural voice models and content-specific emotional parameters
2. Audio generated with human-level quality that preserves:
   - Creator's unique vocal characteristics and energy level (gaming enthusiasm, podcast warmth, educational clarity)
   - Natural accent and intonation patterns appropriate for content type
   - Creator's personality markers and signature style elements
   - Content-specific delivery patterns (gaming reactions, conversational flow, teaching rhythm)
3. Advanced audio processing ensures 95%+ naturalness score vs human dubbing baseline across all content types
4. Audio timing perfectly synchronized with original content pacing and creator's natural delivery style

**Step 5: Universal Quality Assurance and Creator Cost Optimization**
1. Lambda function combines original content with human-level dubbed audio track
2. Content-aware quality scoring validates 95%+ naturalness vs human dubbing baseline for specific content type
3. Creator cost calculation shows 90%+ savings compared to traditional dubbing quotes for their content category
4. Authenticity badge generated using content provenance metadata with creator verification

**Step 6: Creator-Focused Delivery and Notification**
1. Processed content stored in S3 with secure access controls and creator metadata
2. Creator notified via preferred channels (email/SMS/platform notifications) of completion
3. Download link provided with time-limited access and creator analytics integration
4. Audience reach expansion metrics and engagement predictions provided

### 3. Tech Stack

#### Frontend
- **Framework**: React 18 with TypeScript
- **UI Library**: Material-UI for consistent government-friendly interface
- **State Management**: React Query for server state, Context API for local state
- **File Upload**: AWS SDK for direct S3 uploads with progress tracking

#### Backend
- **Runtime**: Node.js 18 on AWS Lambda
- **API Framework**: Express.js with serverless-express adapter
- **Validation**: Joi for request validation and sanitization
- **Monitoring**: CloudWatch for logging and metrics

#### AI/ML
- **Translation**: Amazon Bedrock with Claude 3.5 Sonnet for code-switching intelligence
- **Fallback Model**: Cohere Command for translation redundancy
- **Speech Recognition**: Amazon Transcribe with Indian English model
- **Voice Synthesis**: Amazon Polly Neural TTS with Indian voice options

#### Storage & Infrastructure
- **Object Storage**: Amazon S3 with lifecycle policies
- **Compute**: AWS Lambda for serverless processing
- **Orchestration**: AWS Step Functions for workflow management
- **CDN**: CloudFront for fast content delivery

#### Security
- **Authentication**: AWS Cognito User Pools
- **Authorization**: JWT tokens with role-based access
- **Encryption**: S3 server-side encryption, TLS 1.3 in transit

### 4. AWS Services Used and Why

#### Amazon Bedrock (Claude 3.5 Sonnet, Cohere Command)
- **Purpose**: Human-level bidirectional translation that preserves creator personality and content-specific nuances
- **Why**: Superior language understanding for natural code-switching across gaming, podcast, educational, and entertainment content
- **Content Awareness**: Handles gaming terminology, podcast conversational flow, educational clarity, and entertainment timing
- **Quality Focus**: Achieves 95%+ naturalness score, indistinguishable from human dubbing across all content types
- **Fallback**: Cohere Command provides redundancy if Claude is unavailable

#### Amazon Transcribe
- **Purpose**: Convert speech to timestamped text for both English and Hinglish inputs across all content types
- **Why**: Optimized for Indian accents, provides confidence scores and content-aware processing
- **Content Support**: Handles gaming streams, podcast conversations, educational lectures, and entertainment content
- **Bidirectional Support**: Processes both English→Hinglish and Hinglish→English workflows with content-specific optimization
- **Configuration**: Custom vocabulary for gaming terminology, podcast language, educational terms, and entertainment expressions

#### Amazon Polly
- **Purpose**: Generate human-level dubbed speech that rivals professional dubbing quality across all content types
- **Why**: Neural voices with creator personality preservation, 90% cost reduction vs human dubbing for all creators
- **Content Optimization**: Specialized processing for gaming energy, podcast warmth, educational authority, and entertainment timing
- **Quality**: Advanced SSML processing for human-like pronunciation and content-appropriate emotional delivery
- **Voice Selection**: Multiple Indian accent options for authentic regional representation across different content styles

#### AWS Lambda
- **Purpose**: Serverless compute for all processing stages
- **Why**: Cost-effective, auto-scaling, perfect for hackathon constraints
- **Functions**: Video processing, transcription handling, translation coordination

#### Amazon API Gateway
- **Purpose**: RESTful API endpoints with built-in security
- **Why**: Handles authentication, rate limiting, and request validation
- **Features**: CORS support, request/response transformation

#### AWS Step Functions
- **Purpose**: Orchestrate complex video processing workflow
- **Why**: Visual workflow management, error handling, retry logic
- **Benefits**: Reliable processing pipeline with state management

#### Amazon S3
- **Purpose**: Secure storage for videos, audio, and processed content
- **Why**: Scalable, durable, integrates with all other AWS services
- **Configuration**: Lifecycle policies for automatic cleanup

#### AWS Cognito
- **Purpose**: User authentication and session management
- **Why**: Government-grade security, integrates with existing systems
- **Features**: Multi-factor authentication, password policies

### 5. Security & Privacy Design

#### Authentication & Authorization
- **User Authentication**: AWS Cognito with MFA for government officers
- **Session Management**: JWT tokens with 8-hour expiration
- **Role-Based Access**: Different permissions for officers, reviewers, and admins
- **API Security**: All endpoints require valid authentication tokens

#### Data Protection
- **Encryption at Rest**: S3 server-side encryption with AWS KMS
- **Encryption in Transit**: TLS 1.3 for all API communications
- **Data Isolation**: User content isolated using S3 bucket policies
- **Automatic Cleanup**: Content deleted after 30 days per privacy requirements

#### Content Provenance
- **Authenticity Badge**: Cryptographic signature for processed videos
- **Metadata Tracking**: Complete audit trail of processing steps
- **Tamper Detection**: Hash verification for content integrity
- **Source Verification**: Original uploader identity preserved

#### Compliance
- **Government Standards**: Follows Indian government data handling policies
- **Audit Logging**: All user actions logged in CloudWatch
- **Data Residency**: All processing within Indian AWS regions
- **Privacy Controls**: Users can delete content before 30-day limit

### 6. Scalability Strategy

#### National Scale Preparation
- **Auto-Scaling**: Lambda functions scale automatically with demand
- **Regional Distribution**: Multi-AZ deployment for high availability
- **CDN Integration**: CloudFront for fast content delivery nationwide
- **Database Scaling**: DynamoDB for user metadata with on-demand scaling

#### Performance Optimization
- **Concurrent Processing**: Step Functions handle multiple videos simultaneously
- **Caching Strategy**: Frequently accessed content cached at edge locations
- **Resource Optimization**: Right-sized Lambda functions for cost efficiency
- **Queue Management**: SQS for handling peak upload periods

#### Future Expansion
- **Universal Content Support**: Architecture ready for all content types including live streaming, long-form series, and interactive content
- **Bidirectional Language Pairs**: Scalable to English↔Tanglish, English↔Benglish, and other regional code-switching pairs
- **Creator-Focused Features**: Advanced personality preservation and style customization for individual creators
- **Quality Scaling**: Human-level dubbing quality maintained across all content types and language pairs
- **Cost Optimization**: 90%+ cost reduction model scalable to all supported content categories and creator types
- **Platform Integration**: API compatibility with streaming platforms, content management systems, and creator tools

### 7. Failure Handling

#### Transcription Failures
- **Retry Logic**: Automatic retry with exponential backoff (3 attempts)
- **Fallback Processing**: Alternative transcription service if primary fails
- **User Notification**: Clear error messages with suggested actions
- **Manual Override**: Option to upload custom transcript for processing

#### Translation Failures
- **Model Redundancy**: Fallback from Claude to Cohere Command automatically for both translation directions
- **Quality Validation**: Real-time scoring to ensure 95%+ human-level naturalness
- **Human Review**: Flag translations below quality threshold for manual review
- **Graceful Degradation**: Provide original language version if translation fails to meet quality standards

#### Dubbing Failures
- **Voice Alternatives**: Multiple Polly neural voice options for redundancy in both languages
- **Quality Assurance**: Automated validation ensures human-level dubbing quality (95%+ naturalness)
- **Retry Mechanisms**: Different synthesis parameters and emotional markers on failure
- **Cost Protection**: No charges if output fails to meet human-level quality standards

#### System-Level Failures
- **Circuit Breakers**: Prevent cascade failures across services
- **Dead Letter Queues**: Capture failed processing attempts for analysis
- **Health Monitoring**: Real-time system health checks and alerts
- **Rollback Capability**: Quick rollback to previous working version

#### Data Recovery
- **S3 Versioning**: Multiple versions of content for recovery
- **Cross-Region Backup**: Critical data replicated across regions
- **Point-in-Time Recovery**: Restore system state from any point
- **Disaster Recovery**: Complete system restoration within 4 hours

---

*This design document provides the technical foundation for implementing the Setu AI MVP - the bridge that connects creators with their audiences across languages. Delivering human-level bidirectional dubbing quality at 90% cost reduction compared to traditional dubbing services across all content types - gaming, podcasts, education, entertainment, and beyond - while balancing hackathon constraints with production-ready architecture principles that truly bridge communication gaps.*