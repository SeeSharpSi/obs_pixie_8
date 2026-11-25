---
created: 2026-10-26
type: project
topic: tech
status: idea
---
# config 
```
{
  "app": "llm_thing",
  "version": 1,
  "settings": {
    "Endpoint": "https://opencode.ai/zen/go/v1/chat/completions",
    "Model": "deepseek-v4.1-flash",
    "ApiMode": "auto",
    "MaxOutputTokens": "0",
    "ReasoningEffort": "",
    "RequestTimeoutMs": "120000",
    "SystemPrompt": "The user's date-time is $DATETIME. Keep answers concise for a watch screen. Always use the Search MCP server to get up to date websites, and then the web fetch tool to get info from them. Format your responses in markdown, but only use bold text and lists.",
    "ShowThinking": false,
    "ShowInputContextSize": true,
    "ShowOutputContextSize": false,
    "PreserveChats": true,
    "WebSearchEnabled": true,
    "GeolocationToolEnabled": true,
    "TimelineToolEnabled": true,
    "HealthToolEnabled": true,
    "PebbleMemoryToolEnabled": true,
    "MaxToolCalls": "16",
    "FontSize": "24",
    "BuzzStrength": "1",
    "SpeakerFeedbackEnabled": false,
    "ScrollLines": "3",
    "TouchScrollEnabled": false,
    "TextColor": 16777215,
    "BackgroundColor": 0,
    "PromptBackgroundColor": 5570560,
    "BoldTextColor": 16755455,
    "StartDictationQuickLaunch": true,
    "McpServersJson": "[{\"enabled\":true,\"label\":\"Maps\",\"url\":\"https://mapstools.googleapis.com/mcp\",\"description\":\"This is the Google maps MCP. Use it for weather, geolocation, or anything to do with a map.\",\"allowedTools\":\"\",\"maxToolCalls\":\"\",\"authorization\":\"\",\"headers\":[{\"name\":\"X-Goog-Api-Key\",\"value\":\"\"}]},{\"enabled\":false,\"label\":\"Tavily\",\"url\":\"https://mcp.tavily.com/mcp/?tavilyApiKey=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\",\"description\":\"Use this to search the web.\",\"allowedTools\":\"\",\"maxToolCalls\":\"\",\"authorization\":\"\",\"headers\":[]},{\"enabled\":true,\"label\":\"Phone Media\",\"url\":\"http://127.0.0.1:8765/servers/media/mcp\",\"description\":\"Used to interact with the user's phone\",\"allowedTools\":\"\",\"maxToolCalls\":\"\",\"authorization\":\"\",\"headers\":[]},{\"enabled\":true,\"label\":\"Exa\",\"url\":\"https://mcp.exa.ai/mcp\",\"description\":\"Used to search the web\",\"allowedTools\":\"\",\"maxToolCalls\":\"\",\"authorization\":\"\",\"headers\":[{\"name\":\"x-api-key\",\"value\":\"\"}]},{\"enabled\":true,\"label\":\"Obsidian\",\"url\":\"http://127.0.0.1:8765/servers/obsidian/mcp\",\"description\":\"Used to read, search, and create local Obsidian notes\",\"allowedTools\":\"\",\"maxToolCalls\":\"\",\"authorization\":\"\",\"headers\":[]}]"
  }
}
```

