# Component Documentation

## Overview

This document provides detailed documentation for all HTML components, CSS classes, and their usage in the HTML Cheatsheet project. Each component is documented with its purpose, structure, and styling.

## HTML Components

### 1. Document Structure

#### `<html>`
- **Purpose**: Root element of the HTML document
- **Attributes**: None
- **Content**: Contains `<head>` and `<body>` sections
- **Usage**: Standard HTML5 document structure

#### `<head>`
- **Purpose**: Contains metadata and external resources
- **Content**: 
  - Google Fonts preconnect links
  - CSS stylesheet link
- **Usage**: Document head with font and style resources

#### `<body>`
- **Purpose**: Main content container
- **Styling**: Light beige background (`rgb(245,245,220)`)
- **Content**: Header, main, and footer sections
- **Usage**: Contains all visible page content

### 2. Header Section

#### `<header>`
- **Purpose**: Page header containing title and author information
- **Content**: `<h1>` and `<p>` elements
- **Styling**: Inherits body styling
- **Usage**: Top section of the page

#### `<h1>`
- **Purpose**: Main page title
- **Content**: "My Codecademy HTML cheatsheet"
- **Styling**: 
  - Font: Exo (Google Font)
  - Weight: Bold
  - Alignment: Center
- **Usage**: Primary heading for the page

#### `<p>` (Author)
- **Purpose**: Author attribution
- **Content**: "By: monkeywarehouse"
- **Styling**:
  - Alignment: Center
  - Transform: Uppercase
  - Font: Helvetica, sans-serif
- **Usage**: Credits section

### 3. Main Content Section

#### `<main>`
- **Purpose**: Primary content area
- **Content**: Table section
- **Usage**: Contains the main cheatsheet table

#### `<section class="table">`
- **Purpose**: Wrapper for the data table
- **Content**: `<table>` element
- **Usage**: Semantic grouping of table content

### 4. Table Components

#### `<table>`
- **Purpose**: Data table displaying HTML tag information
- **Attributes**: `border="1"`
- **Content**: `<thead>`, `<tbody>`, `<tfooter>`
- **Usage**: Structured data presentation

#### `<thead>`
- **Purpose**: Table header section
- **Content**: Header row with column titles
- **Usage**: Defines table column headers

#### `<tr>` (Header Row)
- **Purpose**: Header row containing column titles
- **Content**: Three `<th>` elements
- **Usage**: Table header row

#### `<th>`
- **Purpose**: Table header cells
- **Content**: "Tag", "Name", "Use"
- **Styling**:
  - Font: Exo (Google Font)
  - Weight: 600 (semi-bold)
  - Letter spacing: 1px
- **Usage**: Column headers for the data table

#### `<tbody>`
- **Purpose**: Table body containing data rows
- **Content**: Multiple `<tr>` elements with tag data
- **Usage**: Contains the actual cheatsheet data

#### `<tr>` (Data Rows)
- **Purpose**: Individual data rows
- **Content**: Three `<td>` elements per row
- **Usage**: Each row represents one HTML tag

#### `<td>`
- **Purpose**: Table data cells
- **Content**: Tag syntax, display name, and description
- **Usage**: Individual data points in the table

#### `<td class="code">`
- **Purpose**: Special styling for HTML tag syntax
- **Content**: HTML tags with angle brackets
- **Styling**:
  - Font: Monospace, serif
  - Background: Light green
- **Usage**: Highlights HTML tag syntax in the table

#### `<tfooter>`
- **Purpose**: Table footer section (currently empty)
- **Content**: None
- **Usage**: Available for future table footer content

### 5. Footer Section

#### `<footer>`
- **Purpose**: Page footer area
- **Content**: Currently empty
- **Usage**: Available for future footer content

## CSS Components

### 1. Body Styling

```css
body {
    background-color: rgb(245,245,220);
}
```

**Purpose**: Sets the page background color
**Value**: Light beige color for easy reading
**Usage**: Applied to the entire page body

### 2. Table Header Styling

```css
th {
    font-family: 'Exo';
    font-weight: 600;
    letter-spacing: 1px;
}
```

**Purpose**: Styles table header cells
**Properties**:
- `font-family`: Uses Exo Google Font
- `font-weight`: Semi-bold (600)
- `letter-spacing`: 1px spacing for readability
**Usage**: Applied to all `<th>` elements

### 3. Code Element Styling

```css
.code {
    font-family: monospace, serif;
    background-color: lightgreen;
}
```

**Purpose**: Highlights HTML tag syntax
**Properties**:
- `font-family`: Monospace font for code appearance
- `background-color`: Light green background for emphasis
**Usage**: Applied to `<td>` elements with class "code"

## External Resources

### 1. Google Fonts

#### Exo Font
- **Source**: Google Fonts
- **URL**: `https://fonts.googleapis.com/css2?family=Exo:ital,wght@1,600&display=swap`
- **Usage**: Applied to table headers (`<th>` elements)
- **Preconnect**: Optimized loading with preconnect links

#### Preconnect Links
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="fonts.gstatic.com" crossorigin>
```

**Purpose**: Optimize Google Fonts loading
**Usage**: Placed in document head for performance

### 2. Stylesheet

#### Local CSS
- **File**: `styles.css`
- **Purpose**: Custom styling for the cheatsheet
- **Usage**: Applied to all HTML elements

## Component Relationships

### Hierarchy Structure
```
html
├── head
│   ├── Google Fonts links
│   └── styles.css link
└── body
    ├── header
    │   ├── h1 (title)
    │   └── p (author)
    ├── main
    │   └── section.table
    │       └── table
    │           ├── thead
    │           │   └── tr
    │           │       ├── th (Tag)
    │           │       ├── th (Name)
    │           │       └── th (Use)
    │           ├── tbody
    │           │   └── tr (data rows)
    │           │       ├── td.code (tag syntax)
    │           │       ├── td (display name)
    │           │       └── td (description)
    │           └── tfooter
    └── footer
```

### Styling Cascade
1. **Body**: Sets overall page background
2. **Headers**: Exo font with custom weight and spacing
3. **Code elements**: Monospace font with green background
4. **Default**: Browser default styling for other elements

## Accessibility Features

### Semantic HTML
- **`<header>`**: Clearly identifies page header
- **`<main>`**: Identifies primary content area
- **`<section>`**: Groups related content
- **`<table>`**: Proper table structure for screen readers

### Visual Hierarchy
- **Headers**: Bold, spaced text for easy scanning
- **Code elements**: Distinct styling for quick identification
- **Background**: Light color for reduced eye strain

## Browser Compatibility

### CSS Support
- **Background colors**: All modern browsers
- **Google Fonts**: All modern browsers with fallbacks
- **CSS properties**: Widely supported

### HTML Support
- **HTML5 elements**: All modern browsers
- **Table structure**: Universal support
- **Semantic elements**: Progressive enhancement

## Performance Considerations

### Font Loading
- **Preconnect**: Optimizes Google Fonts loading
- **Fallbacks**: System fonts as fallbacks
- **Display**: Fonts load asynchronously

### CSS Optimization
- **Minimal styles**: Only necessary styling
- **Efficient selectors**: Direct element targeting
- **No external dependencies**: Self-contained styling

## Future Enhancements

### Suggested Component Additions

#### 1. Search Component
```html
<div class="search-container">
    <input type="text" class="search-input" placeholder="Search tags...">
    <button class="search-button">Search</button>
</div>
```

#### 2. Filter Component
```html
<div class="filter-container">
    <select class="category-filter">
        <option value="">All Categories</option>
        <option value="text">Text</option>
        <option value="structure">Structure</option>
    </select>
</div>
```

#### 3. Navigation Component
```html
<nav class="table-nav">
    <button class="nav-prev">Previous</button>
    <span class="nav-info">Page 1 of 1</span>
    <button class="nav-next">Next</button>
</nav>
```

### Suggested CSS Enhancements

#### 1. Responsive Design
```css
@media (max-width: 768px) {
    .table {
        overflow-x: auto;
    }
    
    th, td {
        min-width: 120px;
    }
}
```

#### 2. Interactive States
```css
.code:hover {
    background-color: darkgreen;
    color: white;
}

tr:hover {
    background-color: rgba(0,0,0,0.05);
}
```

#### 3. Dark Mode Support
```css
@media (prefers-color-scheme: dark) {
    body {
        background-color: #2d2d2d;
        color: #ffffff;
    }
}
```

## Testing Guidelines

### Component Testing
1. **Visual**: Verify all elements render correctly
2. **Accessibility**: Test with screen readers
3. **Responsive**: Check on different screen sizes
4. **Performance**: Monitor font loading times

### Cross-browser Testing
- **Chrome**: Primary testing browser
- **Firefox**: Secondary testing browser
- **Safari**: Mobile and desktop testing
- **Edge**: Windows testing

## Maintenance Notes

### Adding New Tags
1. Add new `<tr>` in `<tbody>`
2. Include `<td class="code">` for tag syntax
3. Add display name and description
4. Test rendering in all browsers

### Modifying Styles
1. Update `styles.css` file
2. Test changes across browsers
3. Verify accessibility is maintained
4. Check performance impact

### Font Updates
1. Modify Google Fonts link in `<head>`
2. Update CSS font-family properties
3. Test loading performance
4. Verify fallback fonts work