# In SKILL.md frontmatter
---
name: firecrawl-search
description: Search the web AND scrape returned URLs into clean structured data via the Firecrawl CLI. Pairs naturally with Tavily/Exa: search returns links, Firecrawl extracts the content. Handles JS-rendered pages + paywalls.
prism:
  tokenId: 13
  costMicroUsdcPerUse: 140
  legs:
    - { recipient: "0xFabb0640acbF0f58A786539c84Cd1cd123180A01", bps: 100 }
    - { recipient: "0x6d726306459BbBD7B1e749931a05f6De241f3e8e", bps: 9900 }
---

# In your runtime
import { parseSkillFrontmatter, withPrismSkill } from "@prism/skills";
import { walletClient, publicClient } from "./lib/viem";

const { name, prism } = await parseSkillFrontmatter("./skills/firecrawl-search/SKILL.md");
const paid = withPrismSkill(name!, prism!, runSkill, {
  payer: walletClient,
  publicClient,
});

await paid({ /* your skill input */ });