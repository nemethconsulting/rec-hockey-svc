<div style="display: flex; align-items: center; justify-content: space-between;">
  <h1>Rec Hockey API quick start</h1>
  <img src="rec-hockey-service-logo_4x4.jpeg" alt="Rec Hockey League Logo" style="width: 100px; height: 100px; margin-left: 20px;">
</div>

Find your team and get their schedule!

Once your system is [set up](prerequisites.md) and [tested](test-system.md), jump in and get started using our API.

## Contents of this page
1. Using curl
    - [Find your team](#1)
    - [Get your team's schedule](#2)
2. Using Postman Desktop
    - [Find your team](#3)
    - [Get your team's schedule](#4)
3. [Next steps](#5)
4. [Back to main menu](nav.md)

## Using curl

<a id="1"></a>
### Find your team

1. Locate your team with a simple `GET` call to the `teams` resource.

```bash
curl {base_url}/teams
```
2. The response should look like:

```bash
[
  {
    "id": "1",
    "teamName": "Bellevue Bison",
    "headquarters": "Bellevue, WA",
    "mascot": "Benny the Bison",
    "winLossRatio": "1-1",
    "coach": "Jordan Rinkside",
    "numberOfPlayers": 18,
    "arenaName": "Bellevue Ice Palace",
    "arenaAddress": "123 Ice Palace Ave, Bellevue, WA 98004"
  },
  {
    "id": "2",
    "teamName": "Renton Raptors",
    "headquarters": "Renton, WA",
    "mascot": "Rocky the Raptor",
    "winLossRatio": "1-0-1",
    "coach": "Alex Powerplay",
    "numberOfPlayers": 16,
    "arenaName": "Raptor Nest",
    "arenaAddress": "456 Hockey Way, Renton, WA 98057"
  },
  ...
  // additional team data
```

3. Review the returned list to find your team. Make note of their team `id`for next steps.

<a id="2"></a>
### Get your team's schedule

1. Use another `GET` call to pull your team's schedule from the `games` resource.

```bash
curl {base_url}/games/{id}
```
2. The response (for example, if you chose to look up team `id`= 4) should look like:

```bash
{
  "id": "4",
  "teamName": "Kirkland Kraken",
  "season": "2024-2025",
  "seasonGames": [
    {
      "gameNumber": 1,
      "date": "2024-10-18T19:00:00-08:00",
      "homeGame": true,
      "opposingTeam": "Bothell Blizzards",
      "finalScore": "2-2"
    },
    {
      "gameNumber": 2,
      "date": "2024-10-25T18:30:00-08:00",
      "homeGame": false,
      "opposingTeam": "Redmond Rangers",
      "finalScore": "1-4"
    },
    ...
    // additional game data
    ]
  }
```

## Using Postman Desktop

<a id="3"></a>
### Find your team

1. In the Postman app, create a new request with these values:
    * **METHOD**: GET
    * **URL**: `{base_url}/teams`
    * **Headers**:
        * `Content-Type: application/json`
    * **Request body**:
        Not applicable for this GET request

2. Click **Send** to make the request.

3. The response should look like:

```json
    [
    {
        "id": "1",
        "teamName": "Bellevue Bison",
        "headquarters": "Bellevue, WA",
        "mascot": "Benny the Bison",
        "winLossRatio": "1-1",
        "coach": "Jordan Rinkside",
        "numberOfPlayers": 18,
        "arenaName": "Bellevue Ice Palace",
        "arenaAddress": "123 Ice Palace Ave, Bellevue, WA 98004"
    },
    {
        "id": "2",
        "teamName": "Renton Raptors",
        "headquarters": "Renton, WA",
        "mascot": "Rocky the Raptor",
        "winLossRatio": "1-0-1",
        "coach": "Alex Powerplay",
        "numberOfPlayers": 16,
        "arenaName": "Raptor Nest",
        "arenaAddress": "456 Hockey Way, Renton, WA 98057"
    },
    ...
    // additional team data
    ]
```
4. Review the returned list to find your team. Make note of their team `id`for next steps.

<a id="4"></a>
### Get your team's schedule

1. In the Postman app, create a new request with these values:
    * **METHOD**: GET
    * **URL**: `{base_url}/games/{id}`
    * **Headers**:
        * `Content-Type: application/json`

2. Click **Send** to make the request.

3. The response (for example, if you chose to look up team `id`= 3) should look like:

```json
{
    "id": "3",
    "teamName": "Issaquah Yetis",
    "season": "2024-2025",
    "seasonGames": [
        {
            "gameNumber": 1,
            "date": "2024-10-17T19:00:00-08:00",
            "homeGame": true,
            "opposingTeam": "Redmond Rangers",
            "finalScore": "2-1"
        },
        {
            "gameNumber": 2,
            "date": "2024-10-24T18:30:00-08:00",
            "homeGame": false,
            "opposingTeam": "Bothell Blizzards",
            "finalScore": "1-3"
        },
        ...
    ]
}
```

<a id="5"></a>
## Next steps

You're now ready to dive deeper! Explore the [documentation](nav.md) to learn more about what the Rec Hockey League API can do.

## [Back to main menu](nav.md)