# DSA Training Application - Architecture & Implementation Guide

**Goal:** Start as personal learning tool (Phase 1), scale to public platform (Phase 2)

**Core Features:**
- User accounts & authentication
- Progress tracking across devices
- Leaderboards & social features
- Admin panel to manage problems

---

## Tech Stack

### Backend:
- Spring Boot 3.2+ (Java 17+)
- Spring Security + JWT (authentication)
- Spring Data JPA (database ORM)
- PostgreSQL (production database)
- H2 (development/testing)

### Frontend:
- HTML/CSS/JavaScript (start simple)
- Later: React/Vue (when you need more interactivity)

### DevOps:
- GitHub (code + problem storage)
- Railway/Render (backend hosting)
- Vercel/Netlify (frontend hosting)
- PostgreSQL on Railway/Supabase

---

## Phase 1: MVP (Personal Learning Tool - 2-3 weeks)

### Features:
- User registration/login
- Browse problems by topic
- Mark problems as complete
- Basic progress tracking
- Pull problem content from GitHub

### Database Schema (PostgreSQL):

```sql
-- Users table
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Problems table
CREATE TABLE problems (
    id BIGSERIAL PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    slug VARCHAR(200) UNIQUE NOT NULL,
    topic VARCHAR(50) NOT NULL, -- arrays, strings, hash-maps, sliding-window
    difficulty VARCHAR(20) NOT NULL, -- easy, medium, hard
    description TEXT,
    github_path VARCHAR(500),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- User progress table
CREATE TABLE user_progress (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT REFERENCES users(id),
    problem_id BIGINT REFERENCES problems(id),
    status VARCHAR(20) DEFAULT 'not_started', -- not_started, in_progress, completed
    completed_at TIMESTAMP,
    attempts INT DEFAULT 0,
    UNIQUE(user_id, problem_id)
);
```

### Backend Structure:

```
dsa-training-backend/
├── src/main/java/com/yourname/dsatraining/
│   ├── DsaTrainingApplication.java
│   ├── config/
│   │   ├── SecurityConfig.java
│   │   └── JwtConfig.java
│   ├── controller/
│   │   ├── AuthController.java
│   │   ├── ProblemController.java
│   │   ├── ProgressController.java
│   │   └── UserController.java
│   ├── model/
│   │   ├── User.java
│   │   ├── Problem.java
│   │   └── UserProgress.java
│   ├── repository/
│   │   ├── UserRepository.java
│   │   ├── ProblemRepository.java
│   │   └── UserProgressRepository.java
│   ├── service/
│   │   ├── AuthService.java
│   │   ├── ProblemService.java
│   │   ├── ProgressService.java
│   │   └── GitHubService.java
│   ├── dto/
│   │   ├── LoginRequest.java
│   │   ├── RegisterRequest.java
│   │   ├── ProblemResponse.java
│   │   └── ProgressResponse.java
│   └── security/
│       ├── JwtTokenProvider.java
│       └── JwtAuthenticationFilter.java
├── src/main/resources/
│   ├── application.yml
│   └── application-dev.yml
└── pom.xml
```

### Key API Endpoints (Phase 1):

```java
// Authentication
POST   /api/auth/register
POST   /api/auth/login
GET    /api/auth/me

// Problems
GET    /api/problems              // List all problems
GET    /api/problems/{id}         // Get specific problem
GET    /api/problems/topic/{topic}  // Filter by topic
GET    /api/problems/random       // Random problem
GET    /api/problems/daily        // Daily challenge

// Progress
POST   /api/progress/{problemId}/start     // Mark as started
POST   /api/progress/{problemId}/complete  // Mark as completed
GET    /api/progress/user                  // Current user's progress
GET    /api/progress/stats                 // User statistics
```

### Frontend Structure:

```
dsa-training-frontend/
├── index.html
├── css/
│   ├── styles.css
│   └── dashboard.css
├── js/
│   ├── app.js
│   ├── auth.js
│   ├── api.js
│   ├── problems.js
│   └── dashboard.js
└── pages/
    ├── login.html
    ├── register.html
    ├── dashboard.html
    ├── problems.html
    └── problem-detail.html
```

---

## Phase 2: Public Platform (Add these features)

### Additional Features:
- Leaderboards
- Social features (friends, activity feed)
- Admin panel
- Comments/discussions per problem
- Submission history
- Streak tracking
- Achievements/badges

### Additional Database Tables:

```sql
-- Leaderboard/Rankings
CREATE TABLE leaderboard (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT REFERENCES users(id),
    total_solved INT DEFAULT 0,
    easy_solved INT DEFAULT 0,
    medium_solved INT DEFAULT 0,
    hard_solved INT DEFAULT 0,
    current_streak INT DEFAULT 0,
    longest_streak INT DEFAULT 0,
    last_solved_at TIMESTAMP,
    UNIQUE(user_id)
);

-- User roles (admin panel)
CREATE TABLE roles (
    id SERIAL PRIMARY KEY,
    name VARCHAR(20) UNIQUE NOT NULL -- USER, ADMIN, MODERATOR
);

CREATE TABLE user_roles (
    user_id BIGINT REFERENCES users(id),
    role_id INT REFERENCES roles(id),
    PRIMARY KEY(user_id, role_id)
);

-- Submissions (optional - if you want to store code)
CREATE TABLE submissions (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT REFERENCES users(id),
    problem_id BIGINT REFERENCES problems(id),
    code TEXT,
    language VARCHAR(20),
    status VARCHAR(20), -- passed, failed
    submitted_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Daily challenges
CREATE TABLE daily_challenges (
    id BIGSERIAL PRIMARY KEY,
    problem_id BIGINT REFERENCES problems(id),
    challenge_date DATE UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Additional API Endpoints (Phase 2):

```java
// Leaderboard
GET    /api/leaderboard              // Top 100 users
GET    /api/leaderboard/topic/{topic}  // By specific topic
GET    /api/users/{userId}/rank      // Specific user rank

// Admin Panel
POST   /api/admin/problems           // Create problem
PUT    /api/admin/problems/{id}      // Update problem
DELETE /api/admin/problems/{id}      // Delete problem
GET    /api/admin/users              // List all users
POST   /api/admin/daily-challenge    // Set daily challenge

// Social Features
GET    /api/users/{userId}/profile   // User profile
GET    /api/activity/feed            // Recent activity
POST   /api/problems/{id}/comments   // Add comment
GET    /api/problems/{id}/comments   // Get comments
```

---

## Sample Code: Key Components

### 1. User Entity (model/User.java):

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(unique = true, nullable = false)
    private String username;

    @Column(unique = true, nullable = false)
    private String email;

    @Column(nullable = false)
    private String passwordHash;

    @CreatedDate
    private LocalDateTime createdAt;

    @ManyToMany(fetch = FetchType.EAGER)
    @JoinTable(name = "user_roles",
        joinColumns = @JoinColumn(name = "user_id"),
        inverseJoinColumns = @JoinColumn(name = "role_id"))
    private Set<Role> roles = new HashSet<>();

    // Getters, setters, constructors
}
```

### 2. Problem Controller (controller/ProblemController.java):

```java
@RestController
@RequestMapping("/api/problems")
public class ProblemController {

    @Autowired
    private ProblemService problemService;

    @GetMapping
    public ResponseEntity<List<ProblemResponse>> getAllProblems(
            @RequestParam(required = false) String topic,
            @RequestParam(required = false) String difficulty) {
        return ResponseEntity.ok(problemService.getAllProblems(topic, difficulty));
    }

    @GetMapping("/{id}")
    public ResponseEntity<ProblemResponse> getProblem(@PathVariable Long id) {
        return ResponseEntity.ok(problemService.getProblemById(id));
    }

    @GetMapping("/random")
    public ResponseEntity<ProblemResponse> getRandomProblem(
            @RequestParam(required = false) String topic) {
        return ResponseEntity.ok(problemService.getRandomProblem(topic));
    }

    @GetMapping("/daily")
    public ResponseEntity<ProblemResponse> getDailyChallenge() {
        return ResponseEntity.ok(problemService.getDailyChallenge());
    }
}
```

### 3. Progress Service (service/ProgressService.java):

```java
@Service
public class ProgressService {

    @Autowired
    private UserProgressRepository progressRepository;

    @Autowired
    private LeaderboardRepository leaderboardRepository;

    @Transactional
    public void markAsCompleted(Long userId, Long problemId) {
        UserProgress progress = progressRepository
            .findByUserIdAndProblemId(userId, problemId)
            .orElse(new UserProgress(userId, problemId));

        progress.setStatus("completed");
        progress.setCompletedAt(LocalDateTime.now());
        progressRepository.save(progress);

        // Update leaderboard
        updateLeaderboard(userId);
    }

    private void updateLeaderboard(Long userId) {
        int totalSolved = progressRepository.countByUserIdAndStatus(userId, "completed");

        Leaderboard leaderboard = leaderboardRepository
            .findByUserId(userId)
            .orElse(new Leaderboard(userId));

        leaderboard.setTotalSolved(totalSolved);
        leaderboard.setLastSolvedAt(LocalDateTime.now());
        leaderboard.updateStreak();

        leaderboardRepository.save(leaderboard);
    }
}
```

### 4. Security Config (config/SecurityConfig.java):

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .cors().and()
            .authorizeHttpRequests()
                .requestMatchers("/api/auth/**").permitAll()
                .requestMatchers("/api/problems/**").authenticated()
                .requestMatchers("/api/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            .and()
            .sessionManagement()
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS);

        http.addFilterBefore(jwtAuthenticationFilter(),
                             UsernamePasswordAuthenticationFilter.class);

        return http.build();
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

---

## GitHub Repository Structure

```
dsa-training-problems/
├── problems/
│   ├── arrays/
│   │   ├── two-sum/
│   │   │   ├── README.md
│   │   │   ├── template.py
│   │   │   ├── template.java
│   │   │   ├── template.js
│   │   │   └── tests/
│   │   │       ├── test_solution.py
│   │   │       └── SolutionTest.java
│   │   └── best-time-to-buy-stock/
│   ├── strings/
│   ├── hash-maps/
│   └── sliding-window/
└── problems.json  // Metadata for backend to parse
```

### problems.json:
```json
{
  "problems": [
    {
      "id": 1,
      "title": "Two Sum",
      "slug": "two-sum",
      "topic": "arrays",
      "difficulty": "easy",
      "githubPath": "problems/arrays/two-sum",
      "description": "Given an array of integers...",
      "testCases": 15
    }
  ]
}
```

---

## Development Roadmap

### Week 1-2: Phase 1 MVP
- [ ] Set up Spring Boot project
- [ ] Configure PostgreSQL database
- [ ] Implement User authentication (register/login)
- [ ] Create Problem entity and repository
- [ ] Build Problem API endpoints
- [ ] Create UserProgress tracking
- [ ] Build simple HTML/CSS/JS frontend
- [ ] Test authentication flow
- [ ] Deploy to Railway (backend) + Netlify (frontend)

### Week 3-4: Core Features
- [ ] GitHub API integration (fetch problem content)
- [ ] Daily challenge system
- [ ] User dashboard with progress stats
- [ ] Problem filtering by topic/difficulty
- [ ] Random problem generator
- [ ] Mark problems as complete
- [ ] Basic UI improvements

### Week 5-6: Phase 2 Features
- [ ] Leaderboard implementation
- [ ] Admin panel (CRUD for problems)
- [ ] Streak tracking
- [ ] User profiles
- [ ] Activity feed
- [ ] Comments on problems

### Week 7+: Polish
- [ ] Achievements/badges system
- [ ] Email notifications
- [ ] Search functionality
- [ ] Mobile responsive design
- [ ] Performance optimization
- [ ] Testing & bug fixes

---

## Quick Start Commands

### Backend (Spring Boot):

```bash
# Create project
spring init --dependencies=web,data-jpa,postgresql,security,validation \
  --type=maven-project --language=java --boot-version=3.2.0 \
  dsa-training-backend

cd dsa-training-backend

# Add JWT dependency to pom.xml manually
# <dependency>
#   <groupId>io.jsonwebtoken</groupId>
#   <artifactId>jjwt-api</artifactId>
#   <version>0.12.3</version>
# </dependency>

# Run
./mvnw spring-boot:run
```

### Frontend:

```bash
# Simple static files - just create and open in browser
mkdir dsa-training-frontend
cd dsa-training-frontend
touch index.html
touch styles.css
touch app.js
```

---

## application.yml Configuration

### src/main/resources/application.yml:

```yaml
spring:
  application:
    name: dsa-training-backend

  datasource:
    url: jdbc:postgresql://localhost:5432/dsatraining
    username: ${DB_USERNAME:postgres}
    password: ${DB_PASSWORD:password}
    driver-class-name: org.postgresql.Driver

  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    properties:
      hibernate:
        dialect: org.hibernate.dialect.PostgreSQLDialect
        format_sql: true

jwt:
  secret: ${JWT_SECRET:your-secret-key-change-this-in-production}
  expiration: 86400000  # 24 hours in milliseconds

server:
  port: 8080

logging:
  level:
    com.yourname.dsatraining: DEBUG
    org.springframework.security: DEBUG
```

### src/main/resources/application-dev.yml:

```yaml
spring:
  datasource:
    url: jdbc:h2:mem:testdb
    driver-class-name: org.h2.Driver
  h2:
    console:
      enabled: true
  jpa:
    hibernate:
      ddl-auto: create-drop

server:
  port: 8080
```

---

## pom.xml Dependencies

```xml
<dependencies>
    <!-- Spring Boot Starters -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-security</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>

    <!-- Database -->
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <scope>runtime</scope>
    </dependency>
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>

    <!-- JWT -->
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt-api</artifactId>
        <version>0.12.3</version>
    </dependency>
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt-impl</artifactId>
        <version>0.12.3</version>
        <scope>runtime</scope>
    </dependency>
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt-jackson</artifactId>
        <version>0.12.3</version>
        <scope>runtime</scope>
    </dependency>

    <!-- Lombok (optional but recommended) -->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>

    <!-- Testing -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

---

## Next Steps

1. **Start with Phase 1 MVP** - Get basic auth + problem listing working
2. **Use H2 database first** (easier for development), migrate to PostgreSQL later
3. **Build one feature at a time** - Don't try to build everything at once
4. **Test as you go** - Write unit tests for services
5. **Deploy early** - Get it online ASAP, even if basic

---

## Deployment Options

### Backend Hosting:
- **Railway** - Easy PostgreSQL + Spring Boot deployment
- **Render** - Free tier available, auto-deploy from GitHub
- **Heroku** - Classic option, paid plans
- **AWS Elastic Beanstalk** - More control, more complex

### Frontend Hosting:
- **Vercel** - Best for static sites, fast CDN
- **Netlify** - Easy deploy, good for SPAs
- **GitHub Pages** - Free, simple for static HTML/CSS/JS
- **Cloudflare Pages** - Fast, free tier

### Database Hosting:
- **Railway PostgreSQL** - Integrated with backend
- **Supabase** - Free PostgreSQL with nice UI
- **ElephantSQL** - Managed PostgreSQL
- **Neon** - Serverless PostgreSQL

---

**Last Updated:** 2025-11-20
**Project Status:** Planning Phase
