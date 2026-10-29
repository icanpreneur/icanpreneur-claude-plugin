# Icanpreneur

Talk to your evidence-backed Buyer Persona from Claude. Icanpreneur is an AI co-founder platform that builds Buyer Personas from customer interviews (real, imported or AI-simulated), so product and go-to-market decisions rest on what customers actually said.

This plugin connects Claude to the Icanpreneur remote MCP server. It contains configuration only: no scripts, no local code and no third-party packages.

## What you can do

- Ask your Buyer Persona to review messaging, test pricing or react to product ideas
- Run AI-simulated interviews, run interviews with IVA (our AI interviewer), or import interviews you already have
- Generate positioning and messaging, landing pages and sales decks
- Manage ideas, research, interview scripts, notes, contacts and canvases in your workspace
- Trace every research insight back to its source interview. Real and simulated sources are clearly labeled, and simulated responses are never real customer evidence.

## Requirements

- An Icanpreneur account. Sign up at https://platform.icanpreneur.com/login?returnUrl=%2F&intent=register
- New accounts start with a 7-day trial and a one-time allowance of AI credits. AI features (simulated interviews, generation, persona chat) use credits. When the trial or credits run out, those features need a paid plan.
- No other accounts are needed.

## Setup

1. Add the plugin in Claude.
2. When prompted, connect to Icanpreneur and sign in with your Icanpreneur account (OAuth).
3. Approve access. You can disconnect at any time from Claude's connector settings.

MCP server: https://platform.icanpreneur.com/api/mcp

## Example prompts

- Review my landing page as my Buyer Persona. Which claims lack interview support?
- We're moving to $49 a month. How would my Buyer Persona react, and why?
- Build a Buyer Persona from my interview transcripts, with each insight linked to its source.

## Data handling

- The plugin reads and stores data in your own Icanpreneur account: ideas, research, interview scripts, transcripts, contacts, Buyer Personas, notes and generated documents. This can include personal data about interviewees and contacts. You are responsible for having a lawful basis to submit that data.
- Content created or updated through Claude is saved as ordinary Icanpreneur workspace content. Icanpreneur does not keep a separate archive of MCP requests and responses.
- Some actions create, edit, delete or restore content in your workspace, and generation actions consume credits. Claude acts only within your own access rights and the permissions you grant.
- AI features are processed by contracted AI service providers under enterprise/API terms. Icanpreneur does not use your input or output to train its own models. Processing may occur outside the EEA, including in the United States, under appropriate safeguards.
- The plugin sends data only to the Icanpreneur MCP server. It does not send data to any other service.
- Content returned to Claude is then handled under Anthropic's terms and your Claude settings, not Icanpreneur's.
- The platform is for users aged 18 and over.

Legal documents:

- Privacy Policy: https://platform.icanpreneur.com/legal/privacy-policy
- Terms of Use: https://platform.icanpreneur.com/legal/terms-of-use
- Data Processing Agreement: https://platform.icanpreneur.com/legal/data-processing-agreement

## Support

support@icanpreneur.com

## License

MIT. See the LICENSE file. Use of the Icanpreneur platform and MCP server is governed separately by the Terms of Use above.
