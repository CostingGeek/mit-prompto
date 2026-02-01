# Prompto - AI Prompt Pricing Guide

A modern web application that helps business users estimate the cost of AI API calls based on input and output tokens across different providers.

![Prompto](https://img.shields.io/badge/Next.js-15-black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-3-38bdf8)

## Features

### 📝 Page 1: Prompt Input
- Enter custom prompts or select from predefined use cases:
  - Customer Support Chatbot
  - Document Summarization
  - Complex Analysis / Reasoning
  - High-Volume Classification
  - Enterprise RAG
  - Research/Scientific
- Specify expected number of API calls
- Real-time validation

### 🔢 Page 2: Token Analysis
- Automatic token counting via Claude Sonnet 4.5 API
- Display input and output token counts
- Show recommended most cost-effective model
- Calculate estimated cost per request and total cost

### 📊 Page 3: Pricing Table
- Comprehensive comparison of 46+ AI models from:
  - OpenAI (GPT-5, GPT-4.1, GPT-4o, o1, o3-mini)
  - Anthropic (Claude Opus 4.5, Sonnet 4.5, Haiku 4.5)
  - Google (Gemini 3 Pro, Gemini 2.5 Flash)
  - Mistral AI (Large 3, Medium 3, Small)
  - Cohere (Command R+, Command R)
  - xAI Grok (Grok 4, Grok 4.1 Fast)
  - DeepSeek (V3.2, R1 Reasoner)
  - Meta Llama (Llama 4 Maverick, Llama 4 Scout)
  - Amazon Bedrock (Nova Pro, Nova Lite)
- Sortable columns (provider, model, input/output pricing, context window, estimated cost)
- Filter by provider and cost tier
- Highlighted recommended model

## Tech Stack

- **Framework**: Next.js 15 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **API Integration**: Anthropic Claude SDK
- **Color Scheme**: MIT Red (#750014) and Silver Gray (#8b959e)

## Prerequisites

- Node.js 18+ installed
- Anthropic API key (get one from [console.anthropic.com](https://console.anthropic.com/))

## Installation

1. **Clone or extract the project**
```bash
cd prompto-app
```

2. **Install dependencies**
```bash
npm install
```

3. **Configure environment variables**
```bash
cp .env.example .env
```

Edit `.env` and add your Anthropic API key:
```
ANTHROPIC_API_KEY=your_actual_api_key_here
```

4. **Run the development server**
```bash
npm run dev
```

5. **Open your browser**
Navigate to [http://localhost:3000](http://localhost:3000)

## Usage

### Step 1: Enter a Prompt
- Type your own custom prompt, or
- Select a sample prompt from the dropdown menu
- Adjust the number of expected API calls

### Step 2: Analyze Tokens
- Click "Analyze Prompt"
- The app calls Claude Sonnet 4.5 to process your prompt
- View input/output token counts
- See the recommended most cost-effective model

### Step 3: Compare Pricing
- Navigate to the Pricing Table tab
- Sort by any column to find the best option for your needs
- Filter by provider or cost tier
- See estimated costs for your specific prompt across all models

## Project Structure

```
prompto-app/
├── app/
│   ├── api/
│   │   └── count-tokens/
│   │       └── route.ts          # API endpoint for Claude token counting
│   ├── globals.css               # Global styles
│   ├── layout.tsx                # Root layout
│   └── page.tsx                  # Main application (all 3 pages)
├── components/                   # React components (if needed)
├── data/
│   └── pricing.json              # Pricing data for all AI models
├── lib/
│   ├── types.ts                  # TypeScript type definitions
│   └── samplePrompts.ts          # Predefined prompt examples
├── public/                       # Static assets
├── .env.example                  # Environment variables template
├── next.config.js                # Next.js configuration
├── package.json                  # Dependencies
├── tailwind.config.ts            # Tailwind CSS configuration
└── tsconfig.json                 # TypeScript configuration
```

## API Endpoint

### POST /api/count-tokens

Analyzes a prompt and returns token counts.

**Request:**
```json
{
  "prompt": "Your prompt text here"
}
```

**Response:**
```json
{
  "inputTokens": 42,
  "outputTokens": 156,
  "response": "Claude's response text"
}
```

## Responsive Design

The application is fully responsive and works on:
- 📱 Mobile phones (320px+)
- 📱 Tablets (768px+)
- 💻 Desktops (1024px+)
- 🖥️ Large screens (1440px+)

## Build for Production

```bash
npm run build
npm start
```

## Deployment

This Next.js app can be deployed to:
- **Vercel** (recommended, zero-config)
- **Netlify**
- **AWS Amplify**
- **Docker** (using the standalone output)

### Deploy to Vercel

```bash
npm install -g vercel
vercel
```

Make sure to add your `ANTHROPIC_API_KEY` in the Vercel environment variables.

## Customization

### Adding New Models

Edit `data/pricing.json` and add entries:
```json
{
  "provider": "Provider Name",
  "model": "Model Name",
  "inputPrice": 1.50,
  "outputPrice": 5.00,
  "contextWindow": "128K",
  "bestUseCase": "Description",
  "costTier": "Budget|Mid|Premium"
}
```

### Changing Colors

Edit `tailwind.config.ts`:
```typescript
colors: {
  'mit-red': '#750014',      // Primary color
  'silver-gray': '#8b959e',  // Secondary color
}
```

### Adding Sample Prompts

Edit `lib/samplePrompts.ts` and add new entries to the `samplePrompts` object.

## Troubleshooting

### "ANTHROPIC_API_KEY not configured" error
- Make sure you've created a `.env` file
- Verify the API key is correct
- Restart the development server after adding the key

### Token counting fails
- Check your internet connection
- Verify your Anthropic API key is valid and has credits
- Check the browser console for detailed error messages

### Styling issues
- Clear your browser cache
- Make sure Tailwind CSS is properly configured
- Run `npm install` to ensure all dependencies are installed

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Support

For issues or questions:
1. Check the troubleshooting section above
2. Review the [Next.js documentation](https://nextjs.org/docs)
3. Check [Anthropic API documentation](https://docs.anthropic.com/)

## Acknowledgments

- Built with [Next.js](https://nextjs.org/)
- Styled with [Tailwind CSS](https://tailwindcss.com/)
- Powered by [Anthropic Claude API](https://anthropic.com/)
- Pricing data accurate as of January 2026
