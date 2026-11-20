# Mouve MCP connector

Free Mouve connector: log meals, build workouts, track progress. Health data only with your consent.

[Mouve](https://mouve.it) is a world of fitness to step into: scan your food, follow guided workouts, and discover places to move. The Mouve connector lets your AI assistant work with your own Mouve account. Log meals and look up foods, build and save workouts and programs, record workout sessions and body measurements, see your weekly progress, find outdoor gyms and plan a route, and read or post on your Mouve feed.

This repository is the public home of the connector's listing. The server is hosted by Mouve; there is nothing to install or run.

## Connect

| | |
| --- | --- |
| Server URL | `https://api.mouve.it/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with PKCE (S256) and Dynamic Client Registration; scoped consent per permission |
| Official MCP Registry | [`it.mouve/mcp`](https://registry.modelcontextprotocol.io/v0.1/servers?search=it.mouve) |
| Price | Free. No plan check and no usage fee; a free Mouve account is all you need |

Add `https://api.mouve.it/mcp` as a custom connector in Claude, ChatGPT or any MCP client that supports remote servers, then sign in on mouve.it and approve the permissions you want.

Step-by-step setup for each assistant: [mouve.it/connect-ai](https://mouve.it/connect-ai) ([Markdown](https://mouve.it/connect-ai.md)). Developer docs: [mouve.it/developers/mcp](https://mouve.it/developers/mcp).

Client config for MCP clients that read `mcpServers`:

```json
{
  "mcpServers": {
    "mouve": {
      "type": "streamable-http",
      "url": "https://api.mouve.it/mcp"
    }
  }
}
```

## What you can ask

- "Log my lunch in Mouve: 150 g chicken breast and a cup of rice."
- "Build me a 30 minute beginner full-body workout and save it to Mouve."
- "How is my week going in Mouve? Workouts and food."
- "Log my weight in Mouve as 78.4 kg."
- "Find outdoor gyms near me and plan a walking route to the closest one."

## Tools

46 tools, each with a title and read-only or destructive annotations. Reads and writes are separate tools.

- **Nutrition:** `search_foods`, `log_meal`, `get_nutrition_day`, `update_food_log_entry`, `delete_food_log_entry`, `parse_food_description`, `analyze_food_image`, `generate_meal_suggestion`, `generate_daily_meal_plan`, `save_recipe`
- **Workouts and programs:** `search_exercises`, `create_workout`, `get_my_workouts`, `get_workout_detail`, `log_workout_session`, `get_workout_history`, `get_program_setup`, `create_program`, `get_my_programs`, `get_program`, `update_program`, `start_program`, `share_program`
- **Progress and body:** `get_weekly_progress`, `get_body_metrics`, `log_body_metrics`
- **World:** `find_outdoor_gyms`, `plan_route`, `send_route_to_app`, `get_my_location`
- **Feed and people:** `get_my_feed`, `get_post_detail`, `create_post`, `comment_on_post`, `like_post`, `delete_post`, `get_notifications`, `get_my_profile`, `get_user_profile`, `update_profile`, `follow_user`, `unfollow_user`
- **Memory:** `get_user_context`, `save_user_memory`
- **Other:** `legal_documents`, `health_check`

## Privacy and health data

You sign in on mouve.it and approve each permission on the Mouve consent screen. Workouts, nutrition and body measurements are health data: they sit in their own block on that screen, and the assistant gets them only if you choose **Share my health data**. You can disconnect at any time in Mouve under Settings, Connected apps, and access ends at once.

- Connector privacy policy: [mouve.it/legal/mcp-privacy](https://mouve.it/legal/mcp-privacy)
- Connector terms: [mouve.it/legal/mcp-terms](https://mouve.it/legal/mcp-terms)

## Get the app

- iOS: [App Store](https://apps.apple.com/app/id6761416244)
- Android: [Google Play](https://play.google.com/store/apps/details?id=com.mouve.app)
- Web: [mouve.it](https://mouve.it)

## Contact

Support: support@mouve.it · Security: security@mouve.it · Privacy: privacy@mouve.it

Made by Mouve Technology OÜ, Tallinn, Estonia.
