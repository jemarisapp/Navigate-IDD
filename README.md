# GENAI-Based Automated Video Solution for Medicaid Services

## Project Overview

This project represents a groundbreaking AI-powered automation system designed to address critical accessibility challenges in Medicaid waiver programs. By leveraging cutting-edge artificial intelligence, natural language processing, and video generation technologies, the system transforms complex, dense policy documents into accessible, multilingual educational videos that reach families who need them most.

### The Challenge We're Solving

Medicaid waiver programs like NOW/COMP in Georgia serve over **7,000 people on waiting lists**, yet many families struggle with:

- **Language Barriers**: Complex eligibility rules written in dense policy language
- **Accessibility Issues**: High rejection rates due to confusing application processes  
- **Information Gaps**: Long waitlists with unclear priority systems
- **Cultural Disconnect**: Limited accessible information for non-English speakers
- **Systemic Inefficiency**: Bureaucratic overload reducing service delivery effectiveness

### Our Solution

An end-to-end AI automation pipeline that:
- **Converts** verified waiver documents into plain-language scripts (6th grade reading level)
- **Generates** professional videos in 5 languages with culturally appropriate avatars
- **Distributes** content across social media platforms for maximum reach
- **Maintains** quality through human approval gates and RAG-based accuracy verification

---

## Technical Architecture

### Core Technology Stack

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Workflow Engine** | n8n | Orchestration and automation platform |
| **AI Language Model** | OpenAI GPT-5 | Short script generation and translation |
| **AI Language Model** | Claude Sonnet 4.5 | Long script generation and translation |
| **Vector Database** | Pinecone | RAG implementation for accuracy |
| **Video Generation** | Synthesia | Multi-language AI video creation |
| **Social Distribution** | Blotato | Multi-platform content distribution |
| **Document Management** | Google Workspace | Drive, Docs, Sheets integration |
| **Approval System** | Google Sheets | Human oversight and quality control |

### System Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    GENAI MEDICAID VIDEO AUTOMATION SYSTEM                       │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Document      │───▶│  AI Processing  │───▶│  Video Creation │
│   Ingestion     │    │  (RAG + GPT-5)  │    │  (Synthesia)    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Google Drive   │    │  Pinecone Vector│    │  Multi-Language │
│  File Monitoring│    │  Database       │    │  Video Pipeline │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Text Extraction│    │  Similarity     │    │  Language-Specific│
│  & Embeddings   │    │  Search & RAG   │    │  Formatting     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Script         │    │  Human Approval │    │  Social Media   │
│  Generation     │    │  Workflow       │    │  Distribution   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

---

## Workflow Implementation

### Phase 1: Document Processing & Knowledge Base

**Vector Database Management**
- **Pinecone Integration**: Stores document embeddings for similarity search
- **Source Document Processing**: Monitors Google Drive for new policy documents
- **Topic File Processing**: Handles both short (1-1.5 min) and long (3-5 min) content requests
- **Embedding Generation**: Uses OpenAI's embedding model (1024 dimensions) for vector creation

**Key Features:**
- Real-time document monitoring via Google Drive API
- Automatic text extraction from multiple file formats
- Intelligent document categorization and tagging
- Vector similarity search for context-aware script generation

### Phase 2: AI-Powered Script Generation

**RAG (Retrieval-Augmented Generation) Implementation**
- **Source Verification**: Only uses information from verified policy documents
- **Comprehensive Search Strategy**: 8-12 separate searches per script for maximum detail
- **Quality Assurance**: Every fact must be supported by retrieved sources
- **Plain Language Conversion**: 6th grade reading level for maximum accessibility

**Script Types:**
1. **Short Scripts (1-1.5 minutes)**: Quick, focused educational content
2. **Long Scripts (3-5 minutes)**: Comprehensive, detailed explanations

**AI Prompt Engineering:**
- Structured prompts for consistent output quality
- Mandatory comprehensive search strategies
- Quality check requirements before script generation
- Cultural sensitivity and accessibility considerations

### Phase 3: Multi-Language Translation

**Supported Languages:**
- English (Primary)
- Spanish
- Chinese (Simplified)
- Korean
- Vietnamese

**Translation Process:**
- Approved English scripts trigger translation workflow
- Each language gets separate Google Docs for review
- Cultural adaptation and terminology localization
- Individual approval process for each translated version

### Phase 4: Video Production Pipeline

**Synthesia Integration:**
- **Multi-language Video Creation**: Language-specific avatars and voices
- **Background Customization**: Appropriate visuals for each content type
- **Status Monitoring**: Real-time tracking of video generation progress
- **Quality Control**: Automated quality checks and error handling

**Video Processing:**
- Automatic download of completed videos
- Google Drive storage with organized naming conventions
- Status tracking in Google Sheets dashboard
- Error handling and retry mechanisms

### Phase 5: Social Media Distribution

**Blotato Integration:**
- **Multi-platform Posting**: YouTube and Facebook distribution
- **SEO Optimization**: AI-generated titles, descriptions, and tags
- **Platform-specific Formatting**: Optimized content for each platform
- **Analytics Tracking**: Performance monitoring and engagement metrics

---

## Key Features & Innovations

### Accessibility-First Design

**Plain Language Processing**
- 6th grade reading level for maximum comprehension
- Acronym definitions and technical term explanations
- Conversational tone with supportive validation
- Actionable guidance based on source material

**Multilingual Support**
- 5 language versions with cultural adaptation
- Language-specific avatars and voice selection
- Cultural sensitivity in terminology and examples
- Separate approval processes for quality assurance

**Visual Accessibility**
- Automatic caption generation
- High contrast backgrounds for readability
- Consistent visual branding across languages
- Mobile-optimized video formats

### Quality Assurance Framework

**Human Oversight**
- Multiple approval gates throughout the process
- Subject matter expert review before publication
- Translation quality validation
- Content accuracy verification

**AI-Powered Accuracy**
- RAG system ensures information accuracy
- Source verification for every claim
- Comprehensive search strategies for completeness
- Error detection and correction mechanisms

**Continuous Improvement**
- User feedback integration
- Performance analytics and optimization
- A/B testing capabilities
- Content iteration based on engagement data

### Scalability & Performance

**Automated Workflow**
- Minimal manual intervention required
- Parallel processing for multiple languages
- Error handling and retry mechanisms
- Real-time status monitoring

**Cloud-Native Architecture**
- Serverless processing capabilities
- Auto-scaling based on demand
- Cost optimization through efficient resource usage
- High availability and reliability

---

## Technical Implementation Details

### n8n Workflow Configuration

**Node Count**: 100+ interconnected nodes
**Trigger Types**: File monitors, timers, webhooks, manual triggers
**Data Flow**: Bidirectional with multiple integration points
**Error Handling**: Comprehensive retry logic and fallback procedures


### Data Processing Pipeline

**Input Processing:**
- Document format detection and conversion
- Text extraction and cleaning
- Language detection and classification

**AI Processing:**
- Embedding generation (1024 dimensions)
- Vector similarity search
- Context-aware script generation
- Multi-language translation
- Quality validation and scoring

**Output Processing:**
- Video format optimization
- Metadata generation and SEO optimization
- Platform-specific formatting

---

## Deployment & Configuration

### Prerequisites

**Technical Requirements:**
- n8n instance (self-hosted or cloud)
- Google Workspace account with API access
- OpenAI API key with GPT-5 access
- Pinecone account for vector storage
- Synthesia account for video generation
- Blotato account for social distribution

**Infrastructure:**
- Minimum 4GB RAM for n8n instance
- 50GB storage for video assets
- Stable internet connection (100+ Mbps)
- SSL certificate for webhook endpoints

### Setup Instructions


1. **API Credentials Setup**
   - Configure Google OAuth2 credentials
   - Set up OpenAI API key
   - Configure Pinecone API access
   - Set up Synthesia API credentials
   - Configure Blotato API access
   - Claude/Anthropic API credentials

2. **Workflow Import**
   - Import the `FINAL WORKFLOW.json` file
   - Configure all node credentials
   - Test individual node connections
   - Set up Google Drive folder structure

3. **Dashboard Configuration**
   - Create Google Sheets dashboard
   - Set up approval workflow
   - Configure webhook endpoints
   - Test end-to-end workflow

### Monitoring & Maintenance

**Real-time Monitoring:**
- Google Sheets dashboard for workflow status
- Video generation progress tracking

**Maintenance Tasks:**
- Regular API key rotation
- Vector database optimization
- Video storage cleanup
- Performance tuning and optimization

---

## 📈 Impact & Benefits

### For Families & Individuals

**Accessibility Improvements:**
- Clear, understandable information in native languages
- Reduced application errors and rejections
- Time savings through simplified explanations
- Increased confidence in navigating complex systems


---

## Future Enhancements

### Planned Features

**Accessibility Improvements:**
- American Sign Language (ASL) video generation
- Audio captions for visually impaired users
- Interactive elements and clickable content
- Voice customization options

**Technical Enhancements:**
- Advanced analytics dashboard
- A/B testing framework
- Machine learning optimization
- Real-time collaboration features
- Error logging and alerting
- Performance metrics collection
- Analytics and tracking setup
- Social engagement tracking

**Content Expansion:**
- Additional language support
- Interactive Q&A functionality
- Personalized content recommendations


---

## Conclusion

This GENAI-Based Automated Video Solution represents a significant technological advancement in making Medicaid waiver information accessible to all families, regardless of language, literacy level, or technical expertise. By leveraging cutting-edge AI technologies and maintaining rigorous quality standards through human oversight, the system bridges critical accessibility gaps while improving service delivery efficiency.

The project demonstrates how technology can be used to create meaningful social impact, transforming complex government services into accessible, user-friendly resources that truly serve the communities they're designed to help.

---

*Last Updated: October 2025*  
*Version: 1.0*  
*Status: Production Ready*
