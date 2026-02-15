# Software Requirements Specification (SRS)
# Pragya Shiksha - Voice-First Vernacular AI Teacher

**Document Version**: 1.0  
**Date**: February 15, 2026  
**Project**: Pragya Shiksha  
**Prepared By**: Pragya Shiksha Engineering Team  
**Status**: Draft for Review

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Overall Description](#2-overall-description)
3. [Stakeholders](#3-stakeholders)
4. [Functional Requirements](#4-functional-requirements)
5. [Non-Functional Requirements](#5-non-functional-requirements)
6. [Constraints](#6-constraints)
7. [Assumptions and Dependencies](#7-assumptions-and-dependencies)
8. [Acceptance Criteria](#8-acceptance-criteria)
9. [Risks and Mitigations](#9-risks-and-mitigations)
10. [Future Requirements](#10-future-requirements)
11. [Success Metrics](#11-success-metrics)
12. [Glossary](#12-glossary)

---

## 1. Introduction

### 1.1 Purpose

This Software Requirements Specification (SRS) document provides a complete description of the requirements for Pragya Shiksha, a voice-first, offline-capable, vernacular AI teacher platform designed for rural Indian students. This document is intended for:

- Development team members
- Project stakeholders
- Quality assurance team
- AWS AI for Bharat Hackathon judges
- Government and NGO partners

### 1.2 Scope

**Product Name**: Pragya Shiksha (Sanskrit: "Wisdom Education")

**Product Description**: Pragya Shiksha is a Progressive Web Application (PWA) that provides personalized AI-powered education to rural students in Classes 6-12. The system leverages AWS AI services (Bedrock, Polly, Transcribe) to deliver conversational learning experiences in regional languages, with full offline capability after initial content download.


**Key Features**:
- Voice-first interaction (no typing required)
- Offline-capable (works without internet)
- Vernacular language support (Hindi, Tamil, Telugu in MVP)
- Adaptive AI tutoring powered by Amazon Bedrock
- Works on basic smartphones (₹3000 price point)
- NCERT-aligned curriculum for Classes 6-12

**Benefits**:
- Removes language barriers (education in mother tongue)
- Removes connectivity barriers (offline-first design)
- Removes literacy barriers (voice-based, no reading required)
- Personalized learning at scale (AI adapts to each student)
- Accessible on affordable devices (no expensive smartphones needed)

### 1.3 Problem Statement

**Context**: AWS AI for Bharat Hackathon - AI for Communities, Access & Public Impact

**Problem**: Over 5 crore rural students in India lack access to quality education due to:
1. Teacher shortage in rural areas (1 teacher per 100+ students)
2. Language barriers (education primarily in English/Hindi, not mother tongue)
3. Limited internet connectivity (60% of rural India has no reliable internet)
4. Expensive devices (smartphones > ₹10,000 unaffordable for most families)
5. Low literacy levels (parents cannot help with homework)

**Impact**: 
- 40% rural students drop out before Class 10
- Learning outcomes 3-4 years behind urban peers
- Limited career opportunities due to poor foundational education

### 1.4 Vision and Mission

**Vision**: Bring personalized AI education to 5 crore+ rural students in their mother tongue, on basic smartphones, with zero internet dependency.

**Mission**: Democratize education access by removing language, literacy, and connectivity barriers through voice-first AI tutoring.

### 1.5 Document Conventions

**Requirement Priorities**:
- **MUST**: Critical requirement, system cannot function without it
- **SHOULD**: Important requirement, highly desirable but not critical
- **NICE-TO-HAVE**: Optional enhancement, can be deferred to future releases

**Requirement Identifiers**:
- FR: Functional Requirement
- NFR: Non-Functional Requirement
- C: Constraint
- A: Assumption
- D: Dependency


---

## 2. Overall Description

### 2.1 Product Perspective

Pragya Shiksha is a new, self-contained product built specifically for the AWS AI for Bharat Hackathon. It integrates with:

- **AWS Cloud Services**: Bedrock, Polly, Transcribe, Lambda, DynamoDB, S3, CloudFront
- **Browser APIs**: Web Speech API, Service Workers, IndexedDB
- **Educational Standards**: NCERT curriculum, State Board syllabi

The system operates in two modes:
1. **Online Mode**: Full functionality with cloud AI services
2. **Offline Mode**: Cached lessons and responses, local progress tracking

### 2.2 Product Functions

The system provides the following major functions:

1. **Voice-Based Learning**: Students ask questions via voice, AI responds with audio explanations
2. **Offline Content Access**: Download lesson packs for offline study
3. **Adaptive Tutoring**: AI adjusts difficulty based on student performance
4. **Progress Tracking**: Monitor learning progress, identify knowledge gaps
5. **Multi-Language Support**: Learn in Hindi, Tamil, or Telugu
6. **Teacher Dashboard**: Teachers monitor student progress and assign lessons
7. **Gamification**: Earn points and badges for motivation

### 2.3 User Classes and Characteristics

| User Class | Characteristics | Technical Expertise | Frequency of Use |
|------------|----------------|---------------------|------------------|
| **Rural Students** | Ages 11-18, Classes 6-12, limited English, basic smartphone literacy | Low | Daily (30-60 min) |
| **Teachers** | Government school teachers, moderate smartphone skills | Medium | Weekly (monitoring) |
| **School Admins** | Principals, headmasters, need aggregate reports | Medium | Monthly (reports) |
| **Parents** | Limited literacy, want to track child's progress | Low | Weekly (SMS updates) |
| **Content Creators** | Subject matter experts, create lesson content | High | Daily (content upload) |

### 2.4 Operating Environment

**Client-Side**:
- Device: Android smartphones (₹3000-₹10,000 range)
- OS: Android 8.0+ (Oreo and above)
- RAM: 2GB minimum
- Storage: 16GB minimum (with 2GB free for app data)
- Browser: Chrome 90+, Firefox 88+
- Network: 2G/3G/4G (intermittent), WiFi (occasional)

**Server-Side**:
- Cloud Provider: AWS (Mumbai region - ap-south-1)
- Services: Lambda, API Gateway, DynamoDB, S3, CloudFront, Bedrock, Polly, Transcribe
- Architecture: Serverless, auto-scaling


### 2.5 Design and Implementation Constraints

See Section 6 for detailed constraints.

### 2.6 User Documentation

The following user documentation will be provided:

1. **Student Onboarding Video** (2 minutes, vernacular languages)
2. **Teacher Training Manual** (PDF, 10 pages, bilingual)
3. **FAQ Document** (Common issues and solutions)
4. **In-App Help** (Context-sensitive tooltips)
5. **Voice Tutorials** (Audio guides for first-time users)

---

## 3. Stakeholders

### 3.1 Primary Stakeholders

**Rural Students (Classes 6-12)**
- **Role**: End users of the learning platform
- **Needs**: Easy-to-use voice interface, offline access, vernacular content
- **Success Criteria**: Can complete lessons independently, improve test scores

**Teachers**
- **Role**: Monitor student progress, assign lessons, provide support
- **Needs**: Simple dashboard, actionable insights, minimal training required
- **Success Criteria**: Can identify struggling students, track class performance

### 3.2 Secondary Stakeholders

**School Administrators**
- **Role**: Oversee implementation, generate reports for government
- **Needs**: Aggregate analytics, cost-benefit analysis
- **Success Criteria**: Improved school performance metrics

**Parents**
- **Role**: Encourage children to use the app, track progress
- **Needs**: SMS notifications, simple progress reports
- **Success Criteria**: Understand child's learning progress

### 3.3 Tertiary Stakeholders

**State Governments**
- **Role**: Funding, policy support, scale-up decisions
- **Needs**: Impact assessment, cost per student, scalability proof
- **Success Criteria**: Measurable improvement in learning outcomes

**NGO Partners** (Pratham, Teach For India, Akshaya Patra)
- **Role**: Pilot implementation, ground support, feedback
- **Needs**: Easy deployment, training materials, success stories
- **Success Criteria**: Successful pilot in 50+ schools

**AWS (Hackathon Sponsor)**
- **Role**: Provide cloud credits, technical support
- **Needs**: Showcase AWS AI services, innovative use case
- **Success Criteria**: Award-winning solution, case study


### 3.4 Technical Team

**Development Team** (5 members)
- 1 Full-Stack Developer (React + Python)
- 1 AI/ML Engineer (Bedrock, Polly, Transcribe)
- 1 DevOps Engineer (AWS CDK, CI/CD)
- 1 UI/UX Designer (Mobile-first, vernacular)
- 1 Content Creator (NCERT curriculum expert)

---

## 4. Functional Requirements

### 4.1 Voice-Based Learning (FR1)

#### FR1.1: Voice Question Recording
**Priority**: MUST  
**Description**: Students shall be able to record voice questions in Hindi, Tamil, or Telugu.

**Acceptance Criteria**:
- AC1.1.1: Student can tap microphone button to start recording
- AC1.1.2: Visual indicator shows recording is active (pulsing red circle)
- AC1.1.3: Audio level visualization displays during recording
- AC1.1.4: Student can tap again to stop recording manually
- AC1.1.5: Recording auto-stops after 30 seconds
- AC1.1.6: System handles background noise (echo cancellation, noise suppression)

**Test Cases**:
- TC1.1.1: Record 5-second question, verify audio captured
- TC1.1.2: Record in noisy environment (fan, traffic), verify quality
- TC1.1.3: Test auto-stop at 30 seconds
- TC1.1.4: Test manual stop before 30 seconds

---

#### FR1.2: Speech-to-Text Transcription
**Priority**: MUST  
**Description**: System shall transcribe speech to text with > 90% accuracy for supported languages.

**Acceptance Criteria**:
- AC1.2.1: Transcription completes within 2 seconds for 10-second audio
- AC1.2.2: Accuracy > 90% for clear speech in Hindi, Tamil, Telugu
- AC1.2.3: System handles regional dialects (e.g., Bhojpuri-influenced Hindi)
- AC1.2.4: System displays transcribed text for student verification
- AC1.2.5: Student can edit transcription if incorrect

**Test Cases**:
- TC1.2.1: Transcribe 100 sample questions, measure accuracy
- TC1.2.2: Test with different speakers (male, female, children)
- TC1.2.3: Test with regional accents
- TC1.2.4: Measure transcription latency

**Dependencies**: D1 (Amazon Transcribe accuracy)

---

#### FR1.3: AI Response Generation
**Priority**: MUST  
**Description**: AI shall generate contextual, age-appropriate responses in simple vernacular language.

**Acceptance Criteria**:
- AC1.3.1: Response generated within 5 seconds
- AC1.3.2: Response uses simple vocabulary (5th-grade reading level)
- AC1.3.3: Response relates concepts to rural context (farming, festivals)
- AC1.3.4: Response length < 100 words for audio playback
- AC1.3.5: Response includes follow-up question to continue conversation
- AC1.3.6: Response adapts to student's grade level

**Test Cases**:
- TC1.3.1: Ask "What is photosynthesis?" in Hindi, verify simple explanation
- TC1.3.2: Ask math question, verify step-by-step solution
- TC1.3.3: Measure response generation time (p95 < 5 seconds)
- TC1.3.4: Test with 50 sample questions across subjects

**Dependencies**: D1 (Amazon Bedrock Claude 3.5 Sonnet)

---

#### FR1.4: Text-to-Speech Audio Generation
**Priority**: MUST  
**Description**: System shall convert AI text responses to natural-sounding speech.

**Acceptance Criteria**:
- AC1.4.1: Audio generated within 1 second for cached responses
- AC1.4.2: Audio generated within 3 seconds for new responses
- AC1.4.3: Voice quality is natural (Neural TTS for Hindi)
- AC1.4.4: Audio playback starts immediately (streaming)
- AC1.4.5: Student can pause, replay, or skip audio
- AC1.4.6: Audio cached locally for offline playback

**Test Cases**:
- TC1.4.1: Generate audio for 50-word response, measure time
- TC1.4.2: Test audio quality with 10 students (subjective rating)
- TC1.4.3: Verify caching works (second playback instant)
- TC1.4.4: Test pause/resume functionality

**Dependencies**: D2 (Amazon Polly voice quality)

---

#### FR1.5: Code-Switching Support
**Priority**: SHOULD  
**Description**: System shall handle code-switching (Hinglish, Tanglish) in student questions.

**Acceptance Criteria**:
- AC1.5.1: System recognizes mixed-language questions (e.g., "Photosynthesis kya hai?")
- AC1.5.2: Response uses same language mix as question
- AC1.5.3: System handles English technical terms in vernacular sentences

**Test Cases**:
- TC1.5.1: Ask "Algebra kya hai?" (Hinglish), verify response
- TC1.5.2: Ask "Photosynthesis என்றால் என்ன?" (Tanglish), verify response

---

#### FR1.6: Recording Duration Management
**Priority**: MUST  
**Description**: System shall support 30-second voice recordings with auto-stop.

**Acceptance Criteria**:
- AC1.6.1: Recording auto-stops at exactly 30 seconds
- AC1.6.2: Warning shown at 25 seconds ("5 seconds remaining")
- AC1.6.3: Student can stop recording anytime before 30 seconds
- AC1.6.4: Minimum recording duration is 1 second

**Test Cases**:
- TC1.6.1: Record for 35 seconds, verify stops at 30
- TC1.6.2: Verify warning appears at 25 seconds
- TC1.6.3: Stop recording at 10 seconds, verify accepted


---

### 4.2 Offline Capability (FR2)

#### FR2.1: Lesson Pack Download
**Priority**: MUST  
**Description**: Students shall be able to download lesson packs (< 50MB each) on 2G/3G networks.

**Acceptance Criteria**:
- AC2.1.1: Each lesson pack is < 50MB (compressed)
- AC2.1.2: Download completes in < 5 minutes on 3G (1 Mbps)
- AC2.1.3: Download can be paused and resumed
- AC2.1.4: Progress indicator shows download percentage
- AC2.1.5: Student can download multiple lessons (queue)
- AC2.1.6: Downloaded lessons stored in IndexedDB
- AC2.1.7: Student can delete downloaded lessons to free space

**Test Cases**:
- TC2.1.1: Download lesson pack, verify size < 50MB
- TC2.1.2: Simulate 3G network, measure download time
- TC2.1.3: Pause download, close app, resume - verify works
- TC2.1.4: Download 5 lessons, verify queue management
- TC2.1.5: Delete lesson, verify storage freed

---

#### FR2.2: Complete Offline Functionality
**Priority**: MUST  
**Description**: System shall function completely offline after initial download.

**Acceptance Criteria**:
- AC2.2.1: All downloaded lessons accessible offline
- AC2.2.2: Voice input works offline (Web Speech API)
- AC2.2.3: Audio playback works offline (cached responses)
- AC2.2.4: Progress tracking works offline (local storage)
- AC2.2.5: UI shows "Offline Mode" indicator
- AC2.2.6: No network errors displayed to user

**Test Cases**:
- TC2.2.1: Enable airplane mode, complete full lesson
- TC2.2.2: Verify voice input works offline
- TC2.2.3: Verify audio playback from cache
- TC2.2.4: Complete 5 lessons offline, verify progress saved

---

#### FR2.3: Audio Response Caching
**Priority**: MUST  
**Description**: System shall cache audio responses for common queries.

**Acceptance Criteria**:
- AC2.3.1: Top 100 common questions pre-cached per subject
- AC2.3.2: Generated audio cached for 7 days
- AC2.3.3: Cache size limited to 500MB
- AC2.3.4: LRU (Least Recently Used) eviction policy
- AC2.3.5: Cache hit rate > 60% for typical usage

**Test Cases**:
- TC2.3.1: Ask same question twice, verify second is instant
- TC2.3.2: Fill cache to 500MB, verify old items evicted
- TC2.3.3: Measure cache hit rate over 100 questions

---

#### FR2.4: Offline Progress Tracking
**Priority**: MUST  
**Description**: System shall save progress locally when offline.

**Acceptance Criteria**:
- AC2.4.1: Lesson completion saved to IndexedDB
- AC2.4.2: Quiz scores saved locally
- AC2.4.3: Time spent tracked offline
- AC2.4.4: Progress visible in UI immediately
- AC2.4.5: No data loss if app closed unexpectedly

**Test Cases**:
- TC2.4.1: Complete lesson offline, verify progress saved
- TC2.4.2: Close app mid-lesson, reopen, verify progress restored
- TC2.4.3: Complete 10 lessons offline, verify all tracked

---

#### FR2.5: Auto-Sync on Connectivity
**Priority**: MUST  
**Description**: System shall auto-sync progress to cloud when connectivity restored.

**Acceptance Criteria**:
- AC2.5.1: Sync triggered automatically when online
- AC2.5.2: Sync happens in background (non-blocking)
- AC2.5.3: Sync status shown in UI ("Syncing...", "Synced")
- AC2.5.4: Failed sync retries with exponential backoff
- AC2.5.5: Conflict resolution (server wins for same lesson)

**Test Cases**:
- TC2.5.1: Complete lessons offline, go online, verify sync
- TC2.5.2: Simulate sync failure, verify retry
- TC2.5.3: Complete same lesson on 2 devices, verify conflict resolution

---

#### FR2.6: Differential Sync
**Priority**: SHOULD  
**Description**: System shall support differential sync to minimize bandwidth.

**Acceptance Criteria**:
- AC2.6.1: Only changed data synced (not full dataset)
- AC2.6.2: Sync payload < 10KB for typical session
- AC2.6.3: Timestamp-based change detection
- AC2.6.4: Batch multiple changes in single request

**Test Cases**:
- TC2.6.1: Complete 5 lessons, measure sync payload size
- TC2.6.2: Verify only new progress items sent


---

### 4.3 Adaptive Learning (FR3)

#### FR3.1: Dynamic Difficulty Adjustment
**Priority**: MUST  
**Description**: AI shall adjust lesson difficulty based on student responses.

**Acceptance Criteria**:
- AC3.1.1: If student scores < 50% on quiz, easier questions shown next
- AC3.1.2: If student scores > 80% on quiz, harder questions shown next
- AC3.1.3: Difficulty levels: Beginner, Intermediate, Advanced
- AC3.1.4: AI explains concepts in simpler terms if student struggles
- AC3.1.5: Difficulty adjustment happens in real-time during lesson

**Test Cases**:
- TC3.1.1: Answer 3 questions wrong, verify easier questions appear
- TC3.1.2: Answer 5 questions correct, verify harder questions appear
- TC3.1.3: Test with 20 students, verify personalization works

---

#### FR3.2: Progress Tracking
**Priority**: MUST  
**Description**: System shall track student progress comprehensively.

**Acceptance Criteria**:
- AC3.2.1: Lessons completed count tracked
- AC3.2.2: Time spent per lesson tracked (in seconds)
- AC3.2.3: Quiz scores tracked (percentage)
- AC3.2.4: Streak days tracked (consecutive days of usage)
- AC3.2.5: Total points earned tracked
- AC3.2.6: Progress visible in student dashboard

**Test Cases**:
- TC3.2.1: Complete 5 lessons, verify count accurate
- TC3.2.2: Spend 20 minutes on lesson, verify time tracked
- TC3.2.3: Score 80% on quiz, verify recorded

---

#### FR3.3: Hint System
**Priority**: MUST  
**Description**: AI shall provide hints before revealing answers for wrong responses.

**Acceptance Criteria**:
- AC3.3.1: First wrong answer triggers hint (not full answer)
- AC3.3.2: Second wrong answer triggers detailed hint
- AC3.3.3: Third wrong answer reveals full solution with explanation
- AC3.3.4: Hints are contextual and guide thinking process
- AC3.3.5: Student can request hint without answering first

**Test Cases**:
- TC3.3.1: Answer question wrong, verify hint appears
- TC3.3.2: Answer wrong twice, verify detailed hint
- TC3.3.3: Answer wrong thrice, verify full solution shown

---

#### FR3.4: Lesson Recommendations
**Priority**: SHOULD  
**Description**: System shall recommend next lessons based on performance.

**Acceptance Criteria**:
- AC3.4.1: If student scores < 60%, recommend remedial lesson
- AC3.4.2: If student scores > 80%, recommend advanced lesson
- AC3.4.3: Recommendations consider prerequisite lessons
- AC3.4.4: Student can override recommendations
- AC3.4.5: Recommendations shown on home screen

**Test Cases**:
- TC3.4.1: Score 50% on algebra, verify remedial lesson recommended
- TC3.4.2: Score 90% on geometry, verify advanced lesson recommended

---

#### FR3.5: Knowledge Gap Identification
**Priority**: SHOULD  
**Description**: System shall identify knowledge gaps and suggest remedial content.

**Acceptance Criteria**:
- AC3.5.1: System analyzes wrong answers to identify weak topics
- AC3.5.2: Weak topics highlighted in student dashboard
- AC3.5.3: Remedial lessons suggested for weak topics
- AC3.5.4: Progress on weak topics tracked separately
- AC3.5.5: Teacher notified of student's weak areas

**Test Cases**:
- TC3.5.1: Answer 5 algebra questions wrong, verify algebra flagged as weak
- TC3.5.2: Complete remedial lesson, verify gap addressed


---

### 4.4 Multi-Language Support (FR4)

#### FR4.1: MVP Language Support
**Priority**: MUST  
**Description**: System shall support 3 languages in MVP: Hindi, Tamil, Telugu.

**Acceptance Criteria**:
- AC4.1.1: All UI text available in Hindi, Tamil, Telugu
- AC4.1.2: All lesson content available in all 3 languages
- AC4.1.3: Voice input works in all 3 languages
- AC4.1.4: Voice output (TTS) works in all 3 languages
- AC4.1.5: Language selection during onboarding
- AC4.1.6: Default language based on device locale

**Test Cases**:
- TC4.1.1: Set language to Tamil, verify all UI in Tamil
- TC4.1.2: Complete lesson in Telugu, verify content in Telugu
- TC4.1.3: Test voice input in all 3 languages

---

#### FR4.2: Language Switching
**Priority**: SHOULD  
**Description**: System shall allow students to switch languages mid-session.

**Acceptance Criteria**:
- AC4.2.1: Language switcher in settings menu
- AC4.2.2: Language change takes effect immediately
- AC4.2.3: Progress preserved when switching languages
- AC4.2.4: Lesson content reloaded in new language
- AC4.2.5: Confirmation dialog before switching

**Test Cases**:
- TC4.2.1: Start lesson in Hindi, switch to Tamil, verify content changes
- TC4.2.2: Complete 3 lessons in Hindi, switch to Telugu, verify progress intact

---

#### FR4.3: Content Localization
**Priority**: MUST  
**Description**: Content shall be available in all supported languages.

**Acceptance Criteria**:
- AC4.3.1: All lessons translated by native speakers
- AC4.3.2: Examples use culturally relevant context
- AC4.3.3: Images have captions in selected language
- AC4.3.4: Quiz questions and answers localized
- AC4.3.5: Audio narration in native accent

**Test Cases**:
- TC4.3.1: Review 10 lessons in each language, verify quality
- TC4.3.2: Verify examples are culturally appropriate

---

#### FR4.4: Dialect Support
**Priority**: NICE-TO-HAVE  
**Description**: System shall handle regional dialects and variations.

**Acceptance Criteria**:
- AC4.4.1: System recognizes common dialect variations
- AC4.4.2: Transcription accuracy > 80% for dialects
- AC4.4.3: Response uses standard language (not dialect)

**Test Cases**:
- TC4.4.1: Test with Bhojpuri-influenced Hindi
- TC4.4.2: Test with Kongu Tamil dialect


---

### 4.5 Curriculum Coverage (FR5)

#### FR5.1: Subject Coverage
**Priority**: MUST  
**Description**: System shall cover Math, Science, Social Studies for Classes 6-12.

**Acceptance Criteria**:
- AC5.1.1: Mathematics: Arithmetic, Algebra, Geometry, Trigonometry
- AC5.1.2: Science: Physics, Chemistry, Biology
- AC5.1.3: Social Studies: History, Geography, Civics
- AC5.1.4: Each subject has content for all grades (6-12)
- AC5.1.5: Content difficulty appropriate for grade level

**Test Cases**:
- TC5.1.1: Verify all subjects available for Grade 8
- TC5.1.2: Verify content difficulty matches grade level

---

#### FR5.2: NCERT Alignment
**Priority**: MUST  
**Description**: Content shall align with NCERT and State Board syllabi.

**Acceptance Criteria**:
- AC5.2.1: Lessons cover all NCERT chapters
- AC5.2.2: Learning objectives match NCERT curriculum
- AC5.2.3: Question difficulty matches board exam level
- AC5.2.4: Content reviewed by NCERT-certified teachers
- AC5.2.5: State Board variations included (where applicable)

**Test Cases**:
- TC5.2.1: Map lessons to NCERT chapters, verify 100% coverage
- TC5.2.2: Review by 3 teachers, verify alignment

**Dependencies**: D4 (NCERT curriculum alignment)

---

#### FR5.3: Lesson Density
**Priority**: MUST  
**Description**: System shall provide 5+ lessons per subject per grade.

**Acceptance Criteria**:
- AC5.3.1: Minimum 5 lessons per subject per grade in MVP
- AC5.3.2: Each lesson 20-30 minutes duration
- AC5.3.3: Lessons cover key concepts from syllabus
- AC5.3.4: Lessons build on each other (prerequisites defined)

**Test Cases**:
- TC5.3.1: Count lessons for Grade 8 Math, verify >= 5
- TC5.3.2: Complete lesson, verify duration 20-30 minutes

---

#### FR5.4: Practice Questions
**Priority**: MUST  
**Description**: System shall include practice questions and quizzes.

**Acceptance Criteria**:
- AC5.4.1: Each lesson has 5-10 practice questions
- AC5.4.2: Questions are multiple-choice (4 options)
- AC5.4.3: Immediate feedback on answers (correct/incorrect)
- AC5.4.4: Explanations provided for wrong answers
- AC5.4.5: Quiz at end of lesson (5 questions)

**Test Cases**:
- TC5.4.1: Complete lesson, verify 5-10 practice questions
- TC5.4.2: Answer question wrong, verify explanation shown

---

#### FR5.5: Vocational Skills
**Priority**: NICE-TO-HAVE  
**Description**: System shall offer vocational skills content.

**Acceptance Criteria**:
- AC5.5.1: Digital literacy lessons (using smartphone, internet safety)
- AC5.5.2: Financial planning lessons (savings, budgeting)
- AC5.5.3: Career guidance (different career paths)
- AC5.5.4: Life skills (communication, problem-solving)

**Test Cases**:
- TC5.5.1: Complete digital literacy lesson, verify content quality


---

### 4.6 Teacher Dashboard (FR6)

#### FR6.1: Student Progress Monitoring
**Priority**: MUST  
**Description**: Teachers shall be able to view all students' progress.

**Acceptance Criteria**:
- AC6.1.1: Dashboard shows list of all students in class
- AC6.1.2: For each student: lessons completed, average score, time spent
- AC6.1.3: Progress displayed as charts (bar, line graphs)
- AC6.1.4: Filter by subject, date range
- AC6.1.5: Sort by performance (ascending/descending)
- AC6.1.6: Export data as CSV

**Test Cases**:
- TC6.1.1: Add 30 students, verify all visible in dashboard
- TC6.1.2: Filter by Math subject, verify only Math progress shown
- TC6.1.3: Export CSV, verify data accuracy

---

#### FR6.2: Struggling Student Alerts
**Priority**: MUST  
**Description**: System shall highlight struggling students (< 50% accuracy).

**Acceptance Criteria**:
- AC6.2.1: Students with < 50% average score highlighted in red
- AC6.2.2: Alert badge shown next to student name
- AC6.2.3: Detailed view shows weak topics
- AC6.2.4: Teacher can add notes for student
- AC6.2.5: Email/SMS alert sent to teacher (optional)

**Test Cases**:
- TC6.2.1: Student scores 40% on 3 lessons, verify highlighted
- TC6.2.2: Verify weak topics identified correctly

---

#### FR6.3: Lesson Assignment
**Priority**: SHOULD  
**Description**: Teachers shall be able to assign targeted lessons.

**Acceptance Criteria**:
- AC6.3.1: Teacher can select lesson and assign to student(s)
- AC6.3.2: Assigned lessons appear in student's "To Do" list
- AC6.3.3: Due date can be set for assignment
- AC6.3.4: Student receives notification of assignment
- AC6.3.5: Teacher can track assignment completion

**Test Cases**:
- TC6.3.1: Assign lesson to 5 students, verify they receive it
- TC6.3.2: Set due date, verify reminder sent

---

#### FR6.4: Progress Reports
**Priority**: MUST  
**Description**: System shall generate weekly progress reports.

**Acceptance Criteria**:
- AC6.4.1: Report generated every Monday for previous week
- AC6.4.2: Report includes: students active, lessons completed, average score
- AC6.4.3: Report downloadable as PDF or CSV
- AC6.4.4: Report can be shared via email
- AC6.4.5: Historical reports accessible (last 12 weeks)

**Test Cases**:
- TC6.4.1: Generate report for week, verify data accuracy
- TC6.4.2: Download PDF, verify formatting

---

#### FR6.5: At-Risk Student Alerts
**Priority**: SHOULD  
**Description**: Teachers shall receive alerts for at-risk students.

**Acceptance Criteria**:
- AC6.5.1: Alert if student inactive for 7+ days
- AC6.5.2: Alert if student's score drops > 20% from average
- AC6.5.3: Alert if student attempts same lesson 3+ times
- AC6.5.4: Alerts sent via in-app notification and SMS
- AC6.5.5: Teacher can dismiss or act on alert

**Test Cases**:
- TC6.5.1: Student inactive for 8 days, verify alert sent
- TC6.5.2: Student score drops from 80% to 50%, verify alert


---

### 4.7 Gamification (FR7)

#### FR7.1: Points System
**Priority**: SHOULD  
**Description**: Students shall earn points for lesson completion.

**Acceptance Criteria**:
- AC7.1.1: 10 points awarded per lesson completed
- AC7.1.2: Bonus 5 points for scoring > 80% on quiz
- AC7.1.3: Bonus 2 points for daily streak
- AC7.1.4: Points displayed prominently in UI
- AC7.1.5: Points history visible (earned today, this week, total)

**Test Cases**:
- TC7.1.1: Complete lesson, verify 10 points awarded
- TC7.1.2: Score 90% on quiz, verify 15 points total (10 + 5 bonus)
- TC7.1.3: Use app 3 days in row, verify streak bonus

---

#### FR7.2: Badge System
**Priority**: SHOULD  
**Description**: System shall award badges at milestones.

**Acceptance Criteria**:
- AC7.2.1: Bronze badge at 5 lessons completed
- AC7.2.2: Silver badge at 15 lessons completed
- AC7.2.3: Gold badge at 30 lessons completed
- AC7.2.4: Subject-specific badges (Math Master, Science Star)
- AC7.2.5: Badge animation shown when earned
- AC7.2.6: Badges displayed in student profile

**Test Cases**:
- TC7.2.1: Complete 5 lessons, verify Bronze badge awarded
- TC7.2.2: Complete 15 lessons, verify Silver badge awarded
- TC7.2.3: Verify badge animation plays

---

#### FR7.3: Personal Progress Display
**Priority**: MUST  
**Description**: System shall display personal progress (not competitive leaderboards).

**Acceptance Criteria**:
- AC7.3.1: Progress bar shows lessons completed vs total
- AC7.3.2: Chart shows score trend over time
- AC7.3.3: Streak counter shows consecutive days
- AC7.3.4: No comparison with other students (privacy)
- AC7.3.5: Encouraging messages for milestones

**Test Cases**:
- TC7.3.1: Complete 10 of 50 lessons, verify progress bar shows 20%
- TC7.3.2: Verify no leaderboard or peer comparison visible

---

#### FR7.4: Achievement Celebrations
**Priority**: NICE-TO-HAVE  
**Description**: System shall show celebratory animations on achievements.

**Acceptance Criteria**:
- AC7.4.1: Confetti animation when badge earned
- AC7.4.2: Sound effect on milestone (can be muted)
- AC7.4.3: Congratulatory message from AI teacher
- AC7.4.4: Share achievement option (optional)

**Test Cases**:
- TC7.4.1: Earn badge, verify confetti animation plays
- TC7.4.2: Verify sound effect plays (if not muted)


---

### 4.8 Authentication & Profiles (FR8)

#### FR8.1: Student Registration
**Priority**: MUST  
**Description**: Students shall register with name, grade, language preference.

**Acceptance Criteria**:
- AC8.1.1: Registration form collects: name, grade (6-12), language, phone (optional)
- AC8.1.2: Phone number used for OTP login (if provided)
- AC8.1.3: Unique student ID generated automatically
- AC8.1.4: Profile created in database
- AC8.1.5: Registration completes in < 30 seconds

**Test Cases**:
- TC8.1.1: Register new student, verify profile created
- TC8.1.2: Register without phone, verify allowed
- TC8.1.3: Measure registration time

---

#### FR8.2: OTP-Based Login
**Priority**: MUST  
**Description**: System shall support OTP-based login via phone number.

**Acceptance Criteria**:
- AC8.2.1: Student enters phone number
- AC8.2.2: 6-digit OTP sent via SMS within 30 seconds
- AC8.2.3: OTP valid for 5 minutes
- AC8.2.4: Student enters OTP to login
- AC8.2.5: Max 3 OTP attempts, then 15-minute cooldown
- AC8.2.6: Session persists for 30 days (remember me)

**Test Cases**:
- TC8.2.1: Login with phone, verify OTP received
- TC8.2.2: Enter correct OTP, verify login successful
- TC8.2.3: Enter wrong OTP 3 times, verify cooldown enforced
- TC8.2.4: Login once, close app, reopen - verify still logged in

**Dependencies**: Amazon Cognito, SMS gateway

---

#### FR8.3: Teacher Login
**Priority**: MUST  
**Description**: Teachers shall have separate login with school admin privileges.

**Acceptance Criteria**:
- AC8.3.1: Teacher login with email and password
- AC8.3.2: Teacher can view all students in their school
- AC8.3.3: Teacher cannot access other schools' data
- AC8.3.4: Teacher role assigned by school admin
- AC8.3.5: Teacher dashboard separate from student app

**Test Cases**:
- TC8.3.1: Login as teacher, verify dashboard access
- TC8.3.2: Verify teacher can only see own school's students

---

#### FR8.4: User Preferences
**Priority**: MUST  
**Description**: System shall remember user preferences.

**Acceptance Criteria**:
- AC8.4.1: Language preference saved
- AC8.4.2: Grade level saved
- AC8.4.3: Last viewed lesson saved
- AC8.4.4: Audio volume preference saved
- AC8.4.5: Preferences synced across devices (if logged in)

**Test Cases**:
- TC8.4.1: Set language to Tamil, logout, login - verify Tamil still selected
- TC8.4.2: Start lesson, close app, reopen - verify lesson resumed


---

## 5. Non-Functional Requirements

### 5.1 Performance (NFR1)

#### NFR1.1: Page Load Time
**Priority**: MUST  
**Description**: Web app shall load in < 3 seconds on 3G network.

**Acceptance Criteria**:
- AC-NFR1.1.1: First Contentful Paint (FCP) < 1.5 seconds
- AC-NFR1.1.2: Time to Interactive (TTI) < 3 seconds
- AC-NFR1.1.3: Lighthouse performance score > 90
- AC-NFR1.1.4: Bundle size < 500KB (gzipped)

**Test Cases**:
- TC-NFR1.1.1: Test on 3G network (1 Mbps), measure load time
- TC-NFR1.1.2: Run Lighthouse audit, verify score > 90

---

#### NFR1.2: Voice Transcription Latency
**Priority**: MUST  
**Description**: Voice transcription shall complete in < 2 seconds.

**Acceptance Criteria**:
- AC-NFR1.2.1: 10-second audio transcribed in < 2 seconds (p95)
- AC-NFR1.2.2: 30-second audio transcribed in < 5 seconds (p95)
- AC-NFR1.2.3: Transcription starts within 500ms of recording stop

**Test Cases**:
- TC-NFR1.2.1: Record 10-second audio, measure transcription time
- TC-NFR1.2.2: Test with 100 samples, verify p95 < 2 seconds

---

#### NFR1.3: AI Response Generation Time
**Priority**: MUST  
**Description**: AI response generation shall complete in < 5 seconds.

**Acceptance Criteria**:
- AC-NFR1.3.1: Simple questions answered in < 3 seconds (p50)
- AC-NFR1.3.2: Complex questions answered in < 5 seconds (p95)
- AC-NFR1.3.3: Timeout after 10 seconds with error message

**Test Cases**:
- TC-NFR1.3.1: Ask 100 questions, measure response time distribution
- TC-NFR1.3.2: Verify p50 < 3s, p95 < 5s

---

#### NFR1.4: Audio Playback Start Time
**Priority**: MUST  
**Description**: Audio playback shall start quickly.

**Acceptance Criteria**:
- AC-NFR1.4.1: Cached audio starts in < 1 second
- AC-NFR1.4.2: Generated audio starts in < 3 seconds
- AC-NFR1.4.3: Streaming starts before full audio downloaded

**Test Cases**:
- TC-NFR1.4.1: Play cached audio, measure time to first sound
- TC-NFR1.4.2: Generate new audio, measure playback start time

---

#### NFR1.5: Offline Mode Responsiveness
**Priority**: MUST  
**Description**: Offline mode shall have < 500ms UI response time.

**Acceptance Criteria**:
- AC-NFR1.5.1: Button clicks respond in < 100ms
- AC-NFR1.5.2: Page navigation completes in < 500ms
- AC-NFR1.5.3: Lesson content loads in < 300ms from IndexedDB

**Test Cases**:
- TC-NFR1.5.1: Enable airplane mode, measure UI responsiveness
- TC-NFR1.5.2: Navigate between pages, verify < 500ms


---

### 5.2 Scalability (NFR2)

#### NFR2.1: Concurrent Users (Year 1)
**Priority**: MUST  
**Description**: System shall support 1 lakh (100,000) concurrent users.

**Acceptance Criteria**:
- AC-NFR2.1.1: API Gateway handles 10,000 requests/second
- AC-NFR2.1.2: Lambda auto-scales to 1000+ concurrent executions
- AC-NFR2.1.3: DynamoDB handles 50,000 reads/writes per second
- AC-NFR2.1.4: No performance degradation under load

**Test Cases**:
- TC-NFR2.1.1: Load test with 100,000 concurrent users
- TC-NFR2.1.2: Verify response time < 1 second at peak load

---

#### NFR2.2: User Growth (Year 2)
**Priority**: SHOULD  
**Description**: System shall scale to 10 lakh (1 million) users by Year 2.

**Acceptance Criteria**:
- AC-NFR2.2.1: Architecture supports horizontal scaling
- AC-NFR2.2.2: Database partitioning strategy defined
- AC-NFR2.2.3: Multi-region deployment plan ready
- AC-NFR2.2.4: Cost per user remains < ₹10/month at scale

**Test Cases**:
- TC-NFR2.2.1: Capacity planning for 1M users
- TC-NFR2.2.2: Cost projection at 1M users

---

#### NFR2.3: Auto-Scaling
**Priority**: MUST  
**Description**: Backend shall auto-scale based on demand.

**Acceptance Criteria**:
- AC-NFR2.3.1: Lambda scales automatically (no manual intervention)
- AC-NFR2.3.2: DynamoDB on-demand scaling enabled
- AC-NFR2.3.3: CloudFront handles traffic spikes automatically
- AC-NFR2.3.4: Scale-up time < 1 minute

**Test Cases**:
- TC-NFR2.3.1: Simulate traffic spike, verify auto-scaling
- TC-NFR2.3.2: Measure scale-up time

---

#### NFR2.4: Database Performance
**Priority**: MUST  
**Description**: Database shall handle 1M+ records without degradation.

**Acceptance Criteria**:
- AC-NFR2.4.1: Query latency < 10ms for 1M records
- AC-NFR2.4.2: Write latency < 20ms for 1M records
- AC-NFR2.4.3: Indexes optimized for common queries
- AC-NFR2.4.4: Partition key strategy prevents hot partitions

**Test Cases**:
- TC-NFR2.4.1: Load 1M records, measure query performance
- TC-NFR2.4.2: Verify no hot partition issues


---

### 5.3 Availability & Reliability (NFR3)

#### NFR3.1: System Uptime
**Priority**: MUST  
**Description**: System shall have 99.5% uptime (excluding planned maintenance).

**Acceptance Criteria**:
- AC-NFR3.1.1: Maximum 3.6 hours downtime per month
- AC-NFR3.1.2: Planned maintenance during off-peak hours (2-4 AM IST)
- AC-NFR3.1.3: Maintenance notifications sent 24 hours in advance
- AC-NFR3.1.4: Health checks every 30 seconds

**Test Cases**:
- TC-NFR3.1.1: Monitor uptime for 1 month, verify > 99.5%
- TC-NFR3.1.2: Verify health check endpoint responds

---

#### NFR3.2: Offline Mode Reliability
**Priority**: MUST  
**Description**: Offline mode shall function with 100% reliability.

**Acceptance Criteria**:
- AC-NFR3.2.1: No crashes when offline
- AC-NFR3.2.2: All downloaded content accessible offline
- AC-NFR3.2.3: Progress saved reliably to local storage
- AC-NFR3.2.4: No data loss when switching online/offline

**Test Cases**:
- TC-NFR3.2.1: Use app offline for 1 hour, verify no crashes
- TC-NFR3.2.2: Complete 10 lessons offline, verify all progress saved

---

#### NFR3.3: Graceful Degradation
**Priority**: MUST  
**Description**: System shall gracefully degrade if AI services unavailable.

**Acceptance Criteria**:
- AC-NFR3.3.1: If Bedrock unavailable, show cached responses
- AC-NFR3.3.2: If Polly unavailable, use Web Speech API
- AC-NFR3.3.3: If Transcribe unavailable, use Web Speech API
- AC-NFR3.3.4: User notified of degraded mode with clear message

**Test Cases**:
- TC-NFR3.3.1: Disable Bedrock, verify cached responses work
- TC-NFR3.3.2: Disable Polly, verify Web Speech API fallback

---

#### NFR3.4: Data Sync Reliability
**Priority**: MUST  
**Description**: Data sync shall retry with exponential backoff on failures.

**Acceptance Criteria**:
- AC-NFR3.4.1: Failed sync retries after 1s, 2s, 4s, 8s, 16s
- AC-NFR3.4.2: Max 5 retry attempts before giving up
- AC-NFR3.4.3: User notified if sync fails after retries
- AC-NFR3.4.4: Manual sync option available

**Test Cases**:
- TC-NFR3.4.1: Simulate network failure, verify retry logic
- TC-NFR3.4.2: Verify exponential backoff timing


---

### 5.4 Usability (NFR4)

#### NFR4.1: Touch Target Size
**Priority**: MUST  
**Description**: UI shall be operable with large fingers (minimum 44px touch targets).

**Acceptance Criteria**:
- AC-NFR4.1.1: All buttons minimum 44x44 pixels
- AC-NFR4.1.2: Spacing between buttons minimum 8px
- AC-NFR4.1.3: Touch targets meet WCAG 2.1 Level AAA
- AC-NFR4.1.4: No accidental clicks on adjacent buttons

**Test Cases**:
- TC-NFR4.1.1: Measure all button sizes, verify >= 44px
- TC-NFR4.1.2: User testing with 10 rural students

---

#### NFR4.2: Outdoor Readability
**Priority**: MUST  
**Description**: UI shall be readable in bright sunlight.

**Acceptance Criteria**:
- AC-NFR4.2.1: Contrast ratio minimum 7:1 (WCAG AAA)
- AC-NFR4.2.2: Font size minimum 18px for body text
- AC-NFR4.2.3: No light gray text on white background
- AC-NFR4.2.4: Dark mode option available

**Test Cases**:
- TC-NFR4.2.1: Test contrast ratios with accessibility tools
- TC-NFR4.2.2: User testing in bright sunlight

---

#### NFR4.3: Simple Language
**Priority**: MUST  
**Description**: UI shall use simple language (5th-grade reading level).

**Acceptance Criteria**:
- AC-NFR4.3.1: Flesch-Kincaid grade level < 5 for all UI text
- AC-NFR4.3.2: No technical jargon
- AC-NFR4.3.3: Short sentences (< 15 words)
- AC-NFR4.3.4: Active voice preferred over passive

**Test Cases**:
- TC-NFR4.3.1: Run readability analysis on all UI text
- TC-NFR4.3.2: User comprehension testing

---

#### NFR4.4: Bilingual Labels
**Priority**: SHOULD  
**Description**: UI shall provide bilingual labels (vernacular + English).

**Acceptance Criteria**:
- AC-NFR4.4.1: Key actions have both vernacular and English labels
- AC-NFR4.4.2: English text smaller and secondary
- AC-NFR4.4.3: Icons used alongside text for clarity

**Test Cases**:
- TC-NFR4.4.1: Review UI, verify bilingual labels present

---

#### NFR4.5: Zero Prior Experience
**Priority**: MUST  
**Description**: App shall be usable without prior smartphone experience.

**Acceptance Criteria**:
- AC-NFR4.5.1: Interactive tutorial on first launch
- AC-NFR4.5.2: Tooltips for all major features
- AC-NFR4.5.3: Voice instructions available
- AC-NFR4.5.4: 90% of first-time users complete tutorial

**Test Cases**:
- TC-NFR4.5.1: User testing with 20 first-time smartphone users
- TC-NFR4.5.2: Measure tutorial completion rate


---

### 5.5 Accessibility (NFR5)

#### NFR5.1: Device Affordability
**Priority**: MUST  
**Description**: System shall work on smartphones costing ₹3000+.

**Acceptance Criteria**:
- AC-NFR5.1.1: Tested on Redmi 9A, Samsung Galaxy M01 (₹3000-₹5000)
- AC-NFR5.1.2: No lag or crashes on low-end devices
- AC-NFR5.1.3: Animations disabled on low-end devices
- AC-NFR5.1.4: Memory usage < 100MB

**Test Cases**:
- TC-NFR5.1.1: Test on 5 different low-end devices
- TC-NFR5.1.2: Monitor memory usage, verify < 100MB

---

#### NFR5.2: Android Version Support
**Priority**: MUST  
**Description**: System shall function on Android 8+ (covering 95% rural devices).

**Acceptance Criteria**:
- AC-NFR5.2.1: Tested on Android 8, 9, 10, 11, 12, 13
- AC-NFR5.2.2: No features broken on older Android versions
- AC-NFR5.2.3: Polyfills for missing browser features

**Test Cases**:
- TC-NFR5.2.1: Test on Android 8 device, verify all features work
- TC-NFR5.2.2: Automated testing on BrowserStack

---

#### NFR5.3: Screen Reader Support
**Priority**: NICE-TO-HAVE  
**Description**: System shall support screen readers for visually impaired.

**Acceptance Criteria**:
- AC-NFR5.3.1: All images have alt text
- AC-NFR5.3.2: ARIA labels on interactive elements
- AC-NFR5.3.3: Keyboard navigation supported
- AC-NFR5.3.4: Focus indicators visible

**Test Cases**:
- TC-NFR5.3.1: Test with TalkBack screen reader
- TC-NFR5.3.2: Automated accessibility audit

---

#### NFR5.4: Device Specifications
**Priority**: MUST  
**Description**: System shall work on devices with 2GB RAM, 16GB storage.

**Acceptance Criteria**:
- AC-NFR5.4.1: App size < 5MB (initial download)
- AC-NFR5.4.2: Lesson pack < 50MB each
- AC-NFR5.4.3: Total storage usage < 500MB (10 lessons)
- AC-NFR5.4.4: RAM usage < 100MB during operation

**Test Cases**:
- TC-NFR5.4.1: Measure app size, verify < 5MB
- TC-NFR5.4.2: Download 10 lessons, measure storage usage


---

### 5.6 Security (NFR6)

#### NFR6.1: Encrypted Communication
**Priority**: MUST  
**Description**: All API communication shall use HTTPS (TLS 1.3).

**Acceptance Criteria**:
- AC-NFR6.1.1: All API endpoints use HTTPS
- AC-NFR6.1.2: TLS 1.3 or TLS 1.2 minimum
- AC-NFR6.1.3: Valid SSL certificate from trusted CA
- AC-NFR6.1.4: HTTP requests redirect to HTTPS
- AC-NFR6.1.5: HSTS header enabled

**Test Cases**:
- TC-NFR6.1.1: SSL Labs test, verify A+ rating
- TC-NFR6.1.2: Verify TLS version with OpenSSL

---

#### NFR6.2: Data Encryption at Rest
**Priority**: MUST  
**Description**: User data shall be encrypted at rest (AES-256).

**Acceptance Criteria**:
- AC-NFR6.2.1: DynamoDB encryption enabled
- AC-NFR6.2.2: S3 bucket encryption enabled
- AC-NFR6.2.3: Encryption keys managed by AWS KMS
- AC-NFR6.2.4: Key rotation every 90 days

**Test Cases**:
- TC-NFR6.2.1: Verify DynamoDB encryption settings
- TC-NFR6.2.2: Verify S3 encryption settings

---

#### NFR6.3: Privacy Compliance
**Priority**: MUST  
**Description**: System shall comply with GDPR and COPPA (children's data).

**Acceptance Criteria**:
- AC-NFR6.3.1: Parental consent for users under 13
- AC-NFR6.3.2: Data deletion on request (within 30 days)
- AC-NFR6.3.3: Data export on request (within 7 days)
- AC-NFR6.3.4: Privacy policy in simple language
- AC-NFR6.3.5: No third-party data sharing without consent

**Test Cases**:
- TC-NFR6.3.1: Request data deletion, verify completed in 30 days
- TC-NFR6.3.2: Request data export, verify received in 7 days

---

#### NFR6.4: Rate Limiting
**Priority**: MUST  
**Description**: System shall implement rate limiting (100 requests/min/user).

**Acceptance Criteria**:
- AC-NFR6.4.1: API Gateway throttling at 100 req/min per user
- AC-NFR6.4.2: 429 status code returned when limit exceeded
- AC-NFR6.4.3: Retry-After header included in response
- AC-NFR6.4.4: Rate limit resets every minute

**Test Cases**:
- TC-NFR6.4.1: Make 101 requests in 1 minute, verify 101st blocked
- TC-NFR6.4.2: Verify 429 status code and Retry-After header

---

#### NFR6.5: Secure Logging
**Priority**: MUST  
**Description**: System shall mask sensitive data in logs.

**Acceptance Criteria**:
- AC-NFR6.5.1: Phone numbers masked (show only last 2 digits)
- AC-NFR6.5.2: Student names not logged
- AC-NFR6.5.3: Audio content not logged
- AC-NFR6.5.4: Only student IDs logged (not PII)

**Test Cases**:
- TC-NFR6.5.1: Review CloudWatch logs, verify no PII


---

### 5.7 Cost Efficiency (NFR7)

#### NFR7.1: Cost Per Student
**Priority**: MUST  
**Description**: Infrastructure cost shall be < ₹1 per student per month.

**Acceptance Criteria**:
- AC-NFR7.1.1: Total AWS cost < ₹1 lakh for 1 lakh students/month
- AC-NFR7.1.2: Cost breakdown tracked per service
- AC-NFR7.1.3: Cost alerts set at 80% of budget
- AC-NFR7.1.4: Monthly cost reports generated

**Test Cases**:
- TC-NFR7.1.1: Monitor costs for 1 month, verify < ₹1/student
- TC-NFR7.1.2: Verify cost alerts trigger correctly

---

#### NFR7.2: AWS Free Tier Usage
**Priority**: SHOULD  
**Description**: System shall use AWS free tier where possible.

**Acceptance Criteria**:
- AC-NFR7.2.1: Lambda free tier: 1M requests/month
- AC-NFR7.2.2: DynamoDB free tier: 25GB storage
- AC-NFR7.2.3: S3 free tier: 5GB storage
- AC-NFR7.2.4: CloudFront free tier: 50GB transfer

**Test Cases**:
- TC-NFR7.2.1: Monitor free tier usage, optimize to stay within limits

---

#### NFR7.3: API Call Optimization
**Priority**: MUST  
**Description**: AI API calls shall be optimized (caching, batching).

**Acceptance Criteria**:
- AC-NFR7.3.1: Cache hit rate > 60% for Bedrock calls
- AC-NFR7.3.2: Polly audio cached for 7 days
- AC-NFR7.3.3: Transcribe calls batched where possible
- AC-NFR7.3.4: Bedrock token usage < 1000 per conversation

**Test Cases**:
- TC-NFR7.3.1: Monitor cache hit rate, verify > 60%
- TC-NFR7.3.2: Measure Bedrock token usage per conversation

---

#### NFR7.4: Storage Optimization
**Priority**: SHOULD  
**Description**: Storage shall use S3 Intelligent-Tiering for cost optimization.

**Acceptance Criteria**:
- AC-NFR7.4.1: S3 Intelligent-Tiering enabled
- AC-NFR7.4.2: Infrequently accessed data moved to cheaper tier
- AC-NFR7.4.3: Old data archived to Glacier after 90 days
- AC-NFR7.4.4: Storage costs reduced by 30% vs standard S3

**Test Cases**:
- TC-NFR7.4.1: Verify Intelligent-Tiering enabled
- TC-NFR7.4.2: Compare costs with standard S3


---

### 5.8 Maintainability (NFR8)

#### NFR8.1: Code Standards
**Priority**: MUST  
**Description**: Code shall follow industry standards.

**Acceptance Criteria**:
- AC-NFR8.1.1: Python code follows PEP8
- AC-NFR8.1.2: JavaScript code follows Airbnb style guide
- AC-NFR8.1.3: Linting enforced in CI/CD pipeline
- AC-NFR8.1.4: Code reviews required for all PRs

**Test Cases**:
- TC-NFR8.1.1: Run linter, verify no errors
- TC-NFR8.1.2: Verify CI/CD blocks non-compliant code

---

#### NFR8.2: Test Coverage
**Priority**: MUST  
**Description**: All functions shall have unit test coverage > 80%.

**Acceptance Criteria**:
- AC-NFR8.2.1: Unit test coverage > 80% for backend
- AC-NFR8.2.2: Unit test coverage > 80% for frontend
- AC-NFR8.2.3: Integration tests for all API endpoints
- AC-NFR8.2.4: E2E tests for critical user flows

**Test Cases**:
- TC-NFR8.2.1: Run coverage report, verify > 80%
- TC-NFR8.2.2: Verify CI/CD blocks PRs with < 80% coverage

---

#### NFR8.3: API Documentation
**Priority**: MUST  
**Description**: API documentation shall be auto-generated.

**Acceptance Criteria**:
- AC-NFR8.3.1: OpenAPI/Swagger spec generated from code
- AC-NFR8.3.2: API docs hosted at /api/docs
- AC-NFR8.3.3: Request/response examples included
- AC-NFR8.3.4: Authentication requirements documented

**Test Cases**:
- TC-NFR8.3.1: Verify API docs accessible
- TC-NFR8.3.2: Verify docs match actual API behavior

---

#### NFR8.4: Infrastructure as Code
**Priority**: MUST  
**Description**: Infrastructure shall be defined as code (AWS CDK).

**Acceptance Criteria**:
- AC-NFR8.4.1: All AWS resources defined in CDK
- AC-NFR8.4.2: Infrastructure versioned in Git
- AC-NFR8.4.3: Deployment automated via CI/CD
- AC-NFR8.4.4: Rollback possible within 5 minutes

**Test Cases**:
- TC-NFR8.4.1: Deploy infrastructure from CDK, verify success
- TC-NFR8.4.2: Test rollback procedure


---

### 5.9 Localization (NFR9)

#### NFR9.1: Externalized Text
**Priority**: MUST  
**Description**: UI text shall be externalized for easy translation.

**Acceptance Criteria**:
- AC-NFR9.1.1: All UI strings in i18n files (JSON)
- AC-NFR9.1.2: No hardcoded strings in code
- AC-NFR9.1.3: Translation keys follow naming convention
- AC-NFR9.1.4: Missing translations flagged in development

**Test Cases**:
- TC-NFR9.1.1: Search codebase for hardcoded strings
- TC-NFR9.1.2: Verify all strings in i18n files

---

#### NFR9.2: Date/Time Formats
**Priority**: SHOULD  
**Description**: Date/time formats shall respect local conventions.

**Acceptance Criteria**:
- AC-NFR9.2.1: Dates in DD/MM/YYYY format (Indian standard)
- AC-NFR9.2.2: Time in 12-hour format with AM/PM
- AC-NFR9.2.3: Timezone: IST (Indian Standard Time)
- AC-NFR9.2.4: Relative dates ("2 days ago") in vernacular

**Test Cases**:
- TC-NFR9.2.1: Verify date format across UI
- TC-NFR9.2.2: Verify time format across UI

---

#### NFR9.3: Regional Accents
**Priority**: SHOULD  
**Description**: Audio voices shall use region-appropriate accents.

**Acceptance Criteria**:
- AC-NFR9.3.1: Hindi voice uses neutral North Indian accent
- AC-NFR9.3.2: Tamil voice uses neutral Tamil Nadu accent
- AC-NFR9.3.3: Telugu voice uses neutral Andhra Pradesh accent
- AC-NFR9.3.4: User can select preferred accent (future)

**Test Cases**:
- TC-NFR9.3.1: User testing with native speakers
- TC-NFR9.3.2: Verify accent acceptability rating > 80%


---

## 6. Constraints

### C1: AWS Services Only
**Description**: Must use AWS services only (hackathon requirement).  
**Impact**: Cannot use Google Cloud, Azure, or other cloud providers.  
**Rationale**: AWS AI for Bharat Hackathon requirement.

### C2: Amazon Bedrock Required
**Description**: Must use Amazon Bedrock for AI (hackathon requirement).  
**Impact**: Cannot use OpenAI GPT-4, Anthropic Claude direct API, or other LLMs.  
**Rationale**: AWS AI for Bharat Hackathon requirement.

### C3: Budget Constraint
**Description**: Budget constraint of ₹50 lakhs for Year 1.  
**Impact**: Must optimize costs aggressively, use free tier, caching.  
**Mitigation**: AWS credits from hackathon, cost monitoring, auto-scaling.

### C4: Timeline Constraint
**Description**: MVP in 3 months, full launch in 6 months.  
**Impact**: Must prioritize features, use agile development, minimal viable features.  
**Mitigation**: Focus on MUST requirements first, defer NICE-TO-HAVE features.

### C5: Team Size Constraint
**Description**: Team size limited to 5 people (hackathon constraint).  
**Impact**: Cannot build all features, must use managed services, minimize custom code.  
**Mitigation**: Use AWS managed services, open-source libraries, focus on core features.

### C6: Offline Requirement
**Description**: Must work offline (rural internet unavailability).  
**Impact**: Complex architecture with Service Workers, IndexedDB, sync logic.  
**Rationale**: 60% of rural India has no reliable internet.

### C7: Vernacular Language Requirement
**Description**: Must support vernacular languages (not just English).  
**Impact**: Content creation effort 3x, translation costs, voice quality varies by language.  
**Rationale**: 70% of rural students not comfortable with English.

---

## 7. Assumptions and Dependencies

### 7.1 Assumptions

#### A1: Device Availability
**Assumption**: Students have access to basic smartphones (₹3000+).  
**Validation**: Survey of 100 rural households shows 80% have smartphones.  
**Risk**: If false, may need feature phone support (SMS-based).

#### A2: Occasional Connectivity
**Assumption**: Students have occasional WiFi/mobile data for initial download.  
**Validation**: Schools have WiFi, students visit weekly for downloads.  
**Risk**: If false, may need USB/SD card distribution of content.

#### A3: Teacher Device Access
**Assumption**: Teachers have smartphones or computers for dashboard access.  
**Validation**: 95% of government teachers have smartphones.  
**Risk**: If false, may need paper-based reports.

#### A4: Shared Device Access
**Assumption**: Schools have at least 1 device per 10 students for shared access.  
**Validation**: Government schemes provide tablets to schools.  
**Risk**: If false, may need to provide devices.

#### A5: Government Subsidies
**Assumption**: Government will provide subsidies for at-scale deployment.  
**Validation**: Discussions with State Education Departments ongoing.  
**Risk**: If false, may need alternative funding (CSR, NGOs).


### 7.2 Dependencies

#### D1: Amazon Bedrock Availability
**Dependency**: Amazon Bedrock Claude 3.5 Sonnet availability in India region.  
**Status**: Available in us-east-1, ap-south-1 (Mumbai).  
**Risk**: If unavailable, may need to use us-east-1 (higher latency).  
**Mitigation**: Test latency from India to us-east-1, optimize prompts.

#### D2: Amazon Polly Voice Quality
**Dependency**: Amazon Polly Hindi/Tamil/Telugu voice quality acceptable.  
**Status**: Hindi Neural voice (Kajal) available, Tamil/Telugu Standard voices.  
**Risk**: If quality poor, user satisfaction drops.  
**Mitigation**: User testing, fallback to Web Speech API, request Neural voices for Tamil/Telugu.

#### D3: Amazon Transcribe Accuracy
**Dependency**: Amazon Transcribe vernacular language accuracy > 90%.  
**Status**: Hindi accuracy ~85%, Tamil/Telugu ~80%.  
**Risk**: If accuracy poor, user frustration increases.  
**Mitigation**: Custom vocabulary, noise cancellation, user can edit transcription.

#### D4: NCERT Curriculum Alignment
**Dependency**: NCERT curriculum alignment with lesson content.  
**Status**: NCERT curriculum publicly available, content creators familiar.  
**Risk**: If misaligned, schools won't adopt.  
**Mitigation**: Review by NCERT-certified teachers, pilot testing in schools.

#### D5: NGO Partnerships
**Dependency**: NGO partnerships for pilot school access.  
**Status**: Discussions ongoing with Pratham, Teach For India.  
**Risk**: If partnerships fail, pilot delayed.  
**Mitigation**: Direct outreach to government schools, alternative NGOs.

---

## 8. Acceptance Criteria

### AC1: Voice Lesson Completion
**Criteria**: 90% of test users can complete a full lesson via voice.  
**Measurement**: User testing with 100 rural students, track completion rate.  
**Target**: 90 out of 100 students complete lesson without assistance.

### AC2: Offline Mode Reliability
**Criteria**: Offline mode works flawlessly for 95% of use cases.  
**Measurement**: Test 100 offline scenarios, track success rate.  
**Target**: 95 out of 100 scenarios work without errors.

### AC3: Student Satisfaction
**Criteria**: 80% student satisfaction score (post-lesson survey).  
**Measurement**: 5-point Likert scale survey after each lesson.  
**Target**: Average score >= 4.0 out of 5.0.

### AC4: Transcription Accuracy
**Criteria**: < 10% error rate in voice transcription.  
**Measurement**: Transcribe 1000 sample questions, manually verify accuracy.  
**Target**: < 100 errors out of 1000 transcriptions.

### AC5: Teacher Dashboard Usability
**Criteria**: Teachers can monitor student progress in real-time.  
**Measurement**: Teacher testing with 20 teachers, track task completion.  
**Target**: 100% of teachers can view progress, identify struggling students.


---

## 9. Risks and Mitigations

### Risk Matrix

| Risk ID | Risk Description | Impact | Probability | Mitigation Strategy |
|---------|------------------|--------|-------------|---------------------|
| R1 | Poor voice recognition accuracy | High | Medium | Custom vocabulary, noise cancellation, user can edit transcription |
| R2 | Students misuse free data | Medium | High | Rate limiting (100 req/min), teacher monitoring, usage analytics |
| R3 | AWS costs exceed budget | High | Medium | Aggressive caching, optimize API calls, AWS credits, cost alerts |
| R4 | Low adoption by teachers | High | Low | Training programs, simple UI, teacher incentives, success stories |
| R5 | Internet unavailability | Medium | High | Offline-first architecture, download at school WiFi, USB distribution |
| R6 | Content quality issues | High | Medium | Review by subject experts, pilot testing, iterative improvement |
| R7 | Device compatibility issues | Medium | Medium | Test on 10+ device models, progressive enhancement, fallbacks |
| R8 | Language translation errors | Medium | Medium | Native speaker translators, cultural review, user feedback |
| R9 | Security breach | High | Low | Encryption, rate limiting, security audits, AWS WAF |
| R10 | Scalability bottlenecks | Medium | Low | Load testing, auto-scaling, multi-region deployment |

### Detailed Risk Analysis

#### R1: Poor Voice Recognition Accuracy
**Impact**: High - Users frustrated, abandon app  
**Probability**: Medium - Transcribe accuracy varies by language  
**Mitigation**:
- Custom vocabulary for educational terms
- Noise cancellation and echo suppression
- User can edit transcription before submission
- Fallback to Web Speech API
- Continuous improvement based on user feedback

**Contingency**: If accuracy < 80%, add text input option as fallback.

---

#### R2: Students Misuse Free Data
**Impact**: Medium - Increased costs, server overload  
**Probability**: High - Students may spam questions  
**Mitigation**:
- Rate limiting: 100 requests per minute per user
- Teacher monitoring dashboard
- Usage analytics to detect abuse patterns
- Temporary account suspension for abuse

**Contingency**: Implement CAPTCHA for suspicious activity.

---

#### R3: AWS Costs Exceed Budget
**Impact**: High - Project becomes unsustainable  
**Probability**: Medium - AI API costs can spike  
**Mitigation**:
- Aggressive caching (60%+ cache hit rate)
- Optimize Bedrock prompts (reduce tokens)
- Use Web Speech API first (free)
- AWS credits from hackathon
- Cost alerts at 80% of budget
- Auto-scaling limits

**Contingency**: Reduce features, increase caching, seek additional funding.

---

#### R4: Low Adoption by Teachers
**Impact**: High - No monitoring, students unsupervised  
**Probability**: Low - Teachers generally supportive  
**Mitigation**:
- Simple, intuitive teacher dashboard
- Training programs (2-hour workshop)
- Teacher incentives (certificates, recognition)
- Success stories and testimonials
- Ongoing support (helpline, WhatsApp group)

**Contingency**: Hire dedicated teacher support staff.

---

#### R5: Internet Unavailability
**Impact**: Medium - Cannot download new content  
**Probability**: High - 60% of rural areas have poor connectivity  
**Mitigation**:
- Offline-first architecture (core requirement)
- Download lesson packs at school WiFi
- USB/SD card distribution of content
- Differential sync to minimize bandwidth
- Pre-cache common questions

**Contingency**: Partner with schools to provide WiFi access points.


---

## 10. Future Requirements (Post-MVP)

### FR9: Extended Language Support
**Priority**: SHOULD (Year 2)  
**Description**: Support for 9 more Indian languages (total 12).

**Languages**: Marathi, Gujarati, Kannada, Malayalam, Odia, Punjabi, Assamese, Urdu, Bengali

**Acceptance Criteria**:
- All UI and content available in 12 languages
- Voice input/output for all 12 languages
- Cultural localization for each language

**Effort Estimate**: 6 months, 3 content creators

---

### FR10: Peer-to-Peer Learning
**Priority**: NICE-TO-HAVE (Year 2)  
**Description**: Students can help each other through voice chat.

**Features**:
- Group study sessions (max 5 students)
- Voice chat with moderation
- Peer doubt solving
- Collaborative problem solving

**Acceptance Criteria**:
- Students can create/join study groups
- Voice chat works with low latency (< 500ms)
- Inappropriate content filtered

**Effort Estimate**: 4 months, 2 developers

---

### FR11: Parent App
**Priority**: SHOULD (Year 2)  
**Description**: Parent app for progress monitoring.

**Features**:
- SMS notifications for milestones
- Simple progress dashboard
- Weekly reports
- Direct messaging with teacher

**Acceptance Criteria**:
- Parents can view child's progress
- SMS sent for major milestones
- App works on basic smartphones

**Effort Estimate**: 3 months, 1 developer

---

### FR12: DIKSHA Integration
**Priority**: SHOULD (Year 2)  
**Description**: Integration with government DIKSHA platform.

**Features**:
- Single sign-on with DIKSHA
- Content sync with DIKSHA
- Progress reporting to DIKSHA
- Compliance with DIKSHA standards

**Acceptance Criteria**:
- Students can login with DIKSHA credentials
- Content available on DIKSHA platform
- Progress synced to DIKSHA

**Effort Estimate**: 6 months, 2 developers

**Dependencies**: DIKSHA API access, government approval

---

### FR13: Entrance Exam Preparation
**Priority**: NICE-TO-HAVE (Year 3)  
**Description**: AI tutoring for entrance exams (JEE, NEET).

**Features**:
- JEE/NEET syllabus coverage
- Previous year questions
- Mock tests
- Performance analytics

**Acceptance Criteria**:
- 1000+ practice questions per exam
- Mock tests simulate actual exam
- Detailed performance analysis

**Effort Estimate**: 12 months, 5 content creators


---

## 11. Success Metrics

### M1: User Adoption
**Metric**: 50,000 active users by end of Year 1  
**Measurement**: Monthly Active Users (MAU) from analytics  
**Target**: 50,000 MAU by December 2026  
**Current**: 0 (pre-launch)

**Milestones**:
- Month 3 (MVP): 1,000 users (pilot schools)
- Month 6 (Launch): 10,000 users
- Month 9: 25,000 users
- Month 12: 50,000 users

---

### M2: Engagement
**Metric**: 70% lesson completion rate  
**Measurement**: (Lessons completed / Lessons started) × 100  
**Target**: 70% completion rate  
**Benchmark**: Industry average 40-50%

**Tracking**:
- Daily completion rate
- Weekly completion rate
- Completion rate by subject
- Completion rate by grade

---

### M3: Learning Outcomes
**Metric**: 60% improvement in learning outcomes vs control group  
**Measurement**: Pre-test and post-test scores  
**Target**: 60% improvement in test scores  
**Study Design**: Randomized controlled trial with 1000 students

**Methodology**:
- Control group: Traditional teaching
- Treatment group: Pragya Shiksha + traditional teaching
- Pre-test before intervention
- Post-test after 3 months
- Compare score improvements

---

### M4: Teacher Satisfaction
**Metric**: 80% teacher satisfaction  
**Measurement**: Teacher survey (5-point Likert scale)  
**Target**: Average score >= 4.0 out of 5.0  
**Survey Questions**:
- Ease of use (1-5)
- Usefulness for monitoring (1-5)
- Time saved (1-5)
- Would recommend to others (1-5)

---

### M5: Retention
**Metric**: < 5% dropout rate from app  
**Measurement**: (Users who stopped using / Total users) × 100  
**Target**: < 5% monthly dropout rate  
**Benchmark**: EdTech apps typically have 20-30% dropout

**Tracking**:
- Users inactive for 7+ days
- Users inactive for 30+ days
- Reasons for dropout (exit survey)

---

### Additional Metrics

#### M6: Performance Metrics
- Page load time: < 3 seconds (p95)
- API response time: < 500ms (p95)
- Offline mode reliability: 99%+
- Voice transcription accuracy: > 90%

#### M7: Cost Metrics
- Cost per student: < ₹1/month
- AWS cost: < ₹1 lakh/month (for 1 lakh users)
- Cost per lesson completion: < ₹0.50

#### M8: Quality Metrics
- Bug count: < 10 critical bugs/month
- Crash rate: < 0.1%
- User-reported issues: < 5% of users
- Content quality rating: > 4.0/5.0


---

## 12. Glossary

### Technical Terms

**API (Application Programming Interface)**: Interface for software components to communicate.

**AWS (Amazon Web Services)**: Cloud computing platform by Amazon.

**Bedrock**: AWS service for accessing foundation models (LLMs).

**CDN (Content Delivery Network)**: Distributed network of servers for fast content delivery.

**DynamoDB**: AWS NoSQL database service.

**IndexedDB**: Browser database for storing large amounts of data offline.

**Lambda**: AWS serverless compute service.

**NCERT**: National Council of Educational Research and Training (India's curriculum body).

**Polly**: AWS text-to-speech service.

**PWA (Progressive Web App)**: Web app that works like a native app.

**Service Worker**: Browser script that runs in background, enables offline functionality.

**Transcribe**: AWS speech-to-text service.

**TTS (Text-to-Speech)**: Technology that converts text to spoken audio.

**STT (Speech-to-Text)**: Technology that converts spoken audio to text.

---

### Domain Terms

**Adaptive Learning**: Educational approach that adjusts to student's level.

**Code-Switching**: Mixing two languages in conversation (e.g., Hinglish).

**COPPA**: Children's Online Privacy Protection Act (US law for children's data).

**DIKSHA**: Government of India's digital learning platform.

**GDPR**: General Data Protection Regulation (EU privacy law).

**Gamification**: Using game elements (points, badges) to motivate learning.

**Lesson Pack**: Compressed bundle of educational content for offline use.

**OTP (One-Time Password)**: Temporary password sent via SMS for authentication.

**Vernacular**: Native language of a region (e.g., Hindi, Tamil, Telugu).

---

### Acronyms

**AC**: Acceptance Criteria  
**API**: Application Programming Interface  
**AWS**: Amazon Web Services  
**CDN**: Content Delivery Network  
**COPPA**: Children's Online Privacy Protection Act  
**CSR**: Corporate Social Responsibility  
**FR**: Functional Requirement  
**GDPR**: General Data Protection Regulation  
**GSI**: Global Secondary Index (DynamoDB)  
**HTTPS**: Hypertext Transfer Protocol Secure  
**IAM**: Identity and Access Management  
**JWT**: JSON Web Token  
**KMS**: Key Management Service  
**LLM**: Large Language Model  
**MAU**: Monthly Active Users  
**MVP**: Minimum Viable Product  
**NCERT**: National Council of Educational Research and Training  
**NFR**: Non-Functional Requirement  
**NGO**: Non-Governmental Organization  
**OTP**: One-Time Password  
**PII**: Personally Identifiable Information  
**PWA**: Progressive Web App  
**RTO**: Recovery Time Objective  
**RPO**: Recovery Point Objective  
**S3**: Simple Storage Service  
**SMS**: Short Message Service  
**SRS**: Software Requirements Specification  
**SSL**: Secure Sockets Layer  
**STT**: Speech-to-Text  
**TC**: Test Case  
**TLS**: Transport Layer Security  
**TTS**: Text-to-Speech  
**UI**: User Interface  
**UX**: User Experience  
**WAF**: Web Application Firewall  
**WCAG**: Web Content Accessibility Guidelines

---

## Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Product Owner | [Name] | _________ | ______ |
| Technical Lead | [Name] | _________ | ______ |
| QA Lead | [Name] | _________ | ______ |
| Stakeholder Representative | [Name] | _________ | ______ |

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-02-15 | Pragya Shiksha Team | Initial draft for AWS AI for Bharat Hackathon |

---

**End of Document**
