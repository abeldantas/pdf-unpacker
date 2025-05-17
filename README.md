# PDF Unpacker

A tool to convert PDF files to Markdown format while preserving images by uploading them to Imgur. Perfect for making your PDFs AI-processable and editable.

## Features

- Converts PDF files to clean Markdown format
- Automatically extracts images from PDFs
- Uploads images to Imgur for reliable hosting
- Strategically places image references throughout the document
- Updates Markdown references to use Imgur URLs
- Supports batch conversion of multiple PDFs

## Requirements

- For PDF to Markdown conversion:
  - `npx` and Node.js - To run the pdf2md package
  - `@opendocsg/pdf2md` - Will be automatically installed if missing
  - `curl` - For API calls to Imgur
  - `jq` - For parsing JSON responses

- Optional but recommended for image extraction:
  - `pdfimages` (from poppler-utils package) - For extracting images from PDFs
  - `convert` (from ImageMagick) - For converting image formats before uploading

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/abeldantas/pdf-unpacker.git
   cd pdf-unpacker
   ```

2. Make the script executable:
   ```bash
   chmod +x pdf2markdown
   ```

3. Create a `.env` file with your Imgur credentials:
   ```bash
   # .env file
   IMGUR_CLIENT_ID=your_client_id
   IMGUR_CLIENT_SECRET=your_client_secret
   IMGUR_ACCESS_TOKEN=your_access_token
   IMGUR_REFRESH_TOKEN=your_refresh_token
   ```

## Usage

### Converting a Single PDF

```bash
./pdf2markdown input.pdf [output.md]
```

If you don't specify an output file, it will use the same name as the input file with a `.md` extension.

### Batch Converting Multiple PDFs

```bash
./pdf2markdown --folder path/to/pdfs output/dir
```

This will convert all PDF files in the specified directory and save the Markdown files to the output directory.

## Getting Imgur API Credentials

To use this tool, you need to set up Imgur API credentials:

1. Create an Imgur account at [imgur.com](https://imgur.com/)
2. Register an application at [api.imgur.com/oauth2/addclient](https://api.imgur.com/oauth2/addclient)
   - Select "OAuth 2 authorization without a callback URL"
   - Fill in the required information
3. Note your Client ID and Client Secret
4. Generate access and refresh tokens following the OAuth flow

You can follow this [video tutorial](https://www.youtube.com/watch?v=anfNgyplDjI&t=73s) for detailed instructions on obtaining tokens.

For more information about the Imgur API, see the [official documentation](https://apidocs.imgur.com/).

## Imgur Limits

Be aware of Imgur's upload limits:

- **Free account**: 
  - 50 uploads per day
  - Images may be removed after 6 months of inactivity
  - 20MB per image

- **Imgur Emerald** ($5/month or $49/year):
  - Unlimited uploads
  - Images stored permanently
  - Ad-free experience

## Notes

- The `.env` file containing your API credentials is excluded from git via `.gitignore`
- Images are temporarily extracted during conversion but are cleaned up afterward
- Imgur does not support all file formats - PDFs with unsupported image formats may have issues

## License

MIT