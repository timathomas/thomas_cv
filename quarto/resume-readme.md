# Quarto Two-Column Resume Template

A clean, professional two-column resume template for Quarto using Typst, inspired by modern minimalist design.

## Features

✅ **Two-column layout** - Left column (60%) for experience, right column (40%) for skills/education  
✅ **Clean, minimalist design** - Professional appearance with simple lines and spacing  
✅ **Fully customizable** - Easy-to-edit sections with clear instructions  
✅ **Multi-page support** - Automatically handles overflow to page 2  
✅ **Typst-powered** - Fast rendering with beautiful typography  
✅ **No external dependencies** - Pure Quarto + Typst solution

## Requirements

- Quarto (version 1.4 or higher)
- Typst is included with Quarto, no separate installation needed

## Quick Start

### 1. Installation

Download the `two-column-resume.qmd` file to your computer.

### 2. Customize Your Resume

Open `two-column-resume.qmd` in your favorite text editor (RStudio, VS Code, or any text editor).

Edit the header section with your personal information:

```typst
#resume_header(
  "YOUR NAME",                       // Your full name
  "Your Job Title",                  // Your job title
  "your.email@gmail.com",           // Your email
  "123-456-7890",                   // Your phone
  "Your Address",                    // Your address
  "linkedin.com/in/yourprofile"     // Your LinkedIn
)
```

### 3. Update Content Sections

#### Professional Profile
Replace the Lorem ipsum text with your professional summary.

#### Experience
Use the `experience_entry()` function for each job:

```typst
#experience_entry(
  "Senior Data Analyst",            // Job title
  "Company Name",                    // Company
  "Jan 2020 - Present",             // Date range
  (                                  // Bullet points
    "Led data-driven initiatives that increased efficiency by 25%",
    "Developed R packages for internal analysis workflows",
    "Mentored junior analysts on statistical methods"
  )
)
```

#### Skills
Add or remove skills:

```typst
#skill_item("R Programming")
#skill_item("Python")
#skill_item("Data Visualization")
#skill_item("Statistical Analysis")
```

#### Education
Update education entries:

```typst
#education_entry(
  "Master of Science in Statistics",  // Degree
  "University Name",                   // University
  "City, State",                       // Location
  "2018 - 2020"                       // Date range
)
```

### 4. Render Your Resume

#### Option 1: Command Line
```bash
quarto render two-column-resume.qmd
```

#### Option 2: RStudio
Open the file in RStudio and click the "Render" button.

#### Option 3: VS Code
If you have the Quarto extension installed, use `Cmd/Ctrl + Shift + K` to render.

The output will be a PDF file: `two-column-resume.pdf`

## Customization Guide

### Adjusting Column Widths

Change the column ratio in the `grid()` function:

```typst
#grid(
  columns: (65%, 35%),    // Left column 65%, right column 35%
  column-gutter: 1.5em,
  ...
)
```

### Changing Font

Replace "Arial" in the document settings:

```typst
#set text(font: "Helvetica", size: 10pt, fill: black)
```

Available fonts typically include: Arial, Helvetica, Times New Roman, Georgia, Courier

### Adjusting Spacing

Modify vertical spacing values:

```typst
#v(0.5em)  // Smaller spacing
#v(1.0em)  // Larger spacing
```

### Changing Line Thickness

Adjust line stroke in section headers:

```typst
#line(length: 100%, stroke: 1pt + black)  // Thicker line
#line(length: 100%, stroke: 0.3pt + black)  // Thinner line
```

### Adding/Removing Pages

To add a third page, copy the grid structure after the second `#pagebreak()`:

```typst
#pagebreak()

#grid(
  columns: (60%, 40%),
  column-gutter: 1.5em,
  
  [
    // Left column content
  ],
  
  [
    // Right column content
  ]
)
```

## Template Structure

```
Resume Header
├── Name (large, uppercase)
├── Title (uppercase)
└── Contact Information (2-column grid)

Page 1
├── Left Column (60%)
│   ├── Professional Profile
│   └── Experience (3-4 entries)
└── Right Column (40%)
    ├── Skills (8-10 items)
    ├── Education (2-4 entries)
    └── Certifications (2-3 entries)

Page 2
├── Left Column (60%)
│   ├── Experience (continued)
│   └── References (2 entries)
└── Right Column (40%)
    ├── Skills (continued)
    └── Extras
```

## Function Reference

### `resume_header(name, title, email, phone, address, linkedin)`
Creates the header section with contact information.

### `section_header(title)`
Creates a section header with an underline.

### `experience_entry(title, company, date, items)`
Creates a work experience entry with bullet points.
- `items` should be a tuple/array of strings

### `education_entry(degree, university, location, date)`
Creates an education entry.

### `certification_entry(cert_name, university, location)`
Creates a certification entry.

### `skill_item(skill)`
Creates a single skill bullet point.

### `reference_entry(name, position, company, phone, email)`
Creates a reference entry with contact information.

## Tips for Best Results

### Content Tips
- Keep bullet points concise (1-2 lines maximum)
- Use action verbs: "Led," "Developed," "Implemented"
- Quantify achievements when possible: "Increased by 25%"
- Tailor content to the specific job you're applying for

### Design Tips
- Maintain consistent spacing throughout
- Don't overcrowd - white space is important
- Keep font sizes consistent within sections
- Test print before sending - ensure everything fits nicely

### Layout Tips
- Put your most important/recent experience first
- Balance content between columns
- If one column is much longer, adjust the column ratio
- Consider removing less relevant older experience

## Troubleshooting

### Issue: Resume doesn't render
**Solution**: Make sure Quarto is installed and updated to version 1.4+
```bash
quarto --version
quarto update
```

### Issue: Font doesn't look right
**Solution**: Try a different font. Not all fonts are available on all systems.

### Issue: Content overflows page
**Solution**: 
1. Reduce font size slightly: `#set text(font: "Arial", size: 9.5pt)`
2. Reduce margins in YAML: `margin: x: 0.5in`
3. Edit content to be more concise

### Issue: Columns are unbalanced
**Solution**: Move content between columns or adjust column ratios

### Issue: Can't see emoji icons in PDF
**Solution**: This is expected on some systems. The template works with or without emoji rendering.

## Examples

### For Academic Positions
Focus more on:
- Publications (add a Publications section)
- Teaching experience
- Research projects
- Academic honors

### For Industry Positions
Focus more on:
- Quantifiable achievements
- Technical skills
- Project outcomes
- Leadership experience

### For Career Changers
Focus more on:
- Transferable skills
- Relevant projects (even if personal/volunteer)
- Clear objective statement
- Continuous learning (certifications, courses)

## Advanced: Creating a Quarto Extension

If you want to use this template across multiple projects, you can create a Quarto extension:

1. Create extension structure:
```bash
quarto create extension format
```

2. Choose "typst" as the base format

3. Copy the Typst code from this template into the generated `typst-template.typ` file

4. Share your extension on GitHub

## Contributing

Feel free to customize this template for your needs! Some ideas:
- Add color scheme support
- Create different column layouts (50/50, 70/30, etc.)
- Add support for portfolio images
- Create single-column variant

## License

This template is provided as-is for personal and commercial use.

## Resources

- [Quarto Documentation](https://quarto.org/)
- [Typst Documentation](https://typst.app/docs/)
- [Quarto Community](https://github.com/quarto-dev/quarto-cli/discussions)

## Questions or Issues?

If you encounter problems or have questions:
1. Check the Troubleshooting section above
2. Review Quarto's Typst documentation
3. Search or ask in the Quarto community discussions

---

**Good luck with your job search!** 🚀
