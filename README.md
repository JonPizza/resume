# 📄 Auto-Building Resume with YAMLResume

**Transform your YAML resume into a beautiful PDF automatically with every update!**

This repository provides a complete CI/CD pipeline that automatically generates a professional PDF resume whenever you update your YAML file. No more manual builds, no more forgetting to update your resume - just push your changes and get a fresh PDF instantly.

## ✨ Features

- 🚀 **Automatic PDF Generation** - Updates your resume PDF on every YAML change
- 📦 **Zero Configuration** - Works out of the box with GitHub Actions
- 🎨 **Professional Formatting** - Uses YAMLResume's clean, ATS-friendly templates
- 📱 **Always Up-to-Date** - Never worry about having an outdated resume again
- 🌐 **Optional Public Hosting** - Serve your resume PDF via GitHub Pages
- 💾 **Version History** - Full git history of all your resume changes

## 🚀 Quick Start

### 1. Use This Template

Click the "Use this template" button or:

```bash
git clone https://github.com/JonPizza/resume.git
cd resume
```

### 2. Edit Your Resume

Open `resume.yml` and add your information:

```yaml
person:
  name: "John Doe"
  email: "john.doe@email.com"
  phone: "+1 (555) 123-4567"
  location: "San Francisco, CA"
  website: "https://johndoe.com"
  linkedin: "https://linkedin.com/in/johndoe"
  github: "https://github.com/johndoe"

summary: |
  Experienced software engineer with 5+ years building scalable web applications.
  Passionate about clean code, user experience, and continuous learning.

experience:
  - company: "Tech Company Inc."
    position: "Senior Software Engineer"
    startDate: "2021-03"
    endDate: "Present"
    location: "San Francisco, CA"
    highlights:
      - "Led development of microservices architecture serving 1M+ users"
      - "Reduced API response times by 40% through optimization"
      - "Mentored 3 junior developers and established code review processes"
```

### 3. Push and Watch the Magic

```bash
git add resume.yml
git commit -m "Update my resume"
git push
```

🎉 **That's it!** GitHub Actions will automatically build your PDF and commit it to the repository.

## 📁 Repository Structure

```
├── .github/workflows/
│   └── build-resume.yml      # CI/CD pipeline
├── resume.yml                # Your resume data (edit this!)
├── output/
│   └── resume.pdf           # Auto-generated PDF
├── README.md
└── examples/
    └── sample-resume.yml    # Example resume for reference
```

## 🛠 How It Works

1. **Edit** your `resume.yml` file with your information
2. **Commit & Push** your changes to GitHub
3. **GitHub Actions** detects the change and triggers the workflow
4. **YAMLResume** builds a beautiful PDF from your YAML
5. **PDF is committed** back to your repository automatically
6. **Download** your fresh resume from the `output/` folder

## 📋 Resume YAML Structure

Your `resume.yml` should follow this structure:

```yaml
person:
  name: "Your Name"
  email: "your.email@example.com"
  phone: "+1 (555) 123-4567"
  location: "City, State"
  website: "https://yourwebsite.com"
  linkedin: "linkedin.com/in/yourprofile"
  github: "github.com/yourusername"

summary: |
  Your professional summary here.

experience:
  - company: "Company Name"
    position: "Job Title"
    startDate: "YYYY-MM"
    endDate: "Present" # or "YYYY-MM"
    location: "City, State"
    highlights:
      - "Achievement 1"
      - "Achievement 2"

education:
  - institution: "University Name"
    degree: "Degree Name"
    startDate: "YYYY-MM"
    endDate: "YYYY-MM"
    gpa: "3.8" # optional

skills:
  - category: "Programming"
    items: ["Python", "JavaScript", "Java"]
  - category: "Tools"
    items: ["Docker", "AWS", "Git"]

projects:
  - name: "Project Name"
    description: "Brief description"
    technologies: ["Tech1", "Tech2"]
    url: "https://github.com/you/project"
```

## 🎯 Usage Examples

### Update Your Experience
```bash
# Edit resume.yml - add new job experience
git add resume.yml
git commit -m "Add new position at Amazing Corp"
git push
# ✅ New PDF will be generated automatically
```

### Manual Build Trigger
1. Go to the **Actions** tab in your repository
2. Click on **"Build Resume"**
3. Click **"Run workflow"** → **"Run workflow"**

### Download Your Resume
- **From GitHub**: Navigate to `output/resume.pdf` in your repository
- **From Actions**: Download from the latest workflow run artifacts
- **Public URL** (if GitHub Pages enabled): `https://yourusername.github.io/yourrepo/output/resume.pdf`

## 🌐 Enable Public Access (Optional)

To make your resume publicly accessible:

1. Go to **Settings** → **Pages**
2. Set **Source** to "Deploy from a branch"
3. Select **main** branch and **/ (root)** folder
4. Your resume will be available at:
   ```
   https://yourusername.github.io/repository-name/output/resume.pdf
   ```

## 🔧 Customization

### Multiple Resume Versions
Create different YAML files for different purposes:
```
resume-tech.yml       # Technical positions
resume-marketing.yml  # Marketing roles
resume-academic.yml   # Academic positions
```

Then modify the workflow to build multiple versions:
```yaml
- name: Build all resume versions
  run: |
    for resume in *.yml; do
      docker run --rm -v $(pwd):/home/yamlresume yamlresume/yamlresume build "$resume"
    done
```

### Custom Themes
Modify the build command to use different themes:
```yaml
docker run --rm -v $(pwd):/home/yamlresume yamlresume/yamlresume build resume.yml --theme=modern
```

## 🐛 Troubleshooting

### Build Fails
- Check the **Actions** tab for error details
- Ensure your YAML is valid (use a YAML validator)
- Verify all required fields are present

### PDF Not Generated
- Make sure you're pushing changes to `resume.yml`
- Check that the workflow file is in `.github/workflows/`
- Verify the workflow has permission to commit (should work by default)

### Local Testing
Test your resume locally before pushing:
```bash
# Using Docker
docker run --rm -v $(pwd):/home/yamlresume yamlresume/yamlresume build resume.yml

# Using npm (if you have Node.js)
npm install -g yamlresume
yamlresume build resume.yml
```

## 📚 Resources

- [YAMLResume Documentation](https://github.com/yamlresume/yamlresume)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [YAML Syntax Guide](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)

## 🤝 Contributing

Found a bug or want to improve the workflow? 

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## ⭐ Show Your Support

If this helped you automate your resume building, give it a star! ⭐

---

**Made with ❤️ for developers who want to focus on content, not formatting.**