<h1 align="center">
  ✨ YouTube Transcript API JS ✨
</h1>

<p align="center">
  <a href="https://www.npmjs.com/package/youtube-transcript-js">
    <img src="https://img.shields.io/npm/v/youtube-transcript-js.svg" alt="NPM Version">
  </a>
  <a href="https://www.npmjs.com/package/youtube-transcript-js">
    <img src="https://img.shields.io/npm/dm/youtube-transcript-js.svg" alt="NPM Downloads">
  </a>
</p>

<p align="center">
  <b>A lightweight JavaScript API and CLI for retrieving YouTube video transcripts and subtitles (including auto-generated and translated ones). No headless browsers required.</b>
</p>

---

**Author:** Chintamani Pala

---

## Features

- Fetch YouTube video transcripts (captions/subtitles) via API or CLI.
- Supports auto-generated and manually created transcripts.
- Supports translation (where available).
- No browser automation or scraping required.
- Proxy support for bypassing IP blocks.
- Multiple output formats: JSON, text, SRT, WebVTT, pretty-print.

---

## Installation

```bash
npm install youtube-transcript-js
```

Or clone this repository and install dependencies:

```bash
git clone https://github.com/chintamani-pala/youtube-transcript-js.git
cd youtube-transcript-js
npm install
```

---

## Usage

### As a Library (API)

```js
const {
  YouTubeTranscriptApi,
  TranscriptListFetcher,
  ProxyConfig,
  GenericProxyConfig,
  WebshareProxyConfig,
  InvalidProxyConfig,
  formatters,
  errors,
  settings
} = require('youtube-transcript-js');

const ytt_api = new YouTubeTranscriptApi();
const video_id = '0Okxsszt624';

ytt_api.fetch(video_id, ['en']).then(transcript => {
    console.log(transcript);
}).catch(err => {
    console.error(err);
});
```

#### API Exports

- `YouTubeTranscriptApi` - Main API class
- `YouTubeTranscriptCli` - CLI class
- `TranscriptListFetcher` - Fetches transcript lists
- `ProxyConfig`, `GenericProxyConfig`, `WebshareProxyConfig`, `InvalidProxyConfig` - Proxy support
- `formatters` - Output formatters (JSON, SRT, WebVTT, etc.)
- `errors` - Custom error classes
- `settings` - Internal constants

---

### CLI Usage

You can use the CLI to fetch transcripts directly from the terminal.

```bash
npx youtube-transcript-js --video-ids=0Okxsszt624 --format=json
```

#### CLI Options

- `--video-ids` (comma-separated list or positional arguments)
- `--format` (json, pretty, text, srt, webvtt)  
  _Default: pretty_
- `--languages` (comma-separated, e.g. `en,hi`)
- `--excludeManuallyCreated`  
- `--excludeGenerated`  
- `--httpProxy`  
- `--httpsProxy`  
- `--webshareProxyUsername`  
- `--webshareProxyPassword`  
- `--preserveFormatting`  

#### Example

```bash
npx youtube-transcript-js --video-ids=0Okxsszt624 --format=json
```

---

## Proxy Support

You can use proxies to bypass IP blocks.  
Supports generic HTTP/HTTPS proxies and [Webshare](https://www.webshare.io/) rotating residential proxies.

Example:

```js
const { GenericProxyConfig, YouTubeTranscriptApi } = require('youtube-transcript-js');
const proxyConfig = new GenericProxyConfig('http://your-proxy:port');
const ytt_api = new YouTubeTranscriptApi({ proxyConfig });
```

---

## Output Formats

- **pretty**: Node.js util.inspect
- **json**: Raw JSON
- **text**: Plain text
- **srt**: SubRip Subtitle
- **webvtt**: Web Video Text Tracks

---


## License

MIT

---

## Author

Chintamani Pala
