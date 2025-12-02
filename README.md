#  AI Contact Intelligence Extractor

**Extract any information from websites using intelligent AI - from contact details to custom data fields, summaries, and creative content.**

This powerful Apify actor combines traditional web scraping with advanced AI capabilities to extract exactly what you need from any website. Whether you're collecting contact information, generating summaries, or creating custom data structures, this actor adapts to your specific requirements.

![AI Contact Intelligence Extractor](https://raw.githubusercontent.com/DZ-ABDLHAKIM/ai-contact-intelligence/refs/heads/main/unnamed.png)


---

## Key Features

### 🎯 Dual Extraction Modes

**🆓 Free Tier - Basic Extraction + AI (Pay-Per-Use)**
- **Contact Information** - Emails, phone numbers, social media links
- **AI-Powered Extraction** - Available via pay-per-use model through your Apify account
- **Simple AI Model** - Fast and efficient extraction for common tasks
- **Perfect for Testing** - Try AI features before upgrading

**💎 Paid Tier - Premium AI Extraction**
- **Advanced AI Model** - Superior accuracy and understanding for complex extraction
- **Universal Data Extraction** - Extract ANY information you specify
- **Natural Language Instructions** - Tell the AI what you want
- **Intelligent Understanding** - AI analyzes and extracts complex data patterns
- **Flexible Output** - Get summaries, structured data, or creative content
- **Context-Aware** - Understands relationships between data points
- **Included in Subscription** - No per-use charges for AI extraction
- **Includes Basic Extraction** - Get both AI insights AND traditional contact data

### ⚡ Performance & Reliability
- **Full Browser Rendering** - Handles all modern websites with JavaScript support
- **Screenshot Capture** - Automatically captures page screenshots for reference
- **Smart Token Management** - Automatic overflow protection (15,000 token limit)
- **Automatic Retry Logic** - Built-in error recovery with exponential backoff for rate limits
- **Graceful Fallback** - Switches to basic extraction if AI fails
- **Memory-Based Billing** - Transparent, predictable pricing model

### 🛠️ Developer-Friendly
- **Clean JSON Output** - Ready for any data pipeline or API integration
- **Flexible Configuration** - Control extraction method and instructions
- **Multiple Views** - Pre-configured data views for different use cases

---

## 📖 How It Works

### Free Users (Basic + AI Pay-Per-Use)
1. **Input URLs** - Provide one or more website links
2. **Choose Mode** - Use basic extraction only, or enable AI (charges per use)
3. **AI Optional** - Pay per request to access AI-powered extraction
4. **Get Results** - Contact data + optional AI insights in structured JSON

### Paid Users (Premium AI Included)
1. **Input URLs** - Provide one or more website links
2. **Write Instructions** - Tell the AI what to extract
3. **Enable AI Extraction** - Use advanced AI model (included in your subscription)
4. **Get Premium Results** - AI extracts exactly what you requested, plus basic contact data

---

##  Input Configuration

### Basic Input (Basic Extraction Only)

```json
{
  "startUrls": [
    { "url": "https://example.com/contact" },
    { "url": "https://example.com/about" }
  ],
  "useAI": false
}
```

### AI-Powered Input (Free Users - Pay Per Use)

```json
{
  "startUrls": [
    { "url": "https://apify.com/about" }
  ],
  "useAI": true,
  "aiInstructions": "Summarize this page in 3 bullet points"
}
```

**Note for Free Users:** Enabling AI will charge your Apify account per request. You can control costs by disabling AI when you only need basic contact extraction.

### Premium AI Input (Paid Subscription - Included)

```json
{
  "startUrls": [
    { "url": "https://apify.com/about" }
  ],
  "useAI": true,
  "aiInstructions": "Extract CEO name, support email, and company mission statement"
}
```

**Note for Paid Users:** AI extraction is included in your subscription at no additional cost. You get access to our most advanced AI model for superior accuracy.

### Advanced AI Extraction Examples

**Extract Specific Contact Info:**
```json
{
  "aiInstructions": "Extract CEO name, support email, and company address"
}
```

**Generate Content Summary:**
```json
{
  "aiInstructions": "Summarize key services and pricing in 5 bullet points"
}
```

**Custom Data Fields:**
```json
{
  "aiInstructions": "List team members with their roles and social media links"
}
```

**Creative Output:**
```json
{
  "aiInstructions": "Write a 2-sentence company description based on this page"
}
```

### Input Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `startUrls` | `array` | **Required** | List of website URLs to scrape (supports any valid HTTP/HTTPS URL) |
| `useAI` | `boolean` | `false` | Enable AI-powered extraction. **Free users:** Charges per request. **Paid users:** Included in subscription with advanced model. |
| `aiInstructions` | `string` | "Summarize this page in 3 bullet points" | Natural language instructions for AI (max 75 words/500 characters). Ignored if AI is disabled. |

---

## 📤 Output Structure

### Free Tier Output (Basic Extraction Only)

```json
{
  "url": "https://example.com",
  "title": "Example Company - Contact Us",
  "basicExtraction": {
    "emails": ["info@example.com", "support@example.com"],
    "phones": ["+1-555-0100", "+1-555-0200"],
    "socialLinks": [
      "https://twitter.com/example",
      "https://linkedin.com/company/example"
    ],
    "extractionMethod": "regex"
  },
  "screenshot": {
    "available": true,
    "key": "screenshot-abc123",
    "url": "https://api.apify.com/v2/key-value-stores/xyz/records/screenshot-abc123"
  },
  "extractionTier": "FREE",
  "extractionMethod": "Basic Only",
  "userTier": "FREE",
  "isPaidUser": false,
  "note": "Basic extraction only. Enable 'Use AI' to unlock AI-powered extraction (charges apply per request).",
  "scrapedAt": "2025-11-28T21:06:12.787Z"
}
```

### Free Tier Output (With AI Pay-Per-Use)

```json
{
  "url": "https://apify.com/about",
  "title": "About · Apify",
  "aiExtraction": {
    "summary_bullets": [
      "Apify is a platform for developing web automation solutions, founded in 2015.",
      "Their mission is to help people get more value from the web.",
      "Trusted by industry leaders with 25,000+ customers worldwide."
    ]
  },
  "basicExtraction": {
    "emails": [],
    "phones": ["+420-123-456-789"],
    "socialLinks": [
      "http://linkedin.com/company/apify",
      "https://x.com/apify"
    ],
    "extractionMethod": "regex"
  },
  "screenshot": {
    "available": true,
    "key": "screenshot-xyz789",
    "url": "https://api.apify.com/v2/key-value-stores/abc/records/screenshot-xyz789"
  },
  "extractionTier": "FREE",
  "extractionMethod": "AI-Powered + Basic",
  "userTier": "FREE",
  "isPaidUser": false,
  "tokenCount": 1945,
  "note": "AI extraction completed using OpenRouter (charged to your Apify account).",
  "scrapedAt": "2025-11-29T12:34:56.789Z"
}
```

### Paid Tier Output (Premium AI + Basic Extraction)

```json
{
  "url": "https://apify.com/about",
  "title": "About · Apify",
  "aiExtraction": {
    "ceo_name": "Jan Čurn",
    "support_email": "support@apify.com",
    "company_mission": "To make the web more programmable and help businesses get value from web data"
  },
  "basicExtraction": {
    "emails": ["support@apify.com", "sales@apify.com"],
    "phones": ["+420-123-456-789"],
    "socialLinks": [
      "http://linkedin.com/company/apify",
      "https://x.com/apify",
      "https://github.com/apify"
    ],
    "extractionMethod": "regex"
  },
  "screenshot": {
    "available": true,
    "key": "screenshot-7Gd9k2Pq1Lm",
    "url": "https://api.apify.com/v2/key-value-stores/xGJUQLo3QjB68fqFG/records/screenshot-7Gd9k2Pq1Lm"
  },
  "extractionTier": "PAID",
  "extractionMethod": "AI-Powered + Basic",
  "userTier": "GOLD",
  "isPaidUser": true,
  "tokenCount": 1945,
  "note": "AI extraction completed using included premium AI model.",
  "scrapedAt": "2025-11-29T12:34:56.789Z"
}
```

### Output Fields Explained

#### Common Fields (All Tiers)
- `url` - Scraped website URL
- `title` - Page title extracted from HTML
- `extractionTier` - `FREE` or `PAID`
- `extractionMethod` - Extraction method used
- `userTier` - User subscription level (FREE, BRONZE, SILVER, GOLD)
- `isPaidUser` - Boolean indicating paid status
- `scrapedAt` - Timestamp of extraction
- `screenshot` - Screenshot information with URL for viewing

#### Basic Extraction (All Tiers)
- `basicExtraction.emails` - Array of email addresses found
- `basicExtraction.phones` - Array of phone numbers detected
- `basicExtraction.socialLinks` - Array of social media URLs
- `basicExtraction.extractionMethod` - Always "regex" for basic extraction

#### AI Extraction (When Enabled)
- `aiExtraction` - Dynamic object containing whatever the AI extracted based on your instructions
- `userInstructions` - The instructions you provided to the AI
- `tokenCount` - Number of tokens processed (for transparency)
- `note` - Information about which AI model was used and billing details

**Note:** The structure of `aiExtraction` varies based on your instructions. The AI creates appropriate field names to match your request.

---

## 🎯 What Can AI Extract?

### 📋 Structured Data
- **Contact Information** - "Extract all emails, phone numbers, and addresses"
- **Team Members** - "List all team members with their names and roles"
- **Pricing Plans** - "Extract pricing tiers with features and costs"
- **Product Details** - "Find product names, descriptions, and specifications"

### 📝 Content Summaries
- **Page Summaries** - "Summarize this page in 3-5 bullet points"
- **Key Takeaways** - "What are the main services offered on this page?"
- **Company Overview** - "Describe what this company does in 2 sentences"

### 🎨 Creative Content
- **Marketing Copy** - "Write a catchy tagline based on this company's mission"
- **Social Media Posts** - "Create a LinkedIn post about this company"
- **Descriptions** - "Write a professional company description"

### 🔍 Analysis & Insights
- **Feature Comparison** - "Compare the features of different pricing plans"
- **Sentiment Analysis** - "Describe the tone and messaging of this page"
- **Key Topics** - "List the main topics covered on this page"

---

## 💰 Pricing & Billing

### Free Tier
- ✅ **Basic extraction** - Always free
- ✅ **Screenshot capture** - Included
- 💳 **AI extraction** - Pay per request through Apify (simple AI model)
- 💡 **Cost control** - Disable AI when you only need basic contact data

### Paid Tier (Bronze/Silver/Gold)
- ✅ **Basic extraction** - Included
- ✅ **Screenshot capture** - Included
- ✅ **Premium AI extraction** - Included (advanced model, no per-use charges)
- ✅ **Better AI accuracy** - Access to our most sophisticated AI model
- ✅ **Unlimited AI requests** - No per-request billing for AI features

### Upgrade Benefits

| Feature | Free Tier | Paid Tier |
|---------|-----------|-----------|
| Basic Extraction | ✅ Free | ✅ Included |
| Screenshots | ✅ Free | ✅ Included |
| AI Model | Simple (pay-per-use) | **Advanced** (included) |
| AI Accuracy | Good | **Superior** |
| AI Billing | Per request | **No additional cost** |
| Complex Extractions | Limited | **Excellent** |
| Cost Predictability | Variable | **Fixed subscription** |

---

## 💡 Professional Use Cases

### 🎯 Lead Generation & Sales
- **Contact Discovery** - Extract emails and phone numbers from company websites
- **Prospect Research** - Gather company information and key personnel details
- **Market Intelligence** - Analyze competitor offerings and pricing
- **Outreach Personalization** - Extract company details for personalized messaging

### 📊 Market Research
- **Competitor Analysis** - Extract product features, pricing, and positioning
- **Industry Trends** - Summarize key information from multiple sources
- **Content Analysis** - Analyze messaging and value propositions
- **Vendor Evaluation** - Extract and compare vendor capabilities

### 🤖 AI & Automation
- **Training Data** - Extract structured data for ML model training
- **Content Enrichment** - Augment existing databases with web data
- **Automated Monitoring** - Track changes in competitor information
- **Data Pipeline Integration** - Feed structured data into analytics platforms

### 📝 Content Creation
- **Research Automation** - Quickly summarize information from multiple sources
- **Fact Checking** - Extract verifiable claims and statistics
- **Content Repurposing** - Transform web content into different formats
- **Citation Management** - Extract sources and references

---

## 📊 Pre-Configured Data Views

### 1. 📋 Overview
Quick summary of all extractions with key metadata.

**Fields:** Screenshot preview, URL, title, extraction method, user tier, paid status, timestamp

### 2. 🎯 Full Results
Complete dataset with both AI extraction and basic contact data.

**Fields:** Screenshot, URL, title, AI extraction results, basic extraction (emails, phones, social links), extraction method, user tier

Perfect for comprehensive analysis and data export.

---

## 🚀 Getting Started

### 1. Sign Up
Create a free Apify account at [apify.com](https://apify.com?fpr=smcx63)

### 2. Configure Input
Choose your URLs and extraction settings:

**For Basic Extraction (Free):**
```json
{
  "startUrls": [{"url": "https://example.com"}],
  "useAI": false
}
```

**For AI Extraction:**
```json
{
  "startUrls": [{"url": "https://example.com"}],
  "useAI": true,
  "aiInstructions": "Extract contact email and company description"
}
```

### 3. Run the Actor
Click "Start" and let the actor process your URLs.

### 4. Download Results
Export data in JSON, CSV, Excel, or via API.

---

## ⚠️ Important Notes

### AI Extraction Options

**Free Users:**
- ✅ Can use AI features via pay-per-request model
- ✅ Access to simple AI model for basic tasks
- ✅ Perfect for testing before committing to subscription
- 💳 Charges applied to Apify account per request
- ⚡ Automatic retry logic handles rate limits gracefully

**Paid Users:**
- ✅ AI features included in subscription
- ✅ Access to advanced AI model for superior accuracy
- ✅ No per-request charges
- ✅ Better for complex, nuanced extraction tasks
- ✅ Predictable costs

### Token Limits
- **15,000 token limit per page** - Pages exceeding this limit automatically fallback to basic extraction
- **Instruction limit:** 75 words / 500 characters
- Long instructions are automatically truncated

### Best Practices
1. **Be specific in AI instructions** - "Extract CEO name" works better than "Find information about leadership"
2. **Test with single URLs first** - Verify your instructions work before batch processing
3. **Consider your budget** - Free users should monitor AI usage to control costs
4. **Upgrade for heavy use** - Paid subscription is more cost-effective for regular AI usage

---

## 🛡️ Legal & Compliance

This actor extracts **publicly available** information from websites. All extracted data is information that is accessible through normal web browsing.

**Important:** Please ensure your use complies with:
- Website Terms of Service
- Applicable copyright laws
- Data protection regulations (GDPR, CCPA, etc.)
- Your specific jurisdiction's laws
- Robots.txt directives

**Responsibility:** Users are responsible for how they use extracted data. This tool should be used ethically and legally.

---

## ❓ Frequently Asked Questions

### Q: Why does the free tier charge for AI?
A: AI processing requires significant computational resources. We offer two options: pay-per-use for free accounts (flexible, try before you buy) or included in paid subscriptions (better value for regular use).

### Q: What's the difference between free and paid AI models?
A: Paid users get access to our most advanced AI model with superior accuracy and understanding of complex instructions. Free users get a simpler model that works great for straightforward tasks but charges per use.

### Q: How much does AI cost on the free tier?
A: AI requests are charged to your Apify account per use. The exact cost depends on Apify's current pricing. Check your Apify billing for details.

### Q: When should I upgrade to a paid subscription?
A: Upgrade if you:
- Use AI extraction regularly (more cost-effective)
- Need the highest AI accuracy for complex tasks
- Want predictable costs without per-request billing
- Require advanced understanding of nuanced instructions

### Q: Can I extract data from any website?
A: You can extract from any publicly accessible website, but always respect Terms of Service and robots.txt directives.

### Q: What happens if AI extraction fails?
A: The actor automatically falls back to basic extraction, so you always get contact data even if AI processing fails.

### Q: Can I process multiple URLs at once?
A: Yes! Provide multiple URLs in the `startUrls` array for batch processing.

### Q: Why does the actor always use Browser mode?
A: Browser mode ensures maximum reliability by fully rendering JavaScript, handling modern web applications, and capturing screenshots. It works on 99% of websites.

---

## 💬 Support & Contact

Need help or have questions? We're here for you:

- 📧 **Email:** [fridaytechnolog@gmail.com](mailto:fridaytechnolog@gmail.com)
- 🙋 **GitHub:** [DZ-ABDLHAKIM](https://github.com/DZ-ABDLHAKIM)
- 🦅 **Twitter:** [@DZ_45Omar](https://x.com/DZ_45Omar)
- 🔧 **Apify Profile:** [dz_omar](https://apify.com/dz_omar?fpr=smcx63)

---

## 🌟 Related Actors by [DZ_OMAR](https://apify.com/dz_omar?fpr=smcx63)

### 🎬 Video & Media Tools

**[YouTube Transcript & Metadata Extractor](https://apify.com/dz_omar/youtube-transcript-metadata?fpr=smcx63)**
Extract complete video transcripts with timestamps and comprehensive metadata. Perfect for content analysis, SEO, and subtitle generation.

**[YouTube Full Channel, Playlists, Shorts, Live](https://apify.com/dz_omar/Youtube-Scraper-Pro?fpr=smcx63)**
Extract complete playlist information with all video details from any YouTube playlist. Fast, reliable, and built for scale.

**[Zoom Scraper | 🎥 Downloader & 📄 Transcript](https://apify.com/dz_omar/zoom-scraper?fpr=smcx63)**
Extract Zoom meeting recordings, transcripts, and metadata. Ideal for meeting analysis and documentation.

**[Loom Scraper | 🎥 Downloader & 📄 Transcript](https://apify.com/dz_omar/loom-video-scraper?fpr=smcx63)**
Download Loom videos and extract transcripts. Perfect for training content and video documentation.

### 🏠 Real Estate Data

**[Idealista Scraper API](https://apify.com/dz_omar/idealista-scraper-api?fpr=smcx63)**
Advanced Idealista property data extraction with API access. Get listings, prices, and detailed property information.

**[Idealista Scraper](https://apify.com/dz_omar/idealista-scraper?fpr=smcx63)**
Extract Spanish real estate listings from Idealista. Perfect for market analysis and property research.

### 🛠️ Developer & Security Tools

**[Screenshot](https://apify.com/dz_omar/screenshot?fpr=smcx63)**
Fast, reliable webpage screenshots with customizable options. Essential for monitoring and documentation.

**[Ultimate Screenshot](https://apify.com/dz_omar/ultimate-screenshot?fpr=smcx63)**
Advanced screenshot tool with full-page capture, custom viewports, and quality controls.

**[Network Security Scanner](https://apify.com/dz_omar/network-security-scanner?fpr=smcx63)**
Scan websites for security vulnerabilities and get comprehensive security reports.

### 📱 Social Media Tools

**[Facebook Ads Scraper Pro](https://apify.com/dz_omar/facebook-ads-scraper-pro?fpr=smcx63)**
Extract Facebook ads data for competitor analysis and market research. Track ad campaigns and strategies.

---

## 📄 License

This actor is provided as-is for use on the Apify platform. Use responsibly and in accordance with applicable laws and website terms of service.

---

**Ready to extract any data from any website?** [Start using AI Contact Intelligence Extractor now!](https://apify.com/dz_omar/ai-contact-intelligence?fpr=smcx63)
