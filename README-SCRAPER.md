# PW.Live Advanced Scraper

A sophisticated web scraper for PW.Live educational content with advanced anti-detection measures and security features.

## 🚀 Features

### Advanced Security & Anti-Detection
- **Random User Agents**: Rotates between realistic browser user agents
- **Smart Rate Limiting**: Prevents overwhelming the server with requests
- **Random Delays**: Human-like behavior with variable request timing
- **Session Management**: Secure cookie handling and authentication
- **CSRF Protection**: Automatic token extraction and handling
- **Retry Logic**: Automatic error recovery with exponential backoff
- **Request Headers**: Realistic browser headers to avoid detection
- **Multiple Selectors**: Adaptive content extraction strategies

### Content Types Supported
- **Batches**: Course batches and programs
- **Lectures**: Video lectures and recorded sessions
- **Notes**: Study materials and written notes
- **DPP**: Daily Practice Problems and exercises
- **DPP Notes**: Solutions and explanations for DPP

## 🛠️ Installation & Setup

### Prerequisites
- Node.js 18+ 
- npm or yarn
- Valid PW.Live account credentials

### Dependencies Installed
```bash
npm install axios cheerio axios-cookiejar-support tough-cookie --legacy-peer-deps
```

### Running the Application
```bash
npm run dev
```
The application will be available at `http://localhost:8000`

## 📖 Usage

### Web Interface
1. Open `http://localhost:8000` in your browser
2. Enter your PW.Live username and password
3. Click "Start Scraping" to begin the process
4. Wait for the results to be displayed

### API Endpoints

#### Health Check
```bash
GET /api/pw-scraper
```
Returns service status and health information.

#### Scrape Data
```bash
POST /api/pw-scraper
Content-Type: application/json

{
  "username": "your_username",
  "password": "your_password"
}
```

### Response Format
```json
{
  "success": true,
  "data": {
    "batches": [
      {
        "title": "Course Title",
        "link": "https://pw.live/course/...",
        "type": "batches",
        "scrapedAt": "2024-01-01T00:00:00.000Z"
      }
    ],
    "lectures": [...],
    "notes": [...],
    "dpp": [...],
    "dppNotes": [...]
  },
  "timestamp": "2024-01-01T00:00:00.000Z",
  "message": "Data scraped successfully"
}
```

## 🔒 Security Features

### Anti-Detection Measures
- **User Agent Rotation**: 5 different realistic browser user agents
- **Request Timing**: Random delays between 2-5 seconds
- **Rate Limiting**: Maximum 10 requests per minute
- **Header Variation**: Dynamic browser headers for each request
- **Session Persistence**: Maintains login state across requests

### Error Handling
- **Automatic Retries**: Up to 3 attempts for failed requests
- **Exponential Backoff**: Increasing delays between retry attempts
- **Graceful Degradation**: Continues scraping other sections if one fails
- **Detailed Error Messages**: Clear feedback for different error types

### Security Best Practices
- **No Credential Storage**: Credentials are processed but never stored
- **HTTPS Only**: All requests use secure connections
- **Input Validation**: Comprehensive validation of user inputs
- **Error Sanitization**: Safe error messages without sensitive data

## 🏗️ Architecture

### File Structure
```
src/
├── app/
│   ├── api/pw-scraper/route.ts    # API endpoint
│   ├── layout.tsx                 # App layout
│   └── page.tsx                   # Main UI component
└── lib/
    └── pwScraper.ts              # Core scraping logic
```

### Core Components

#### `pwScraper.ts`
- Main scraping engine with anti-detection measures
- Login authentication and session management
- Content extraction with multiple fallback strategies
- Rate limiting and error handling

#### `route.ts`
- RESTful API endpoint for scraping requests
- Input validation and sanitization
- Error handling and response formatting
- Health check functionality

#### `page.tsx`
- Modern React UI with Tailwind CSS
- Real-time status updates and progress indication
- Responsive design for all device sizes
- Clean, professional interface

## ⚙️ Configuration

### Anti-Detection Settings
```typescript
const ANTI_DETECTION_CONFIG = {
  minDelay: 2000,        // Minimum delay between requests (ms)
  maxDelay: 5000,        // Maximum delay between requests (ms)
  timeout: 30000,        // Request timeout (ms)
  maxRetries: 3,         // Maximum retry attempts
  maxRequestsPerMinute: 10, // Rate limiting
};
```

### Customization
You can modify the scraping behavior by editing:
- **URLs**: Update target URLs in the `scrapeData` function
- **Selectors**: Modify CSS selectors for content extraction
- **Delays**: Adjust timing parameters for your needs
- **User Agents**: Add more user agents to the rotation

## 🚨 Important Notes

### Legal & Ethical Use
- Only use with your own PW.Live account
- Respect the platform's terms of service
- Use responsibly and avoid overloading servers
- This tool is for educational purposes

### Limitations
- Requires valid PW.Live account credentials
- Subject to changes in PW.Live's website structure
- Rate limited to prevent server overload
- May need updates if site structure changes

### Troubleshooting

#### Common Issues
1. **Login Failed**: Check credentials and account status
2. **Rate Limited**: Wait before making more requests
3. **No Data Found**: Site structure may have changed
4. **Network Errors**: Check internet connection

#### Error Codes
- `400`: Invalid input or missing credentials
- `401`: Authentication failed
- `408`: Request timeout
- `429`: Rate limit exceeded
- `500`: Internal server error
- `503`: Service unavailable

## 🔧 Development

### Adding New Content Types
1. Add new URL to the `urls` object in `scrapeData`
2. Update the UI section titles and descriptions
3. Test with different CSS selectors if needed

### Enhancing Security
- Add more user agents to the rotation
- Implement proxy support for additional anonymity
- Add more sophisticated timing patterns
- Enhance header randomization

## 📝 License

This project is for educational purposes only. Please ensure compliance with PW.Live's terms of service and applicable laws.

## 🤝 Contributing

When contributing:
1. Maintain security best practices
2. Test thoroughly with different scenarios
3. Update documentation for any changes
4. Follow the existing code style and patterns

---

**⚠️ Disclaimer**: This tool is provided as-is for educational purposes. Users are responsible for ensuring compliance with all applicable terms of service and laws.
