<div style="display: flex; align-items: center; justify-content: space-between;">
  <h1>Create an entry for your team</h1>
  <img src="rec-hockey-service-logo_4x4.jpeg" alt="Rec Hockey League Logo" style="width: 100px; height: 100px; margin-left: 20px;">
</div>

In this tutorial:

- You will learn how to add a team to the Rec Hockey League API using both
curl and Postman Desktop
- You will be introduced to some common errors and troubleshooting tips

## Contents of this page
1. [Prerequisites](#1)
2. [Add your team using curl](#2)
3. [Add your team using Postman Desktop](#3)
4. [Errors & troubleshooting](#4)
5. [Related topics](#5)
6. [Back to main menu](nav.md)

<a id="1"></a>
## Prerequisites

- Make sure your system is running the API server. See [Test your set up](test-system.md) if you need help with this.

<a id="2"></a>
## Add your team using curl

1. Refer to the [teams resource](res-teams.md) doc for field descriptions and values constraints specific to this resource.

2. Perform a `GET` call like you did in the [test your system](test-system.md) doc to retrieve a list of teams. The API does not automatically generate id values, so you must provide one. Use the highest existing id + 1. (In the case of the following POST, this `id` will be 5).

3. Format your `POST` call as follows:

```bash
curl -X POST {base_url}/teams \
-H "Content-Type: application/json" \
-d '{
  "id": 5,
  "teamName": "Shoreline Squids",
  "headquarters": "Shoreline, WA",
  "mascot": "Sandy the Squid",
  "winLossRatio": "TBD",
  "coach": "Finn Splash",
  "numberOfPlayers": 19,
  "arenaName": "Squid Harbor",
  "arenaAddress": "456 Coral St, Shoreline, WA 98155"
}'
```

The response should look like:

```bash
{
  "id": 5,
  "teamName": "Shoreline Squids",
  "headquarters": "Shoreline, WA",
  "mascot": "Sandy the Squid",
  "winLossRatio": "TBD",
  "coach": "Finn Splash",
  "numberOfPlayers": 19,
  "arenaName": "Squid Harbor",
  "arenaAddress": "456 Coral St, Shoreline, WA 98155"
}
```

4. With your team created, you can go ahead and start adding your [team's schedule](tut-add-games.md).

<a id="3"></a>
## Add your team using Postman Desktop

1. Refer to the [teams resource](res-teams.md) doc for fields and values specific to this resource.

2. Perform a `GET` call like you did in the [test your system](test-system.md) doc to retrieve a list of teams. The API does not automatically generate id values, so you must provide one. Use the highest existing id + 1. (In the case of the following POST, this `id` will be 6).

3. Format your `POST` call as follows:

* **METHOD**: POST
    * **URL**: `{{base_url}}/teams`
    * **Headers**:
        * `Content-Type: application/json`
    * **Request body**:
        You can change the values of each property as needed.

```json
{
  "id": 6,
  "teamName": "Bothell Blizzards",
  "headquarters": "Bothell, WA",
  "mascot": "Blake the Blizzard",
  "winLossRatio": "TBD",
  "coach": "Chill Iceberg",
  "numberOfPlayers": 18,
  "arenaName": "Blizzard Bay",
  "arenaAddress": "789 Snowy Ln, Bothell, WA 98011"
}
```

The response should look like:

```json
{
    "id": 6,
    "teamName": "Bothell Blizzards",
    "headquarters": "Bothell, WA",
    "mascot": "Blake the Blizzard",
    "winLossRatio": "TBD",
    "coach": "Chill Iceberg",
    "numberOfPlayers": 18,
    "arenaName": "Blizzard Bay",
    "arenaAddress": "789 Snowy Ln, Bothell, WA 98011"
}
```

4. With your team created, you can go ahead and start adding your [team's schedule](tut-add-games.md).

<a id="4"></a>
## Errors & troubleshooting

1. One error you may encounter is:

```bash
Error: Insert failed, duplicate id
```
Both curl and Postman Desktop will throw this error when you try to `POST` using a team `id` that already exists in the database.

**To troubleshoot:** Do a `GET` call to review all teams in the db and find an `id` that is not already being used, preferably being the highest existing `id` +1.

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

1. [Add games to your team's calendar](tut-add-games.md)
2. [Update the final score of a game](tut-add-score.md)
3. [Retrieve the league's win/loss records](tut-get-wins.md)

## [Back to main menu](nav.md)
