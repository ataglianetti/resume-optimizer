# Resume Optimizer

AI-powered resume optimization system that tailors your resume to specific job listings using Claude Code.

## Overview

This system helps you create ATS-optimized, keyword-targeted resumes for each job application. Instead of maintaining multiple resume versions manually, you maintain a single source of truth and let Claude Code generate optimized versions based on job descriptions.

## Directory Structure

```
resume-optimizer/
├── .claude-instructions.md  # Resume generation rules (READ THIS FIRST!)
├── source/                  # Your master resume data
│   ├── base-resume.md       # Main resume template
│   ├── skills.md            # Comprehensive skills inventory
│   ├── experience.md        # Detailed work history
│   ├── interview-stories.md # SARO stories for interview prep
│   └── essay-responses.md   # Templates for application essay questions
├── optimized/               # Job-specific optimized resumes (markdown & HTML)
├── templates/               # Formatting templates
│   └── ats-template*.html
└── archive/                 # Interview prep materials
```

**IMPORTANT**: Claude Code follows the rules in `.claude-instructions.md` when generating resumes. If you want to change how resumes are formatted (page length, bullet count, spacing, etc.), edit that file.

## Setup Instructions

### 1. Fill Out Your Source Files

**`source/base-resume.md`**
- Add your personal information (name, contact details, links)
- Write a generic professional summary
- List all relevant experience
- Include education, certifications, and projects

**`source/skills.md`**
- Create a comprehensive inventory of ALL your skills
- Rate your proficiency level for each
- Include technical skills, soft skills, and domain knowledge
- Keep this list exhaustive - you'll never send all of it

**`source/experience.md`**
- Document EVERY achievement and responsibility from each role
- Quantify everything (metrics, percentages, impacts)
- Include full technical stack details
- This is your "master list" that gets selectively pulled from

**`source/essay-responses.md`**
- Add templates for "Why this company/role?" questions
- Document your career goals and motivations
- Describe your work style and cultural fit preferences
- Include company research and product enthusiasm talking points
- This gets used to generate responses for application essay questions

### 2. Optimization Workflow

When you find a job you want to apply for:

1. **Copy the job listing URL**
2. **In Claude Code, provide the URL and say:**
   ```
   "Optimize my resume for this job: [URL]"
   ```

3. **Claude Code will:**
   - Fetch and analyze the job description
   - Extract key requirements, skills, and keywords
   - **Scan for application form essay questions** (if present)
   - Generate a **compact, 1-page** optimized markdown resume emphasizing relevant experience
   - Save it to `optimized/YYYY-MM-DD_[Company]_[Role]_Resume.md`
   - Create an ATS-friendly HTML version at `optimized/YYYY-MM-DD_[Company]_[Role]_Resume.html`
   - **Generate pre-filled essay responses** (if questions were found)
   - Save essay responses to `optimized/YYYY-MM-DD_[Company]_[Role]_Essay_Responses.md`
   - Follow formatting rules from `.claude-instructions.md` (4 bullets per role, generous white space, scannable)

4. **Review and adjust** the optimized version as needed

5. **Export to PDF** (if needed):
   - Open the HTML file in a browser
   - Print to PDF using browser's print function
   - Use default settings for best ATS compatibility

## Best Practices

### Maintaining Your Source Files

- **Update regularly**: Add new skills, projects, and achievements as they happen
- **Be comprehensive**: Include everything in your source files, even if you won't use it all
- **Quantify achievements**: Always include metrics (%, $, time saved, users impacted)
- **Use action verbs**: Led, Architected, Implemented, Optimized, Delivered, etc.

### ATS Optimization Tips

The system follows these ATS-friendly principles:

- **Simple formatting**: No tables, columns, or complex layouts
- **Standard fonts**: Arial, Helvetica, or similar sans-serif
- **Clear section headers**: Experience, Education, Skills (standard names)
- **Keywords**: Mirrors language from job descriptions
- **Chronological order**: Most recent experience first
- **No images or graphics**: Text only
- **Standard file format**: HTML/PDF (not .pages, .docx with complex formatting)

### Resume Length

- **ALL resumes**: 1 page (non-negotiable)
- Focus on quality over quantity
- 4 bullets per role maximum
- Generous white space for scannability

Claude Code will ruthlessly prioritize the most relevant content to fit on one page while maintaining readability.

## Example Usage

```markdown
User: "Optimize my resume for this Senior Software Engineer role at Google: https://careers.google.com/jobs/..."

Claude Code will:
1. Fetch the job description
2. Identify key skills (e.g., Python, distributed systems, leadership)
3. Pull relevant achievements from your experience.md
4. Emphasize matching skills from skills.md
5. Rewrite the professional summary to align with the role
6. Generate optimized resume in both markdown and HTML formats
```

## Output Files

### Optimized Markdown
- Location: `optimized/YYYY-MM-DD_[Company]_[Role]_Resume.md`
- Purpose: Editable version you can review and adjust
- Date-stamped for tracking application timeline
- Obsidian-friendly for easy editing

### ATS-Friendly HTML
- Location: `optimized/YYYY-MM-DD_[Company]_[Role]_Resume.html`
- Purpose: Final formatted version ready for submission
- Compact styling with generous white space
- Can be opened in browser and saved as PDF

### Essay Responses (if applicable)
- Location: `optimized/YYYY-MM-DD_[Company]_[Role]_Essay_Responses.md`
- Purpose: Pre-filled responses to application form essay questions
- Includes word counts for each response
- Ready to copy/paste into application forms
- Common question types:
  - "Why do you want to work here?"
  - "Why are you interested in this role?"
  - "Describe your relevant experience"
  - "Tell us about a time when..." (behavioral questions)
  - "What makes you a good fit for this position?"

## Tips for Success

1. **Be honest**: Only include skills and experience you actually have
2. **Stay current**: Update your source files monthly
3. **Customize further**: Use Claude Code's output as a starting point, then refine
4. **Track applications**: Keep notes in the optimized markdown files about application status
5. **A/B test**: Try different approaches and track which get responses

## System Customization

### To Change Resume Format
Edit `.claude-instructions.md` to adjust:
- Page length requirements
- Bullet point limits per role
- Spacing and white space rules
- Font sizes and styling
- File naming conventions

### Per-Resume Customizations
Ask Claude Code to:
- "Make this resume more technical/managerial/leadership-focused"
- "Emphasize my experience with [specific technology]"
- "Add more metrics and quantifiable achievements"
- "Adjust the tone to be more [formal/casual/innovative]"

### Essay Response Features
The system automatically:
- **Scans job application pages** for essay questions and text input fields
- **Generates tailored responses** using your source/essay-responses.md templates
- **Adapts tone and content** based on question type:
  - Motivation questions → Uses "Why This Company" section
  - Behavioral questions → Condenses stories from interview-stories.md
  - Skills questions → Pulls from experience.md
  - Cultural fit → Uses "Work Style" section
- **Respects character limits** and provides word counts
- **Includes specific examples** from your experience (not generic template text)

## Troubleshooting

**"My resume is too long"**
- This shouldn't happen anymore! Check `.claude-instructions.md` is being followed
- If it's still too long, reduce bullets per role in the instructions file
- Make sure bullets are concise (1-1.5 lines each)

**"ATS systems aren't parsing my resume correctly"**
- Stick to standard section headers
- Avoid complex formatting
- Use the HTML template provided (it's tested for ATS compatibility)
- Submit as PDF (not Word doc) after printing from HTML

**"I need to emphasize different skills"**
- Update your skills.md with proficiency levels
- Tell Claude Code which skills to prioritize
- Ask for specific industry or role focus

**"The application doesn't have essay questions"**
- No problem! Claude Code will only generate essay responses if it detects questions
- You'll still get the optimized resume and HTML as usual

**"I want to customize an essay response"**
- Edit the generated YYYY-MM-DD_Company_Role_Essay_Responses.md file
- Or update source/essay-responses.md to improve future responses
- Ask Claude Code to "regenerate essay responses with more focus on [X]"

**"Essay responses are too long/short"**
- Check if the application specifies character/word limits
- Tell Claude Code: "Shorten the essay responses to ~200 words each"
- Or: "Expand the responses to use the full 500 character limit"

---

**Ready to get started?** Fill out your source files, then paste a job URL to Claude Code and watch the magic happen!
