import FirecrawlApp from "@mendable/firecrawl-js";
import { z } from "zod";

const app = new FirecrawlApp({
  apiKey: "fc-YOUR_API_KEY"
});

// Define schema to extract contents into
const schema = z.object({
  company_mission: z.string(),
  supports_sso: z.boolean(),
  is_open_source: z.boolean(),
  is_in_yc: z.boolean()
});

(async () => {
  const result = await app.scrape("https://docs.firecrawl.dev/", {
    formats: [{
      type: "json",
      schema: schema
    }],
  });

  console.log(result);
})();
