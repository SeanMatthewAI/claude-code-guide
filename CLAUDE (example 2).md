# Productivity Coach Web App - Simple Guide

## Overview
Build a minimalist AI-powered productivity coach with a glass morphism design that synthesizes insights from 15 productivity books.

## Tech Stack
- **React 18** + TypeScript + Vite
- **Tailwind CSS** for styling
- **Framer Motion** for animations
- **Gemini 2.5 Pro** for AI responses

## Key Features
1. **Chat Interface** - Clean conversation UI with glass effects
2. **Knowledge Base** - Content from 15 productivity books
3. **AI Coach** - Personalized advice using book insights
4. **Mobile Responsive** - Works great on all devices

## Quick Setup

### 1. Install Dependencies
```bash
npm create vite@latest productivity-coach -- --template react-ts
cd productivity-coach
npm install tailwindcss framer-motion lucide-react react-markdown @google/genai
```

### 2. Environment Setup
Create `.env.local`:
```
GEMINI_API_KEY=your_gemini_api_key_here
```

### 3. File Structure
```
src/
├── components/
│   ├── ui/           # Glass UI components
│   ├── chat/         # Chat interface
│   └── landing/      # Landing page
├── hooks/            # React hooks
├── utils/            # AI integration
├── knowledge/        # .md book files
└── types/           # TypeScript types
```

## Core Components

### Glass UI System
```typescript
// Glass effect utility classes
.glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}
```

### AI Integration
```typescript
// Simple AI hook
export function useProductivityChat() {
  const [messages, setMessages] = useState([]);
  const [isLoading, setIsLoading] = useState(false);
  
  const sendMessage = async (content: string) => {
    // Send to /api/chat endpoint
    // Get AI response with full knowledge base
  };
  
  return { messages, sendMessage, isLoading };
}
```

### Knowledge Base Strategy
**Simple Approach**: Bundle all 15 book .md files and send complete context to Gemini 2.5 Pro. Let the AI do intelligent synthesis across books.

## Design Principles

### Visual Style
- Dark purple gradient background
- Glass morphism effects throughout
- White/translucent text
- Smooth animations
- Mobile-first responsive

### User Experience
- Simple two-page app (Landing + Chat)
- Real-time streaming responses
- Conversation persistence
- Markdown formatting support

## Deployment

### Vercel (Recommended)
1. Create `/api/chat.ts` serverless function
2. Add `GEMINI_API_KEY` to environment variables
3. Deploy with `vercel --prod`

### Security
- API keys only in serverless functions
- Never expose keys in client code
- Use CORS protection

## The 15 Books
- Atomic Habits (James Clear)
- Clear Thinking (Shane Parrish)
- Deep Work (Cal Newport)
- Discipline Equals Freedom (Jocko Willink)
- Effortless (Greg McKeown)
- Essentialism (Greg McKeown)
- Feel-Good Productivity (Ali Abdaal)
- Four Thousand Weeks (Oliver Burkeman)
- Hyperfocus (Chris Bailey)
- Indistractable (Nir Eyal)
- Off the Clock (Laura Vanderkam)
- Solving the Procrastination Puzzle (Timothy Pychyl)
- The Almanack of Naval Ravikant
- The Power of Habit (Charles Duhigg)
- Thinking, Fast and Slow (Daniel Kahneman)

## Success Metrics
- Fast load times (<3s)
- Beautiful glass aesthetic
- Intelligent AI responses grounded in books
- Smooth mobile experience
- Conversation persistence

## Development Status
✅ Complete UI with glass morphism  
✅ Chat interface with streaming  
✅ Knowledge base integration  
✅ Gemini API integration  
✅ Markdown response formatting  
✅ Mobile responsive design  
✅ New chat functionality  

## Next Steps
1. Add your Gemini API key to `.env.local`
2. Test with `npm run dev`
3. Deploy to Vercel
4. Optional: Add conversation memory, smart suggestions, progress tracking

The app provides intelligent productivity coaching by synthesizing insights from world-class books through a beautiful, modern interface.