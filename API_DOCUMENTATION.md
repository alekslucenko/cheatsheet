# API Documentation

## Overview

This document provides comprehensive documentation for all public APIs, functions, and components that could be implemented to enhance the HTML Cheatsheet project. While the current project is static HTML/CSS, these APIs represent the planned functionality for future versions.

## Core APIs

### 1. Search API

#### `searchTags(query: string, options?: SearchOptions): SearchResult[]`

Searches through the HTML tags table for matching entries.

**Parameters:**
- `query` (string): The search term to look for
- `options` (SearchOptions, optional): Search configuration options

**Returns:** Array of SearchResult objects

**Example:**
```javascript
// Basic search
const results = searchTags('paragraph');
console.log(results);
// Output: [{ tag: '<p>', name: 'Paragraph', use: 'Creates a paragraph of text.' }]

// Search with options
const results = searchTags('header', { 
    caseSensitive: false, 
    searchIn: ['name', 'use'] 
});
```

**SearchOptions Interface:**
```typescript
interface SearchOptions {
    caseSensitive?: boolean;     // Default: false
    searchIn?: string[];         // Default: ['tag', 'name', 'use']
    maxResults?: number;         // Default: 50
    fuzzy?: boolean;             // Default: false
}
```

**SearchResult Interface:**
```typescript
interface SearchResult {
    tag: string;        // The HTML tag (e.g., '<p>')
    name: string;       // Display name (e.g., 'Paragraph')
    use: string;        // Description of the tag's purpose
    rowIndex: number;   // Index in the original table
}
```

### 2. Tag Management API

#### `addTag(tagName: string, displayName: string, description: string, category?: string): boolean`

Adds a new HTML tag to the cheatsheet.

**Parameters:**
- `tagName` (string): The HTML tag name (without brackets)
- `displayName` (string): Human-readable name for the tag
- `description` (string): Description of what the tag does
- `category` (string, optional): Category for grouping tags

**Returns:** boolean indicating success

**Example:**
```javascript
const success = addTag('div', 'Division', 'Creates a block-level container', 'structure');
if (success) {
    console.log('Tag added successfully');
}
```

#### `removeTag(tagName: string): boolean`

Removes a tag from the cheatsheet.

**Parameters:**
- `tagName` (string): The HTML tag name to remove

**Returns:** boolean indicating success

**Example:**
```javascript
const removed = removeTag('p');
if (removed) {
    console.log('Paragraph tag removed');
}
```

#### `updateTag(tagName: string, updates: TagUpdate): boolean`

Updates an existing tag's information.

**Parameters:**
- `tagName` (string): The HTML tag name to update
- `updates` (TagUpdate): Object containing fields to update

**Returns:** boolean indicating success

**Example:**
```javascript
const updated = updateTag('p', {
    displayName: 'Paragraph Element',
    description: 'Creates a paragraph of text with proper spacing.'
});
```

**TagUpdate Interface:**
```typescript
interface TagUpdate {
    displayName?: string;
    description?: string;
    category?: string;
}
```

### 3. Export API

#### `exportCheatsheet(format: ExportFormat, options?: ExportOptions): string | Blob`

Exports the cheatsheet data in various formats.

**Parameters:**
- `format` (ExportFormat): The desired export format
- `options` (ExportOptions, optional): Export configuration

**Returns:** Exported data as string or Blob

**Example:**
```javascript
// Export as JSON
const jsonData = exportCheatsheet('json');
console.log(jsonData);

// Export as CSV
const csvData = exportCheatsheet('csv', { 
    includeHeaders: true,
    delimiter: ',' 
});

// Export as HTML table
const htmlTable = exportCheatsheet('html', { 
    includeStyles: true 
});
```

**ExportFormat Type:**
```typescript
type ExportFormat = 'json' | 'csv' | 'html' | 'markdown' | 'pdf';
```

**ExportOptions Interface:**
```typescript
interface ExportOptions {
    includeHeaders?: boolean;     // Default: true
    delimiter?: string;           // Default: ',' (for CSV)
    includeStyles?: boolean;      // Default: false (for HTML)
    filename?: string;            // Default: 'html-cheatsheet'
}
```

### 4. Filter API

#### `filterByCategory(category: string): Tag[]`

Filters tags by their category.

**Parameters:**
- `category` (string): The category to filter by

**Returns:** Array of Tag objects

**Example:**
```javascript
const textTags = filterByCategory('text');
console.log(textTags);
// Output: [{ tag: '<p>', name: 'Paragraph', ... }, ...]
```

#### `getCategories(): string[]`

Returns all available categories.

**Returns:** Array of category names

**Example:**
```javascript
const categories = getCategories();
console.log(categories);
// Output: ['text', 'structure', 'form', 'media', ...]
```

#### `filterByUsage(usagePattern: string): Tag[]`

Filters tags by usage pattern.

**Parameters:**
- `usagePattern` (string): Pattern to match in usage descriptions

**Returns:** Array of Tag objects

**Example:**
```javascript
const containerTags = filterByUsage('container');
console.log(containerTags);
```

### 5. UI Management API

#### `highlightRow(rowIndex: number, highlight: boolean): void`

Highlights or unhighlights a table row.

**Parameters:**
- `rowIndex` (number): Index of the row to highlight
- `highlight` (boolean): Whether to highlight or unhighlight

**Example:**
```javascript
// Highlight the first row
highlightRow(0, true);

// Remove highlight
highlightRow(0, false);
```

#### `scrollToTag(tagName: string): boolean`

Scrolls the page to a specific tag.

**Parameters:**
- `tagName` (string): The HTML tag name to scroll to

**Returns:** boolean indicating success

**Example:**
```javascript
const scrolled = scrollToTag('p');
if (scrolled) {
    console.log('Scrolled to paragraph tag');
}
```

#### `toggleTableSort(column: string, direction?: 'asc' | 'desc'): void`

Sorts the table by a specific column.

**Parameters:**
- `column` (string): Column to sort by ('tag', 'name', 'use')
- `direction` ('asc' | 'desc', optional): Sort direction

**Example:**
```javascript
// Sort by tag name ascending
toggleTableSort('tag', 'asc');

// Sort by description descending
toggleTableSort('use', 'desc');
```

## Utility Functions

### `debounce(func: Function, delay: number): Function`

Creates a debounced version of a function.

**Parameters:**
- `func` (Function): The function to debounce
- `delay` (number): Delay in milliseconds

**Returns:** Debounced function

**Example:**
```javascript
const debouncedSearch = debounce(searchTags, 300);
input.addEventListener('input', (e) => {
    debouncedSearch(e.target.value);
});
```

### `throttle(func: Function, limit: number): Function`

Creates a throttled version of a function.

**Parameters:**
- `func` (Function): The function to throttle
- `limit` (number): Time limit in milliseconds

**Returns:** Throttled function

**Example:**
```javascript
const throttledScroll = throttle(scrollToTag, 100);
```

## Event System

### Events

The API system emits various events that can be listened to:

```javascript
// Listen for tag additions
document.addEventListener('tagAdded', (event) => {
    console.log('New tag added:', event.detail);
});

// Listen for searches
document.addEventListener('searchPerformed', (event) => {
    console.log('Search results:', event.detail.results);
});

// Listen for exports
document.addEventListener('exportCompleted', (event) => {
    console.log('Export completed:', event.detail.format);
});
```

### Event Types

- `tagAdded`: Emitted when a new tag is added
- `tagRemoved`: Emitted when a tag is removed
- `tagUpdated`: Emitted when a tag is updated
- `searchPerformed`: Emitted when a search is executed
- `exportCompleted`: Emitted when an export is completed
- `filterApplied`: Emitted when a filter is applied

## Error Handling

All API functions throw descriptive errors when operations fail:

```javascript
try {
    const result = addTag('', 'Empty Tag', 'This will fail');
} catch (error) {
    console.error('Error adding tag:', error.message);
    // Output: "Error adding tag: Tag name cannot be empty"
}
```

### Common Error Types

- `ValidationError`: Invalid input parameters
- `NotFoundError`: Tag not found for operations
- `ExportError`: Export operation failed
- `NetworkError`: Network-related errors (for future features)

## Performance Considerations

- Search operations are optimized with indexing
- Large datasets use virtual scrolling
- Export operations are asynchronous for large datasets
- UI updates are batched for better performance

## Browser Compatibility

- **ES6+**: All APIs use modern JavaScript features
- **Polyfills**: Available for older browsers
- **Progressive Enhancement**: Core functionality works without JavaScript

## Testing

All APIs include comprehensive test coverage:

```javascript
// Example test
describe('Search API', () => {
    test('should find tags by name', () => {
        const results = searchTags('paragraph');
        expect(results).toHaveLength(1);
        expect(results[0].tag).toBe('<p>');
    });
});
```