# C — How AI Affects Gaming (and can you use AI as a catalyst?)

Research brief for Telugu tech explainer "How big will the gaming industry be?" — final section.
Researched: 2026-11-22. Web search only (WebFetch blocked), 29 searches. Numbers come from search-result snippets of the cited pages.

**Labels:** [V] = verified (primary source, or 2+ major outlets agree) · [S] = single/secondary source or company self-claim · [U] = unverified, conflicting or weak source. Use [U] items only with hedging ("reportedly").

Already known (not re-researched): GDC Nov 2026: 40% of game professionals use GenAI at work, 55% think it hurts the industry; Roblox creators earned $1B+ by Sep 2025, median creator ~$1,440.

---

## 1. AI in DEVELOPMENT: tools, real usage, company bets

### Adoption surveys
- **87% of game developers use AI agents, 90% use some form of AI in their workflow, and 94% expect AI to cut development costs in the long run.** Harris Poll for Google Cloud: 615 developers in the US, South Korea, Finland, Norway and Sweden, surveyed June 20 to July 9, 2025. 63% were worried about data ownership. [V]
  - https://www.googlecloudpresscorner.com/2025-08-18-90-of-Games-Developers-Already-Using-AI-in-Workflows,-According-to-New-Google-Cloud-Research (Aug 18, 2025)
  - https://www.pcgamer.com/software/ai/87-percent-of-game-developers-are-already-using-ai-agents-and-over-a-third-use-ai-for-creative-elements-like-level-design-and-dialogue-according-to-a-new-google-survey
  - Caveat: the survey was commissioned by a vendor (Google), and the GDC Nov 2026 figure of 40% is much lower. Different samples and definitions ("use AI agents" vs "use GenAI at work"). Say so on screen.

### Engines and platforms
- **Unity AI (beta, May 6, 2026):** an in-editor Assistant with Ask, Plan and Agent modes. Agent mode edits the scene directly. Unity also ships "Generators" for placeholder assets, an "AI Gateway" for bringing in third-party agents (Claude, Codex, Gemini) and an official Unity MCP server. The beta is open to all Unity 6 developers. Muse appears to have been folded into this suite [U on the Muse part]. [V]
  - https://unity.com/en/blog/unity-ai-assistant-ask-plan-agent-mode-explained (May 6, 2026)
  - https://unity.com/resources/what-is-unity-ai (Apr 2026)
- **Roblox Cube:** announced March 2025 as Roblox's "core generative AI system for 3D and 4D". Cube 3D was open-sourced. "4D" means generated objects that are interactive and functional. **4D Generation went to open beta for all creators in Feb 2026** (GenerateModelAsync API; prompts pass brand/IP filters). **In April 2026** the Roblox Studio Assistant gained agentic features (planning mode, procedural model generation, self-correcting test loops) and integrations with Claude, Cursor and Codex. [V]
  - https://about.roblox.com/newsroom/2025/03/introducing-roblox-cube (Mar 2025)
  - https://about.roblox.com/newsroom/2026/02/accelerating-creation-powered-roblox-cube-foundation-model (Feb 2026)
  - https://devforum.roblox.com/t/beta-4d-generation-unlock-new-types-of-gameplay/4331818
  - https://thenextweb.com/news/roblox-ai-assistant-agentic-tools-planning-procedural-models (Apr 16, 2026)
- **Epic / Fortnite / Unreal:** AI Darth Vader appeared in Fortnite in May 2025. Dialogue came from Gemini 2.0 Flash and the voice from ElevenLabs Flash v2.5, modelled on James Earl Jones with his estate's approval. Players quickly got it to swear and Epic hotfixed it. SAG-AFTRA filed an unfair labor practice charge over it. [V]
  - Epic's "Persona Device" was announced at State of Unreal 2025 (June 2025). It shipped as the experimental UEFN feature "Conversations" in v40.20 (reported Apr 16, 2026), letting creators build AI NPCs with unscripted voice dialogue. [S] Reports disagree on whether it uses Gemini 1.5 or Gemini 3.1 Flash Lite. [U]
  - https://kotaku.com/fortnite-darth-vader-ai-npc-epic-disney-1851783545
  - https://www.fortnite.com/news/state-of-unreal-2025-highlights-for-fortnite-creators
  - https://wccftech.com/fortnite-uefn-ai-npc-conversations-gemini-elevenlabs/
  - No details found on "Unreal Engine 6 AI features"; only headlines say UE6 "embraces AI". [U]

### AI 3D-asset startups (company claims)
- **Meshy:** reported 10M+ users and 100M+ 3D models generated (GDC, March 2026); 12M+ users by July 2026. [S, company claims] Reported ARR above $100M in Sept 2026. [U, aggregator only] An earlier press release claimed $15M ARR with 30% month-on-month growth. [S]
  - https://welcome.informaengage.com/welcome2026/gdc-festival-of-gaming-2026/what-is-the-best-genai-3d-tool-evaluating-meshys-10-million-creators-milestone-at-gdc-2026/
  - https://technode.global/prnasia/meshy-hits-15m-arr-with-30-month-over-month-growth-unveils-meshy-6-preview-for-next-gen-3d-creation/
- **Tripo AI (China-founded):** "3M+ professional users, 40,000+ studios/partners", and more than 85% of users are outside China. [S] Higher figures (6.5M creators) come only from tool directories. [U]
  - https://www.scmp.com/tech/tech-trends/article/3338202/china-founded-tripo-ai-updates-3d-content-creation-platform-users-more-double
- Not researched (no budget left): AI motion capture from video (Move.ai and similar) and AI voice tools beyond ElevenLabs. Don't cite specific numbers for these.

### Company strategies
- **Krafton (publisher of PUBG and BGMI, the India hook) declared itself an "AI First" company in October 2025.** It will spend about **100 billion won (~$70M) on a GPU cluster** and set aside **about 30 billion won a year from 2026** for staff AI tools. The CEO, Kim Chang-han, framed the move around agentic-AI automation. In January 2026, NHN Cloud was picked to run the cluster: **1,000+ NVIDIA Blackwell Ultra (B300) GPUs**, with full operation targeted for July 2026. Staff raised concerns about the HR restructuring. [V]
  - https://www.pcgamer.com/software/ai/krafton-is-now-an-ai-first-company-will-spend-usd70-million-on-a-gpu-cluster-to-serve-as-the-foundation-for-accelerating-the-implementation-of-agentic-ai (Oct 2025)
  - https://www.asiae.co.kr/en/article/2025102311585579811 (Oct 23, 2025)
  - https://www.asiae.co.kr/en/article/2026011909511400121 (Jan 19, 2026)
- **Square Enix wants generative AI to handle 70% of QA and debugging by the end of 2027.** The goal is in its business plan (Nov 2025) and runs as a joint project with the University of Tokyo. It came alongside layoffs in Western offices; the company did not link the two. [V]
  - https://www.videogameschronicle.com/news/square-enix-says-it-wants-generative-ai-to-be-doing-70-of-its-qa-and-debugging-by-the-end-of-2027/ (Nov 2025)
- **EA:** CEO Andrew Wilson on the Q4 FY25 call (May 2025) said AI is "powering our future" and is already used in design, animation and storytelling. That came alongside reported layoffs of 300+ people. [S] EA's FY26 compensation disclosure mentions strategic AI partnerships and a "GenAI investment framework". [S] EA held no Q4 FY26 call because of its pending take-private deal. [V] FY26 net revenue was $7.531B. [V]
  - https://www.gamesradar.com/games/after-reportedly-laying-off-more-than-300-people-ea-ceo-says-ai-is-powering-our-future-and-is-already-being-used-in-design-animation-and-storytelling
  - https://s204.q4cdn.com/701424631/files/doc_financials/2026/q4/Q4-FY26-Earnings-Release_FINAL.pdf
  - Do NOT quote "the very core of our business" as Wilson's words. That is GamesRadar's paraphrase. [U]
- **Ubisoft:** showed the Neo NPC prototype at GDC 2024. On **Nov 21, 2025** it revealed **"Teammates"**, its first playable GenAI research project: an FPS in which voice-commanded AI squadmates (Pablo, Sofia) and an AI assistant (Jaspar) take spoken orders and chat. It was closed-playtested with "a few hundred players". The writers set personality "boundaries" instead of scripted lines. No release date. [V]
  - https://news.ubisoft.com/en-us/article/3mWlITIuWuu0MoVuR6o8ps/ubisoft-reveals-teammates-an-ai-experiment-to-change-the-game (Nov 21, 2025)
- **King (Candy Crush, owned by Microsoft):** in July 2025 it cut about 200 jobs during the Xbox layoffs. Staff reported that **some laid-off level-design and writing teams were replaced by the AI tools they had built.** [S] The original report is Mobilegamer.biz, repeated by Engadget and others.
  - https://www.engadget.com/gaming/laid-off-candy-crush-studio-staff-reportedly-replaced-by-the-ai-tools-they-helped-build-174141524.html (Jul 2025)

### World models (AI that "dreams" gameplay)
- **Microsoft Muse (WHAM):** published in *Nature* in Feb 2025 (vol 638, pp. 656–663). Built with Ninja Theory and trained on **1B+ images and controller actions from *Bleeding Edge*, about 7+ years of continuous human play**. It is pitched as a tool for gameplay ideation; the weights are on Azure AI Foundry. A real-time version, WHAM-RT/WHAMM, runs as a Copilot Labs tech demo. [V]
  - https://www.microsoft.com/en-us/research/blog/introducing-muse-our-first-generative-ai-model-designed-for-gameplay-ideation/ (Feb 2025)
- **Google DeepMind Genie 3:** announced Aug 2025 as a real-time interactive world model. **Project Genie** opened to US Google AI Ultra subscribers on **Jan 29, 2026**. Generations are capped at 60 seconds and reported at 720p/24fps. Google itself says Genie "is not a game engine and can't create a full game experience." [V]
  - https://blog.google/innovation-and-ai/models-and-research/google-deepmind/project-genie/ (Jan 29, 2026)
  - https://techcrunch.com/2026/01/29/i-built-marshmallow-castles-in-googles-new-ai-world-generator-project-genie
- **Market shock on Jan 30, 2026:** after Project Genie launched, **Unity closed down 24%, its worst day since 2022. Roblox fell 13%, CD Projekt 8.7% and Take-Two 7.9%.** [V] (Bloomberg; intraday figures in other outlets differ slightly)
  - https://www.bloomberg.com/news/articles/2026-01-30/unity-video-game-stocks-fall-as-google-s-ai-tool-genie-sparks-fears
- **Genie 4** was announced in late October 2026: native audio, simulated people who talk back, and possibly mid-session scene edits. It is going to trusted testers first, then Ultra subscribers and the API "soon". [S/U] I could not confirm this on Google's own blog; only secondary coverage.
  - https://technews.tw/2026/10/28/google-deepmind-announces-genie-4/
  - https://ppc.land/googles-genie-4-simulates-people-who-talk-back-in-real-time/

### Cost and time claims
- **Morgan Stanley (Apr 22, 2026): AI could cut video-game development costs by "nearly half", unlocking about $22B a year in profits** for game makers worldwide. The savings would come from environment creation, dialogue and testing, plus smaller teams and faster live updates; not every company benefits equally. [V]
  - https://www.morganstanley.com/insights/articles/ai-gaming-22-billion-industry-earning-potential-2026
  - https://www.thestar.com.my/tech/tech-news/2026/04/22/gaming-industry-could-unlock-22-billion-in-profits-on-ai-driven-cost-cuts---morgan-stanley
- **Bain (Gaming Report 2025):** AAA studios are "squeezed in the middle". Agentic AI may lower big studios' costs but also lowers barriers for small competitors. No percentage given. [S]
  - https://www.bain.com/insights/squeezed-in-the-middle-aaa-gaming-studios-must-adapt-gaming-report-2025/
- BCG notes that some vendors claim AI game-generation tools speed development by up to 90%. That is a vendor claim, so label it as hype. [S]
  - https://bcg.com/publications/2025/video-gaming-report-2026-next-era-of-growth

---

## 2. AI INSIDE GAMES (NPCs, companions, generated worlds)

- **NVIDIA ACE "co-playable characters":** announced at CES in Jan 2025 with Krafton, for PUBG, inZOI, NARAKA: Bladepoint and MIR5. **PUBG Ally** is an AI squadmate that understands voice commands and slang, shares loot, drives vehicles and fights. It ran as a public beta in PUBG Arcade Duos, June 17–30. [V on the features; U on the year, probably 2025]
  - https://www.nvidia.com/en-us/geforce/news/nvidia-ace-autonomous-ai-companions-pubg-naraka-bladepoint/
  - https://developer.nvidia.com/blog/how-krafton-built-pubg-ally-a-co-playable-character-powered-by-nvidia-ace/
- **inZOI (Krafton life sim):** **sold 1M copies in its first week of Steam Early Access** (launched Mar 28, cumulative by Apr 4, 2025), Krafton's fastest-selling title ever. **"Smart Zoi"** characters are driven by an on-device small language model (built with NVIDIA ACE) on GeForce RTX GPUs. [V] The model size (0.5B Mistral NeMo Minitron) and the RTX 3060 minimum come only from fan wikis. [U] Some hands-on previews found Smart Zoi underwhelming. [S]
  - https://press.krafton.com/KRAFTON-HITS-1-MILLION-SALES-OF-INZOI-IN-FIRST-WEEK-OF-EARLY-ACCESS-LA (Apr 2025)
  - https://www.pcgamer.com/games/life-sim/inzois-smart-zoi-ai-system-sounds-great-on-paper-but-seeing-it-in-a-live-demo-didnt-exactly-wow-me
- **Where Winds Meet (NetEase/Everstone, launched Nov 14, 2025):** about **2M players in its opening weekend and a Steam peak of ~190K**. Some NPCs are **LLM chatbots** that accept freeform text or voice. Players "socially engineered" chatbots into completing quests for them and did "obscene stuff" to them. The main story stays hand-written. [V]
  - https://www.gamesradar.com/games/action-rpg/open-world-action-rpg-where-winds-meet-tops-2-million-players-in-its-first-weekend-with-a-concurrent-peak-of-190-000-on-steam-alone-as-it-rakes-in-very-positive-reviews
  - https://kotaku.com/where-winds-meet-ai-npc-llm-chatgpt-steam-2000650074
- **Fortnite AI Darth Vader** (May 2025) and **UEFN "Conversations"** (Apr 2026): see Section 1. The first mass-market talking AI NPC.
- **Ubisoft Teammates** (Nov 2025): voice-controlled AI squad, research only. See Section 1.
- **AI Dungeon / Latitude:** not researched this round (budget). Mention only as "one of the earliest AI-text games (2019)" if needed. [U, from general knowledge, not checked]
- **2026 hit built heavily with AI?** None found. The big 2026 hits with AI in them (Arc Raiders, Crimson Desert) are studio games where AI was a minor part and drew criticism. No 2026 mega-hit is "AI-made". [V that none was found in searches]

---

## 3. STEAM AI-DISCLOSURE DATA and Valve policy

- **Valve's policy:** since **January 2024**, developers must disclose generative AI use on submission (pre-generated content, and live-generated content with guardrails). Disclosures show on store pages. **In January 2026, Valve rewrote the form** so it covers only AI content that players actually consume; behind-the-scenes "efficiency tools" such as code assistants are exempt. [V]
  - https://www.pcgamer.com/software/ai/steam-updates-ai-disclosure-form-to-specify-that-its-focused-on-ai-generated-content-that-is-consumed-by-players-not-efficiency-tools-used-behind-the-scenes/ (Jan 2026)
- **Ichiro Lambe / Totally Human Media (Steam API analysis):**
  - Disclosures grew from about 1,000 titles (Apr 2024) to **7,818 titles by July 2025, about 7% of the Steam library**. **About 1 in 5 games released in 2025** disclosed GenAI. 60% of disclosures were for visual assets. [V]
    - https://www.tomshardware.com/video-games/pc-gaming/1-in-5-steam-games-released-in-2025-use-generative-ai-up-nearly-700-percent-year-on-year-7-818-titles-disclose-genai-asset-usage-7-percent-of-entire-steam-library (Jul 2025)
    - https://www.videogameschronicle.com/news/steam-games-disclosing-generative-ai-use-are-up-800-this-year/
  - Later count: **10,258 games, about 8% of the library** (late 2025). [S]
  - GamesRadar: Steam games openly disclosing GenAI (including Call of Duty: Black Ops 6 and Stellaris) earned about **$660M in 2025**. [S]
    - https://www.gamesradar.com/games/steam-games-that-openly-use-generative-ai-earned-usd660-million-this-year-including-call-of-duty-black-ops-6-stellaris-and-more-as-studios-continue-to-rely-on-the-technology
- **2026 data (independent Reddit analyst u/ploz, reported Nov 2026):** analysed 63,596 games released Jan 2024 to Oct 2026. [S]
  - **49.9% of new Steam games released in October 2026 disclosed AI use**, up from **1.7% in Jan 2024**.
  - **40.1% of 2026 releases so far** disclosed AI, up from 13.2% for 2024 and 24% for 2025 releases.
  - AI is concentrated in small games: **47% of 2026 games with fewer than 10 reviews disclose AI, against 14% of games with 1,000+ reviews.**
  - 63% of 2026 disclosures cite AI-generated art.
  - https://dexerto.com/gaming/almost-half-of-all-new-steam-games-use-ai-now-3423933
  - https://www.pcgamer.com/gaming-industry/steam-week-in-review-take-cover-because-it-looks-like-more-than-half-of-steam-games-will-have-an-ai-disclosure-by-2027-2028/
  - https://www.gadgetreview.com/?p=425709
  - Caveat: the methods differ from Lambe's (yearly totals for 2024 and 2025 don't match his "1 in 5"), so don't mix the two series on one chart. Disclosures are self-reported, so the real share is a floor, and after Jan 2026 back-end AI is no longer counted.
- **Epic CEO Tim Sweeney vs Steam labels:** in 2025 he called them pointless ("nearly every game will use AI"). In late Oct 2026 he called Steam's policy "abhorrent" and a "political act" on X. [S]
  - https://www.tweaktown.com/news/114305/epic-games-ceo-tim-sweeney-cant-stop-going-after-steam-calls-its-ai-disclosure-policy-abhorrent/index.html (Oct 2026)

---

## 4. BACKLASH and RISK

- **SAG-AFTRA video game strike:** began July 26, 2024 (performers vs. major publishers, over AI). It ended when members **ratified the new Interactive Media Agreement by 95.04% to 4.96%**, announced July 9, 2025, after **about 11 months (320 days)**. The deal requires **consent and disclosure for AI digital replicas**, lets performers suspend consent for new AI output during a strike, and gives an immediate **pay rise of 15%+**, with further raises in Nov 2025, 2026 and 2027. [V]
  - https://www.thewrap.com/sag-aftra-ratify-interactive-media-agreement-video-game-strike/ (Jul 2025)
  - https://www.pocketgamer.biz/video-games-strike-ends-after-11-months-as-sag-aftra-ratifies-new-contract
- **Clair Obscur: Expedition 33:** won Game of the Year and Debut Game at the **Indie Game Awards on Dec 18, 2025. Both were rescinded on Dec 20** after Sandfall confirmed it had used GenAI for placeholder textures, which were later patched out. The IGA bans GenAI "at any point in development". The awards went to Blue Prince and Sorry We're Closed. [V]
  - https://www.pcgamer.com/games/rpg/indie-game-awards-pulls-two-awards-from-clair-obscur-over-generative-ai-use-we-have-a-hard-stance-against-gen-ai-in-videogames (Dec 2025)
- **Arc Raiders (Embark/Nexon):** used AI text-to-speech trained on paid actors' voices, which drew strong criticism (Eurogamer's review called it artistically compromising). **It still sold 14M copies by Feb 2026 and 16M+ by May 2026, with a peak of 960K concurrent players.** In March 2026 Embark said it had replaced many TTS lines with human recordings: "A real professional actor is better than AI, that's just how it is" (design director Virgil Watkins). [V]
  - https://www.gamesradar.com/games/third-person-shooter/arc-raiders-significantly-exceeded-expectations-with-14-million-copies-sold-and-almost-1-million-concurrent-players-last-month-and-its-publisher-expects-momentum-to-continue/ (Feb 2026)
  - https://wccftech.com/arc-raiders-16-million-sales-embark-new-games/ (May 2026)
  - https://www.pcgamer.com/games/third-person-shooter/embark-ceo-says-a-real-professional-actor-is-better-than-ai-after-the-studio-re-records-some-arc-raiders-dialog-with-real-humans (Mar 2026)
- **Crimson Desert (Pearl Abyss, March 2026):** **sold 2M copies on launch day**, but players found undisclosed AI-generated 2D props. Pearl Abyss apologised ("We should have clearly disclosed our use of AI"), started a full asset audit and promised replacements. [V] Reports that its stock fell ~30% that week [U] weren't checked against market data.
  - https://gameinformer.com/2026/03/23/crimson-desert-apologizes-for-using-ai-art-and-issues-first-big-patch (Mar 23, 2026)
  - https://www.pcgamer.com/games/rpg/crimson-desert-team-apologizes-after-players-find-ai-art-in-the-game-our-intention-has-always-been-for-any-such-assets-to-be-replaced
- **Jobs:** King replaced laid-off level designers and writers with AI tools (Jul 2025) [S]. Square Enix's 70% QA target came alongside Western layoffs [V]. EA's AI push came alongside 300+ reported layoffs [S]. Analysts expect cost cuts, i.e. smaller teams (Morgan Stanley) [V]. QA and 2D/3D art are the most exposed roles. That last point is an inference from the targets above, not a measured statistic.
- **Copyright:** the **US Copyright Office's Part 2 AI report (Jan 29, 2025)** says works generated entirely by AI are **not copyrightable**. Prompts alone are generally not enough; human selection, arrangement and modification can be protected case by case. [V] For game makers this means purely AI-made art or levels may not be legally "yours" to protect.
  - https://copyright.gov/newsnet/2025/1060.html (Jan 29, 2025)
- **Tool abuse and safety:** players made AI Vader swear (May 2025) and socially engineered the Where Winds Meet chatbots (Nov 2025). Live LLM NPCs carry brand-safety risk. [V]
- Not found or not verified: a Call of Duty Black Ops 7 AI-art backlash (my search returned nothing; don't use it without checking).

---

## 5. AI as a CATALYST for small teams and solo devs

### Examples
- **Pieter Levels' fly.pieter.com (Feb–Mar 2025):** a browser multiplayer flight sim. He **had never made a game**, and built the first working demo in **about 3 hours with Cursor and Three.js**. He self-reported **$87K MRR, a "$1M ARR run-rate in 17 days"**, from in-game ad blimps and billboards (~$5K/month each) and a $29.99 F-16 upgrade. [S, self-reported] Other sources say it later fell to about $12K MRR (May 2025) [S], and that his bio showed "$0/m" by mid-2026 [U]. Peak concurrent players are reported at both 17K and 26K. [U]
  - https://levels.io/full-multiplayer-python-websockets-game-ai
  - https://dev.to/promptway/he-built-a-flight-simulator-in-three-hours-and-hit-1m-a-year-in-17-days-then-it-went-to-zero-1b1l
  - https://404media.co/this-game-created-by-ai-vibe-coding-makes-50-000-a-month-yours-probably-wont
  - Lesson for the video: the win came as much from his **500K+ X following and distribution** as from AI. "ARR run-rate" is not money actually earned.
- **Reality check (Mobilegamer.biz, 2026): "Are the new wave of solo AI game-makers making any money? No, not really."** One game made with Claude earned about **$3K in total sales after thousands spent on tokens**. Another developer spent **$1,500 on AI tools for 1,000 downloads and $0 revenue**. [S]
  - https://mobilegamer.biz/are-the-new-wave-of-solo-ai-game-makers-making-any-money-no-not-really/
- **AI-built Steam launches:** CODEX MORTIS ("world's first 100% AI-developed game", Early Access) and Catvivors (a solo dev using Claude Code, Mar 2026). No meaningful sales reported. [S]
  - https://app.cinevva.com/signals/2026-03-23-solo-devs-shipping-not-vibing
- **Solo hits in 2026 with no AI claim:** Meccha Chameleon (3M+ copies, built in about 2 months) and Sledding Game (100K copies in 5 days). Coverage does not say they used AI, so **do NOT present these as AI successes.** [S]
- **Mid-size studio, with AI as an ingredient:** Embark (Arc Raiders) says TTS let it "keep the studio small" while shipping a big world. It is the clearest commercial example of AI as a scope multiplier, and also the clearest example of backlash. [V]
- **Roblox and UGC platforms** are the most realistic "AI-catalyst" route for beginners: free Cube/Assistant tools, a built-in audience, and $1B+ paid to creators (already known). The median creator earns only ~$1,440, though.

### What a beginner should combine with AI (synthesis, not sourced stats)
1. **Game design fundamentals.** Make a fun core loop first. AI can't decide what is fun, and 47% of tiny 2026 Steam releases disclose AI, so "AI-made" is no longer special.
2. **Basic coding literacy** (JavaScript/Three.js, Luau for Roblox, C# for Unity) so you can read and debug what Cursor, Claude Code or the Unity Agent writes.
3. **Distribution and community:** short-form video, X, Discord, Steam wishlists. This was Levels' real advantage.
4. **An art direction and a human touch.** Use AI for placeholders and prototyping; ship human-made or heavily edited final art, and disclose honestly on Steam. Crimson Desert, Clair Obscur and Arc Raiders show the cost of getting this wrong.
5. **Platform choice:** Roblox, UEFN or the web for fast reach; Steam for premium games (with the AI-disclosure form).
6. **Cost discipline:** track token and tool spend. Mobilegamer found many solo AI devs lose money.
7. **IP awareness:** purely AI output may not be copyrightable (USCO, Jan 2025), and Roblox filters prompts for brand/IP.

---

## 6. MARKET PROJECTIONS (all are ESTIMATES from paid-report vendors; they vary 4–5x)

| Publisher | Scope | Figures | Label |
|---|---|---|---|
| The Business Research Company | GenAI in gaming | $1.79B (2025) → $2.21B (2026) → **$5.09B (2030)**, CAGR ~23% | [S] estimate — https://www.thebusinessresearchcompany.com/report/generative-ai-in-gaming-global-market-report |
| TechSci Research | GenAI in gaming | $2.46B (2025) → **$9.82B (2031)**, CAGR 25.95% | [S] estimate — https://www.techsciresearch.com/report/generative-ai-in-gaming-market/24957.html |
| Market Glass (via MarketResearch.com) | AI in gaming (broad) | $3.5B (2024) → **$23.5B (2030)**, CAGR 37% | [S] estimate — https://www.marketresearch.com/Market-Glass-Inc-v1039/Artificial-Intelligence-AI-Gaming-42952282/ |
| Technavio | GenAI in gaming | +$7.85B growth 2024–2029, CAGR 39.2% | [S] estimate — https://technavio.com/report/generative-ai-in-gaming-market-industry-analysis |
| Market Research Future | GenAI in gaming | $2.61B (2024) → $35B (2035) | [U] the site's other page shows inconsistent units, so avoid |

**Analyst views on AAA costs:** Morgan Stanley says costs could fall by "nearly half", worth ~$22B/yr in profit (Apr 2026) [V]. Bain says AI lowers costs but also lowers barriers for rivals [S]. Google Cloud found 94% of developers expect lower costs [V]. Investor fear runs the other way too: Unity lost 24% in a day on Genie (Jan 30, 2026) [V].

**On-screen framing:** "AI in games is a small market, roughly $5–25B by 2030 depending on who you ask. The real money is the cost it removes from the much larger games industry."

---

## 7. HOOK FACTS (5–8)

1. **Almost half (49.9%) of all new Steam games released in October 2026 admitted using AI, up from 1.7% in January 2024.** [S] (u/ploz analysis via Dexerto/PC Gamer, Nov 2026)
2. **Google released an AI that "dreams up" playable worlds, and Unity's stock crashed 24% in a single day** (Jan 30, 2026); Roblox fell 13%. [V] (Bloomberg)
3. **Morgan Stanley: AI could cut the cost of making a game by nearly half, worth about $22 billion a year in extra profit.** [V] (Apr 2026)
4. **A man who had never made a game built a flight simulator with AI in about 3 hours and hit a "$1M-a-year" run-rate in 17 days, then the revenue faded.** [S, self-reported] Use it as both inspiration and warning.
5. **BGMI's publisher Krafton declared itself "AI First": ~$70M on a 1,000+ GPU cluster and ~30B won a year for staff AI tools.** [V] (Oct 2025 / Jan 2026)
6. **Square Enix (Final Fantasy) wants AI doing 70% of its bug-testing by the end of 2027.** [V]
7. **Arc Raiders was slammed for AI voices and still sold 16M+ copies, then quietly swapped many AI lines for human actors: "A real actor is better than AI."** [V]
8. **Clair Obscur lost its Indie Game of the Year award two days after winning, over AI placeholder textures.** [V] (Dec 2025)
   - Bonus: **87% of game developers already use AI agents** (Google Cloud, 2025) [V]. The GDC 2026 figure of 40% is a useful contrast.

---

## DISPUTED / UNCERTAIN

- **Adoption rates conflict:** Google Cloud says 87–90% (vendor-commissioned, 615 devs, mid-2025); GDC says 40% use GenAI at work (Nov 2026). The definitions differ, so present both with their sources.
- **Steam series:** Lambe ("1 in 5" 2025 releases, 7,818 → 10,258 titles) and u/ploz (24% for 2025, 49.9% in Oct 2026) use different methods. All counts are self-reported floors. Valve's Jan 2026 change removed back-end tools from disclosure, so later shares are not strictly comparable with earlier ones.
- **Pieter Levels' revenue:** "$1M ARR" is a run-rate from his own MRR claim ($87K), not audited, and later reports show a steep decline. Concurrent-player figures conflict (17K vs 26K).
- **Genie 4 (Oct 2026):** only secondary coverage; availability and features not confirmed on Google's blog.
- **Project Genie stock drops:** closing figures (Bloomberg: Unity −24%, Roblox −13%, Take-Two −7.9%) differ from intraday figures (Unity −18.8% to −21%, Take-Two −10%). Use Bloomberg's closing figures.
- **PUBG Ally beta year** (June 17–30): most likely 2025, not confirmed in the snippets.
- **Fortnite UEFN "Conversations"** model (Gemini 1.5 vs 3.1 Flash Lite) and exact launch date: conflicting reports.
- **Meshy/Tripo user and ARR numbers** are company claims or aggregator figures. Meshy's ">$100M ARR, Sep 2026" is [U].
- **Crimson Desert ~30% stock drop:** aggregator only.
- **EA "core of our business"** is not a verified Wilson quote.
- **Unity Muse** being "replaced" by Unity AI is inferred, not confirmed.
- **Not researched (budget):** AI Dungeon stats, AI mocap-from-video tools (Move.ai etc.), the Call of Duty BO7 AI-art controversy, Unreal Engine 6 AI specifics, Steam's Nov 2026 policy (no change found after Jan 2026).
