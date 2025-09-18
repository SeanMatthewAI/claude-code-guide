# PLANNING.md - Productivity Coach Web App
*Strategic Vision and Architecture Document*

## Project Vision

### Core Mission
Create an AI-powered productivity coach that democratizes access to world-class productivity wisdom by synthesizing insights from 15 influential productivity books into personalized, actionable guidance through a beautiful, minimalist chat interface.

### Value Proposition
- **Unique Knowledge Base**: Personal notes from 15 curated productivity books, not generic advice
- **Intelligent Synthesis**: AI discovers connections across different authors and methodologies
- **Beautiful UX**: Liquid glass aesthetic with Apple-inspired design language
- **Instant Access**: No complex setup - start chatting immediately
- **Cross-Book Insights**: Reveals relationships between concepts from different sources

## Target Users & Personas

### Primary Users
1. **Knowledge Workers** (25-45) - Need focus and time management strategies
2. **Entrepreneurs** (28-50) - Want to maximize productivity and decision-making
3. **Students** (18-30) - Seeking better study habits and academic performance
4. **Self-Improvement Enthusiasts** (22-55) - Committed to personal optimization

### Key User Needs
- Overwhelmed by productivity advice - need synthesis
- Want actionable strategies, not abstract concepts
- Prefer conversational learning over reading lengthy books
- Need encouragement and practical next steps
- Want to discover connections between different productivity approaches

## Technical Architecture

### High-Level Architecture
```
User Browser
    ↓
React App (Client-Side)
    ↓
Serverless API Functions (/api/chat)
    ↓
Gemini 2.5 Pro API
```

### Core Components
1. **Knowledge Base Loader**: Bundles all .md files into React app at build time
2. **Chat Interface**: Glass morphism UI with message history and input
3. **AI Integration**: Secure serverless functions proxy requests to Gemini 2.5 Pro
4. **State Management**: React hooks for conversation state and persistence

### Data Flow
1. User sends message via chat interface
2. React app loads complete knowledge base (all 15 books)
3. Constructs full-context prompt with system instructions + knowledge base + user query
4. Sends to secure API endpoint
5. Serverless function forwards to Gemini 2.5 Pro
6. AI response returned through the chain back to user

## Technology Stack

### Frontend Framework
- **React 18+** with TypeScript
- **Vite** for fast development and building
- **Tailwind CSS** for styling and glass morphism effects
- **Framer Motion** for smooth animations and micro-interactions

### AI Integration
- **Primary**: Google Gemini 2.5 Pro (2M+ token context window)
- **Fallback**: OpenAI GPT-4 for backup/comparison
- **Security**: Serverless functions to protect API keys

### Deployment & Hosting
- **Vercel** (recommended) - excellent React support + serverless functions
- **Alternative**: Netlify with Netlify Functions
- **Domain**: Custom domain for professional appearance

### Development Tools
- **Claude Code** for initial development and iteration
- **Git** for version control
- **ESLint + Prettier** for code quality
- **TypeScript** for type safety

## Key Technical Decisions

### Knowledge Integration Strategy
**Decision**: Bundle all .md files directly into React app, include full context in each AI request
**Rationale**: 
- Gemini 2.5 Pro can handle 2M+ tokens easily
- Simpler than RAG/vector search
- No information loss from filtering
- Better cross-book synthesis
- Faster development

### API Security Approach
**Decision**: Use serverless functions to proxy AI API calls
**Rationale**:
- Keeps API keys secure server-side
- Prevents client-side exposure
- Easy to implement with Vercel/Netlify
- Scalable and cost-effective

### UI Design Philosophy
**Decision**: Liquid glass aesthetic with minimal, Apple-inspired design
**Rationale**:
- Modern, premium feel
- Differentiates from generic chat interfaces
- Aligns with high-quality content
- Appeals to target demographic

## Constraints & Considerations

### Technical Constraints
- **Context Window**: Even with 2M tokens, need to monitor total prompt size
- **API Costs**: Gemini calls with large context will have higher costs
- **Bundle Size**: 15 .md files will increase initial load time
- **Rate Limits**: Need to implement client-side rate limiting

### Business Constraints
- **MVP Timeline**: 2-3 weeks for core functionality
- **Budget**: Minimal - leveraging free tiers where possible
- **Scope**: Focus on core chat experience, defer advanced features

### UX Constraints
- **Mobile-First**: Must work excellently on mobile devices
- **Accessibility**: WCAG 2.1 AA compliance required
- **Performance**: Fast load times despite large knowledge base
- **Offline**: Graceful degradation when API unavailable

## Success Metrics

### User Engagement
- **Session Duration**: Target 5+ minutes average
- **Message Exchanges**: Target 8+ messages per conversation
- **Return Visits**: 25%+ users return within 7 days
- **Conversation Depth**: Users ask follow-up questions

### Product Quality
- **Response Relevance**: 90%+ helpful responses (user feedback)
- **Cross-Book Citations**: AI references multiple books per response
- **Response Time**: <3 seconds average API response
- **Error Rate**: <2% API failures

### Technical Performance
- **Page Load**: <3 seconds initial load
- **Core Web Vitals**: All metrics in "Good" range
- **Mobile Experience**: Excellent responsiveness and touch interactions
- **Accessibility**: No critical accessibility issues

## Knowledge Base Content

### Book Sources (15 Total)
1. **Atomic Habits** - James Clear (habit formation, systems)
2. **Clear Thinking** - Shane Parrish (decision-making, mental models)
3. **Deep Work** - Cal Newport (focus, attention management)
4. **Discipline Equals Freedom** - Jocko Willink (military mindset, routine)
5. **Effortless** - Greg McKeown (simplification, automation)
6. **Essentialism** - Greg McKeown (priority, saying no)
7. **Feel-Good Productivity** - Ali Abdaal (sustainable productivity)
8. **Four Thousand Weeks** - Oliver Burkeman (time perspective, mortality)
9. **Hyperfocus** - Chris Bailey (attention management, flow)
10. **Indistractable** - Nir Eyal (distraction management)
11. **Off the Clock** - Laura Vanderkam (time perception, scheduling)
12. **Solving the Procrastination Puzzle** - Timothy Pychyl (procrastination psychology)
13. **The Almanack of Naval Ravikant** - (wealth, happiness, decision-making)
14. **The Power of Habit** - Charles Duhigg (habit loops, behavioral change)
15. **Thinking, Fast and Slow** - Daniel Kahneman (cognitive biases, decision-making)

### Content Strategy
- **Personal Notes**: Use actual personal notes/highlights, not book summaries
- **Synthesis Focus**: AI trained to connect concepts across books
- **Actionable Emphasis**: Prioritize practical techniques over theory
- **Source Attribution**: Always cite specific books/authors

## Risk Assessment

### Technical Risks
- **API Dependencies**: Gemini API changes or outages
- **Context Limits**: Hitting token limits with large knowledge base
- **Performance**: Slow responses with full-context prompts
- **Mitigation**: Fallback APIs, prompt optimization, caching

### Product Risks
- **User Adoption**: Hard to discover without marketing
- **Content Quality**: AI responses not helpful or relevant
- **Competition**: Other AI productivity tools
- **Mitigation**: Focus on unique knowledge base, excellent UX

### Business Risks
- **API Costs**: Expensive with high usage
- **Legal**: Copyright concerns with book content
- **Scaling**: Infrastructure costs with growth
- **Mitigation**: Usage monitoring, fair use guidelines, gradual scaling

## Future Vision

### Phase 1: MVP (2-3 weeks)
- Core chat interface with glass aesthetic
- Full knowledge base integration
- Basic conversation persistence
- Mobile-responsive design

### Phase 2: Enhanced Experience (1-2 weeks)
- Conversation history across sessions
- Smart query suggestions
- Book-specific deep dives
- Performance optimizations

### Phase 3: Advanced Features (Future)
- User accounts and profiles
- Personalized learning paths
- Integration with productivity tools
- Community features and sharing

### Long-Term Vision
Transform from simple chat interface into comprehensive productivity ecosystem that helps users discover, implement, and track productivity strategies based on world-class research and methodology.