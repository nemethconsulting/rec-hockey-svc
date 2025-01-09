<div style="display: flex; align-items: center; justify-content: space-between;">
  <h1>Add games to your team's schedule</h1>
  <img src="rec-hockey-service-logo_4x4.jpeg" alt="Rec Hockey League Logo" style="width: 100px; height: 100px; margin-left: 20px;">
</div>

In this tutorial:

- You will learn how to add games to your team's schedule using both
curl and Postman Desktop
- You will be introduced to some common errors and troubleshooting tips

## Contents of this page
1. [Prerequisites](#1)
2. [Add your games using curl](#2)
3. [Add your games using Postman Desktop](#3)
4. [Errors & troubleshooting](#4)
5. [Related topics](#5)
6. [Back to main menu](nav.md)

<a id="1"></a>
## Prerequisites

- Make sure your system is running the API server. See [Test your set up](test-system.md) if you need help with this.
- Make sure you've first created a team entry in the Rec Hockey League API. See [Create an entry for your team](tut-create-team.md) for assistance.

<a id="2"></a>
## Add your games using curl

1. Start by gathering the necessary data about your games. See our [games resource](res-games.md) guide for the necessary fields to make your call. If you don't have all data on hand, review our [Note on null or empty fields](tut-null-fields.md).

2. Assume your team is assigned `id`=5 in the db (The new entry for the Shoreline Squids) and you want to add the first two season games to the schedule. Make the following `POST`.

```bash
curl -X POST {base_url}/games \
-H "Content-Type: application/json" \
-d '{
  "id": 5,
  "teamName": "Shoreline Squids",
  "season": "2024-2025",
  "seasonGames": [
    {
      "gameNumber": 1,
      "date": "2024-10-19T19:00:00-08:00",
      "homeGame": true,
      "opposingTeam": "Bothell Blizzards",
      "finalScore": "TBD"
    },
    {
      "gameNumber": 2,
      "date": "2024-10-26T18:30:00-08:00",
      "homeGame": false,
      "opposingTeam": "Kirkland Kraken",
      "finalScore": "TBD"
    }
  ]
}'
```

The response should look like:

```json
{
  "id": 5,
  "teamName": "Shoreline Squids",
  "season": "2024-2025",
  "seasonGames": [
    {
      "gameNumber": 1,
      "date": "2024-10-19T19:00:00-08:00",
      "homeGame": true,
      "opposingTeam": "Bothell Blizzards",
      "finalScore": "TBD"
    },
    {
      "gameNumber": 2,
      "date": "2024-10-26T18:30:00-08:00",
      "homeGame": false,
      "opposingTeam": "Kirkland Kraken",
      "finalScore": "TBD"
    }
  ]
}
```

3. Use this method to add any additional games to the team's schedule. When a game is complete, use our [Update the score of a completed game](tut-add-score.md) tutorial to update the db.

<a id="3"></a>
## Add your games using Postman Desktop

1. Start by gathering the necessary data about your games. See our [games resource](res-games.md) guide for the necessary fields to make your call. If you don't have all data on hand, review our [Note on null or empty fields](tut-null-fields.md).

2. Assume your team is assigned `id`=6 in the db (The new entry for the Bothell Blizzards) and you want to add the first two season games to the schedule. Make the following `POST`. 

    * **METHOD**: POST
    * **URL**: `{{base_url}}/games`
    * **Headers**:
        * `Content-Type: application/json`
    * **Request body**:
        You can change the values of each property as needed.

```json
{
  "id": 6,
  "teamName": "Bothell Blizzards",
  "season": "2024-2025",
  "seasonGames": [
    {
      "gameNumber": 1,
      "date": "2024-10-20T19:00:00-08:00",
      "homeGame": true,
      "opposingTeam": "Redmond Rangers",
      "finalScore": "TBD"
    },
    {
      "gameNumber": 2,
      "date": "2024-10-27T18:30:00-08:00",
      "homeGame": false,
      "opposingTeam": "Issaquah Yetis",
      "finalScore": "TBD"
    }
  ]
}
```

The response should look like:

```json
{
    "id": 6,
    "teamName": "Bothell Blizzards",
    "season": "2024-2025",
    "seasonGames": [
        {
            "gameNumber": 1,
            "date": "2024-10-20T19:00:00-08:00",
            "homeGame": true,
            "opposingTeam": "Redmond Rangers",
            "finalScore": "TBD"
        },
        {
            "gameNumber": 2,
            "date": "2024-10-27T18:30:00-08:00",
            "homeGame": false,
            "opposingTeam": "Issaquah Yetis",
            "finalScore": "TBD"
        }
    ]
}
```

3. Use this method to add any additional games to the team's schedule. When a game is complete, use our [Update the score of a completed game](tut-add-score.md) tutorial to update the db.

<a id="4"></a>
## Errors & troubleshooting

1. One error you may encounter is:

```bash
Error: Insert failed, duplicate id
```
Both curl and Postman Desktop will throw this error when you try to `POST` using a  `gameNumber` that already exists. 

**To troubleshoot:** If you receive this error, make a `GET` request and adjust your `gameNumber` for the new game accordingly.

2. Other errors often occur because of a mistyped command, including:
    - Forgetting to put a backslash after one of your lines of code in curl
    - Using single quotes instead of double quotes when delivering your json data
    - Mistyping the URL
    - Forgetting a comma after a field entry in your JSON data (or leaving a trailing comma where it doesn't belong)
    - Other misc mis-formatting of commands and json payloads
    
**To troubleshoot:** Recheck your command closely and look for potential errors.


<a id="5"></a>
## Related topics

Here are related tutorials you may want to look at:

1. [Create an entry for your team](tut-create-team.md)
2. [Update the final score of a game](tut-add-score.md)
3. [Retrieve the league's win/loss records](tut-get-wins.md)

## [Back to main menu](nav.md)
