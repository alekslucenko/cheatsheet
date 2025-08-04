# HTML Cheatsheet Documentation

## Overview

This project is a comprehensive HTML cheatsheet that provides quick reference for HTML tags, their names, and usage. The project consists of a static HTML page with CSS styling for easy navigation and readability.

## Project Structure

```
├── index.html          # Main HTML cheatsheet page
├── styles.css          # CSS styling for the cheatsheet
└── README.md          # This documentation file
```

## Components

### 1. HTML Structure (`index.html`)

#### Header Section
- **Purpose**: Contains the title and author information
- **Elements**:
  - `<header>`: Main header container
  - `<h1>`: Main title "My Codecademy HTML cheatsheet"
  - `<p>`: Author attribution "By: monkeywarehouse"

#### Main Content Section
- **Purpose**: Displays the HTML tag reference table
- **Elements**:
  - `<main>`: Main content container
  - `<section class="table">`: Table section wrapper
  - `<table>`: Data table with HTML tag information

#### Table Structure
- **Headers**: Tag, Name, Use
- **Data Rows**: Individual HTML tags with descriptions
- **Styling**: Uses `.code` class for tag formatting

#### Footer Section
- **Purpose**: Footer area (currently empty, available for future content)

### 2. CSS Styling (`styles.css`)

#### Body Styling
```css
body {
    background-color: rgb(245,245,220);  /* Light beige background */
}
```

#### Table Header Styling
```css
th {
    font-family: 'Exo';           /* Custom Google Font */
    font-weight: 600;             /* Semi-bold weight */
    letter-spacing: 1px;          /* Letter spacing for readability */
}
```

#### Code Element Styling
```css
.code {
    font-family: monospace, serif;  /* Monospace font for code */
    background-color: lightgreen;   /* Light green background */
}
```

## Usage Instructions

### Viewing the Cheatsheet
1. Open `index.html` in any modern web browser
2. The page will display a table of HTML tags with their descriptions
3. Use the browser's search function (Ctrl+F) to find specific tags

### Adding New Tags
To add new HTML tags to the cheatsheet:

1. Open `index.html`
2. Locate the `<tbody>` section
3. Add a new table row with the following structure:
```html
<tr>
  <td class="code">&lt;tag-name&gt;</td>
  <td>Tag Display Name</td>
  <td>Description of what the tag does.</td>
</tr>
```

### Customizing Styles
To modify the appearance:

1. Edit `styles.css` to change colors, fonts, or layout
2. The project uses Google Fonts (Exo) for headers
3. Code elements use monospace font with light green background

## API Documentation (Future Enhancement)

While this is currently a static HTML project, here are suggested APIs that could be added for enhanced functionality:

### Suggested JavaScript APIs

#### 1. Search API
```javascript
// Search functionality for tags
function searchTags(query) {
    // Implementation for filtering table rows
}

// Usage
searchTags('paragraph'); // Returns all rows containing 'paragraph'
```

#### 2. Tag Management API
```javascript
// Add new tag to the cheatsheet
function addTag(tagName, displayName, description) {
    // Implementation for dynamically adding tags
}

// Usage
addTag('div', 'Division', 'Creates a block-level container');
```

#### 3. Export API
```javascript
// Export cheatsheet data
function exportCheatsheet(format) {
    // Implementation for exporting to JSON, CSV, etc.
}

// Usage
exportCheatsheet('json'); // Exports as JSON
exportCheatsheet('csv');  // Exports as CSV
```

#### 4. Filter API
```javascript
// Filter tags by category
function filterByCategory(category) {
    // Implementation for filtering by tag type
}

// Usage
filterByCategory('text');     // Shows only text-related tags
filterByCategory('structure'); // Shows only structural tags
```

## Browser Compatibility

- **Supported Browsers**: Chrome, Firefox, Safari, Edge
- **Minimum Requirements**: HTML5 and CSS3 support
- **Font Requirements**: Internet connection for Google Fonts loading

## Contributing

To contribute to this project:

1. Fork the repository
2. Add new HTML tags to the table
3. Improve CSS styling
4. Submit a pull request

## License

This project is open source and available under the MIT License.

## Version History

- **v1.0.0**: Initial release with basic HTML tag reference
- **Future**: Planned JavaScript enhancements for interactive features

## Contact

For questions or contributions, please contact the project maintainer.