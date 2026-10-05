# CodeMentor Web - Java Static Analysis

A resume-ready web application that analyzes Java source code and reports common code-quality issues, cyclomatic complexity, algorithm patterns, estimated time complexity and an overall quality score.

## Technology
- Java 25
- Spring Boot 4.1.1
- Spring MVC/Web
- HTML5, CSS3, JavaScript
- Maven

Spring Boot 4.1.1 is the current stable line used by this project. It supports Java 25. See the official Spring Boot documentation for system requirements.

## Features
- Paste Java code into the browser
- Upload a `.java` file
- Detect assignment inside `if` conditions
- Detect empty catch blocks
- Detect direct console output
- Detect long lines
- Detect nested-loop performance risks
- Estimate cyclomatic complexity
- Recognize basic sorting, binary-search and loop patterns
- Estimate time complexity
- Generate a 0-100 quality score and grade
- Show line numbers, severity and suggestions
- Download a text report
- Health endpoint at `/api/health`

## Run on Windows
Open Command Prompt in this folder:

```cmd
mvn clean package
mvn spring-boot:run
```

Then open:

```text
http://localhost:8080
```

Alternatively, after packaging:

```cmd
java -jar target\codementor-web-1.0.0.jar
```

## API
### Analyze pasted code
`POST /api/analyze`

JSON:
```json
{"code":"public class Test {}"}
```

### Analyze uploaded file
`POST /api/analyze-file`
Multipart field: `file`

### Health
`GET /api/health`

## Architecture
Browser UI -> REST Controller -> Analyzer Service -> Analysis Result -> Browser Report.

The analyzer is intentionally dependency-light and uses Java regex/pattern analysis for the first web version. A future version can use an AST parser such as JavaParser for more precise syntax-aware analysis.

## Future upgrades
- AST-based analysis
- Login and analysis history
- MySQL/PostgreSQL persistence
- GitHub repository analysis
- PDF report export
- More DSA complexity detection
- Dashboard charts
- SonarQube-style rule configuration
