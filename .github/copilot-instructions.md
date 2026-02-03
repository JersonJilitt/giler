# Giler - Premium Rewards Hub

Giler is a static HTML website that provides a platform for users to discover exclusive free deals, premium apps, and games through a rewards-based system. The site features interactive elements, admin functionality, and mobile-responsive design.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Bootstrap and Run the Website
- Navigate to the repository root: `cd /home/runner/work/giler/giler` 
- Start local development server: `python3 -m http.server 8000` -- NEVER CANCEL: Server starts immediately but keeps running. Set timeout to 300+ seconds for long development sessions.
- Access the website: Open browser to `http://localhost:8000`
- Stop server: Use `Ctrl+C` or stop the session

### Development and Testing
- No build process required - changes to `index.html` are immediately visible after browser refresh
- No dependencies to install - all external resources are loaded via CDN
- No transpilation or compilation steps needed

### Validation Scenarios
After making any changes to the website, ALWAYS test these core user scenarios:

1. **Basic Navigation Test**:
   - Load the homepage and verify it displays correctly
   - Click "Home", "How it Works", and "Search" navigation links
   - Verify smooth scrolling behavior to each section

2. **Tab Functionality Test**:
   - Click "Free Deals" tab and verify content updates
   - Click "Apps" tab and verify different content appears  
   - Click "Games" tab and verify games content is shown
   - Verify active tab highlighting works correctly

3. **Search Functionality Test**:
   - Type "spotify" in the search box
   - Verify search updates the displayed content
   - Clear search and verify content resets

4. **Admin Authentication Test**:
   - Click the "Giler" logo exactly 5 times rapidly
   - Verify admin authentication modal appears
   - Test login with credentials: username `admin`, password `giler2024`
   - Test the "Cancel" button to close modal

5. **Mobile Responsiveness Test**:
   - Resize browser window to mobile size (< 576px width)
   - Verify layout adapts correctly
   - Verify buttons have appropriate touch target sizes (44px minimum)

### Common Development Tasks

#### Modifying Content
- Edit text content directly in `index.html`
- Update CSS styles in the `<style>` section of `index.html`
- Modify JavaScript functionality in the `<script>` section of `index.html`

#### Adding New Offers/Deals
- Locate the JavaScript arrays: `freeDeals`, `apps`, or `games`
- Add new objects with `title`, `image`, `description`, and `lockerUrl` properties
- Changes are automatically saved to localStorage

#### Testing Admin Features
- Admin credentials are hardcoded: `ADMIN_USERNAME = "admin"`, `ADMIN_PASSWORD = "giler2024"`
- Admin panel allows adding offers, saving/loading data, and user management
- Access via clicking logo 5 times, then login with admin credentials

## Key Files and Structure

### Repository Root
```
.
├── .git/                 # Git repository data
├── .github/              # GitHub configuration (this file)
├── CNAME                 # GitHub Pages domain configuration (www.giler.site)
├── README.md             # Basic project description
└── index.html            # Main application file (all code in one file)
```

### index.html Structure
The entire application is contained in a single HTML file with three main sections:

1. **CSS Styles** (lines ~10-400): Complete styling including:
   - CSS custom properties for theming
   - Responsive design breakpoints
   - Animation keyframes
   - Component-specific styles

2. **HTML Structure** (lines ~600-750): Page layout including:
   - Navigation header
   - Welcome section
   - How it works section
   - Tabbed content areas
   - Admin authentication modal

3. **JavaScript** (lines ~750-1100): Application logic including:
   - Data storage with localStorage
   - Tab navigation system
   - Search functionality
   - Admin authentication
   - Mobile responsiveness handlers

## Technical Details

### External Dependencies
- Font Awesome 6.4.0 icons (loaded via CDN)
- No other external dependencies
- All JavaScript is vanilla JS (no frameworks)

### Data Storage
- Uses browser localStorage for persistence
- Three main data arrays: `freeDeals`, `apps`, `games`
- Admin authentication state tracked in memory only

### Browser Compatibility
- Modern browsers with ES6+ support
- CSS Grid and Flexbox used for layouts
- CSS custom properties (variables) used throughout

## Troubleshooting

### Common Issues
- **Images not loading**: External image URLs may be blocked by ad blockers or network restrictions. The site includes fallback "No Image" SVG placeholders.
- **Admin modal not appearing**: Ensure you click the logo exactly 5 times in rapid succession.
- **Search not working**: Verify JavaScript console for errors and check that the search input has focus.

### Local Development Issues
- **Port 8000 already in use**: Use `python3 -m http.server 8001` or another available port
- **Python not available**: Install Python 3 or use alternative local server like `php -S localhost:8000` or Node.js `npx serve`

### Validation Commands
- **No linting required**: Pure HTML/CSS/JS with no build tools
- **No testing framework**: Manual testing via browser interactions
- **No CI/CD**: Direct deployment to GitHub Pages

## Performance Notes
- **Loading time**: < 2 seconds on average connection
- **Interactive**: Immediate - no loading states needed
- **Server startup**: Instant with Python HTTP server
- **File size**: ~44KB total (single HTML file)

Always manually test the complete user flow after making changes to ensure the interactive elements work correctly.