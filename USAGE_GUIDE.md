# Usage Guide

## Quick Start

### 1. Opening the Cheatsheet
```bash
# Simply open the HTML file in any web browser
open index.html
# or
start index.html
# or double-click the file
```

### 2. Basic Navigation
- **View Tags**: Scroll through the table to see all HTML tags
- **Search**: Use browser search (Ctrl+F / Cmd+F) to find specific tags
- **Print**: Use browser print function (Ctrl+P / Cmd+P) to print the cheatsheet

## Adding New HTML Tags

### Step-by-Step Process

#### 1. Open the HTML File
```bash
# Open index.html in your preferred text editor
code index.html
# or
nano index.html
# or
vim index.html
```

#### 2. Locate the Table Body
Find the `<tbody>` section in the HTML file:
```html
<tbody>
    <!-- Existing rows are here -->
</tbody>
```

#### 3. Add a New Row
Insert a new table row with this structure:
```html
<tr>
    <td class="code">&lt;your-tag&gt;</td>
    <td>Your Tag Name</td>
    <td>Description of what this tag does.</td>
</tr>
```

#### 4. Example: Adding a `<div>` Tag
```html
<tr>
    <td class="code">&lt;div&gt;</td>
    <td>Division</td>
    <td>Creates a block-level container for grouping elements.</td>
</tr>
```

#### 5. Example: Adding a `<span>` Tag
```html
<tr>
    <td class="code">&lt;span&gt;</td>
    <td>Span</td>
    <td>Creates an inline container for grouping text or elements.</td>
</tr>
```

### Best Practices for Adding Tags

#### 1. Tag Formatting
- Always use the `.code` class for the first column
- Include angle brackets in the tag display: `&lt;tag&gt;`
- Use lowercase for tag names

#### 2. Description Guidelines
- Keep descriptions concise but informative
- Explain the primary purpose of the tag
- Include common use cases when helpful

#### 3. Examples of Good Descriptions
```html
<!-- Good: Clear and concise -->
<td>Creates a paragraph of text with proper spacing.</td>

<!-- Good: Includes use case -->
<td>Creates a clickable link to another page or resource.</td>

<!-- Good: Explains behavior -->
<td>Creates a line break without starting a new paragraph.</td>
```

## Customizing the Appearance

### 1. Changing Colors

#### Background Color
Edit `styles.css`:
```css
body {
    background-color: #f0f0f0; /* Light gray */
    /* or */
    background-color: #ffffff; /* White */
    /* or */
    background-color: #2d2d2d; /* Dark theme */
}
```

#### Code Element Background
```css
.code {
    background-color: #e8f5e8; /* Light green */
    /* or */
    background-color: #fff3cd; /* Light yellow */
    /* or */
    background-color: #d1ecf1; /* Light blue */
}
```

#### Table Header Color
```css
th {
    background-color: #f8f9fa; /* Light gray background */
    color: #495057; /* Dark gray text */
}
```

### 2. Changing Fonts

#### Main Font
```css
body {
    font-family: 'Arial', sans-serif;
    /* or */
    font-family: 'Georgia', serif;
    /* or */
    font-family: 'Courier New', monospace;
}
```

#### Header Font
```css
h1 {
    font-family: 'Roboto', sans-serif;
    /* or */
    font-family: 'Open Sans', sans-serif;
}
```

#### Code Font
```css
.code {
    font-family: 'Consolas', monospace;
    /* or */
    font-family: 'Source Code Pro', monospace;
}
```

### 3. Adding Google Fonts

#### 1. Choose a Font
Visit [Google Fonts](https://fonts.google.com/) and select a font.

#### 2. Update the HTML
Replace the existing Google Fonts link in `<head>`:
```html
<link href="https://fonts.googleapis.com/css2?family=YourFont:wght@400;600&display=swap" rel="stylesheet">
```

#### 3. Update CSS
```css
th {
    font-family: 'YourFont', sans-serif;
}
```

### 4. Responsive Design

#### Add Mobile Support
```css
/* Add to styles.css */
@media (max-width: 768px) {
    body {
        padding: 10px;
    }
    
    table {
        font-size: 14px;
    }
    
    th, td {
        padding: 8px 4px;
    }
}
```

#### Add Print Styles
```css
@media print {
    body {
        background-color: white;
    }
    
    .code {
        background-color: #f0f0f0;
        border: 1px solid #ccc;
    }
}
```

## Advanced Customization

### 1. Adding Categories

#### Create Category Columns
Add a new column to the table:
```html
<thead>
    <tr>
        <th>Tag</th>
        <th>Name</th>
        <th>Category</th>
        <th>Use</th>
    </tr>
</thead>
```

#### Add Category Data
```html
<tr>
    <td class="code">&lt;p&gt;</td>
    <td>Paragraph</td>
    <td>Text</td>
    <td>Creates a paragraph of text.</td>
</tr>
```

### 2. Adding Examples

#### Create an Examples Column
```html
<thead>
    <tr>
        <th>Tag</th>
        <th>Name</th>
        <th>Use</th>
        <th>Example</th>
    </tr>
</thead>
```

#### Add Example Data
```html
<tr>
    <td class="code">&lt;a&gt;</td>
    <td>Anchor</td>
    <td>Creates a hyperlink.</td>
    <td>&lt;a href="https://example.com"&gt;Link&lt;/a&gt;</td>
</tr>
```

### 3. Adding Interactive Features

#### Search Functionality
Add this JavaScript to make the cheatsheet searchable:
```html
<script>
function searchTable() {
    const input = document.getElementById('searchInput');
    const filter = input.value.toLowerCase();
    const table = document.querySelector('table');
    const rows = table.getElementsByTagName('tr');

    for (let i = 1; i < rows.length; i++) {
        const row = rows[i];
        const cells = row.getElementsByTagName('td');
        let found = false;
        
        for (let j = 0; j < cells.length; j++) {
            const cell = cells[j];
            if (cell.textContent.toLowerCase().indexOf(filter) > -1) {
                found = true;
                break;
            }
        }
        
        row.style.display = found ? '' : 'none';
    }
}
</script>
```

#### Add Search Input
```html
<div style="margin: 20px 0;">
    <input type="text" id="searchInput" placeholder="Search tags..." 
           onkeyup="searchTable()" style="padding: 8px; width: 200px;">
</div>
```

## Troubleshooting

### Common Issues

#### 1. Fonts Not Loading
**Problem**: Google Fonts not displaying correctly
**Solution**: 
- Check internet connection
- Verify the Google Fonts URL is correct
- Add fallback fonts in CSS

#### 2. Table Not Styled
**Problem**: CSS styles not applying
**Solution**:
- Check that `styles.css` is in the same directory as `index.html`
- Verify the CSS file path in the HTML link tag
- Clear browser cache

#### 3. Code Elements Not Highlighted
**Problem**: Tag syntax not showing green background
**Solution**:
- Ensure the `<td>` element has the `class="code"` attribute
- Check that the CSS `.code` rule is properly defined
- Verify no conflicting CSS rules

### Debugging Tips

#### 1. Browser Developer Tools
- **Chrome/Edge**: F12 or Ctrl+Shift+I
- **Firefox**: F12 or Ctrl+Shift+I
- **Safari**: Cmd+Option+I

#### 2. Check Console for Errors
Look for JavaScript errors or missing resource warnings.

#### 3. Inspect Elements
Right-click on elements to inspect their HTML and CSS.

## Performance Optimization

### 1. Font Loading
```html
<!-- Add font-display for better performance -->
<link href="https://fonts.googleapis.com/css2?family=Exo:ital,wght@1,600&display=swap&display=swap" rel="stylesheet">
```

### 2. CSS Optimization
```css
/* Use efficient selectors */
th { /* Good */
    font-family: 'Exo';
}

table th { /* Less efficient */
    font-family: 'Exo';
}
```

### 3. HTML Optimization
```html
<!-- Remove unnecessary whitespace -->
<tr><td class="code">&lt;p&gt;</td><td>Paragraph</td><td>Creates a paragraph.</td></tr>
```

## Version Control

### Git Setup
```bash
# Initialize git repository
git init

# Add files
git add index.html styles.css README.md

# Initial commit
git commit -m "Initial HTML cheatsheet"

# Create .gitignore
echo "*.log" > .gitignore
echo ".DS_Store" >> .gitignore
```

### Commit Guidelines
- Use descriptive commit messages
- Commit related changes together
- Test changes before committing

## Deployment

### Local Testing
```bash
# Start a simple HTTP server
python -m http.server 8000
# or
npx serve .

# Open in browser
open http://localhost:8000
```

### GitHub Pages
1. Push to GitHub repository
2. Enable GitHub Pages in repository settings
3. Select source branch (usually `main`)
4. Access via `https://username.github.io/repository-name`

### Netlify
1. Connect GitHub repository to Netlify
2. Set build command: (leave empty for static site)
3. Set publish directory: `.`
4. Deploy automatically on push

## Maintenance

### Regular Tasks
1. **Update Tags**: Add new HTML5 tags as they become standard
2. **Review Descriptions**: Ensure accuracy and clarity
3. **Test Compatibility**: Check in different browsers
4. **Performance**: Monitor loading times

### Backup Strategy
```bash
# Create backup
cp index.html index.html.backup
cp styles.css styles.css.backup

# Or use git
git tag v1.0.0
```

## Contributing

### How to Contribute
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Contribution Guidelines
- Follow existing code style
- Add descriptive commit messages
- Test changes in multiple browsers
- Update documentation if needed

## Support

### Getting Help
- Check the troubleshooting section above
- Review browser console for errors
- Test in different browsers
- Validate HTML and CSS

### Resources
- [MDN Web Docs](https://developer.mozilla.org/)
- [W3Schools HTML Reference](https://www.w3schools.com/tags/)
- [HTML5 Specification](https://html.spec.whatwg.org/)