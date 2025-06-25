# Simple Node.js Pastebin

A minimalist pastebin service built with Node.js and Express that uses content hashing for unique paste identification.

## Features

• **Content-based hashing** - SHA-256 hash of content as paste ID
• **Automatic deduplication** - Identical content shares same URL
• **Raw text view** - Access raw content at `/raw/:id`
• **File-based storage** - Stores pastes as text files locally
• **Clean interface** - Minimal UI focused on functionality
• **XSS protection** - Basic HTML escaping for security

## Installation

1. **Clone or create project directory**
```bash
mkdir pastebin && cd pastebin
```

2. **Initialize project**
```bash
yarn init -y
yarn add express
```

3. **Update package.json**
```json
{
  "type": "module"
}
```

4. **Copy the code to index.js and run**
```bash
node index.js
```

## Usage

### Creating Pastes
• Visit `http://localhost:3000`
• Enter your content in the textarea
• Click "Create Paste"
• Get a clickable hash ID that links to your paste

### Viewing Pastes
• **HTML view**: `/paste/:id` - Formatted display
• **Raw view**: `/raw/:id` - Plain text content

### API Endpoints
• `GET /` - Home page with paste form
• `POST /paste` - Create new paste
• `GET /paste/:id` - View paste in HTML format
• `GET /raw/:id` - View raw paste content

## How It Works

1. **Content Hashing**: Uses SHA-256 to generate unique IDs from content
2. **Deduplication**: Same content always gets same hash/URL
3. **File Storage**: Saves pastes as `{hash}.txt` in `./pastes/` directory
4. **Immutable**: Content cannot be modified (would change hash)

## Project Structure

```
pastebin/
├── index.js        # Main application
├── package.json    # Dependencies and config
├── pastes/         # Auto-created directory for paste files
└── README.md       # This file
```

## Configuration

• **Port**: Default 3000 (change `PORT` variable in index.js)
• **Storage**: Files stored in `./pastes/` directory
• **Hash Algorithm**: SHA-256 (64 character hex strings)

## Security Notes

• Basic XSS protection with HTML escaping
• No authentication or rate limiting
• Files stored locally (not suitable for production without modifications)
• Consider adding HTTPS, rate limiting, and proper security headers for production use

## License

MIT
