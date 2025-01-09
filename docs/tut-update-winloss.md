<div style="display: flex; align-items: center; justify-content: space-between;">
  <h1>Update your team's winLossRatio</h1>
  <img src="rec-hockey-service-logo_4x4.jpeg" alt="Rec Hockey League Logo" style="width: 100px; height: 100px; margin-left: 20px;">
</div>

In this tutorial:

- You will learn how to update the `winLossRatio` field after a game is completed, using both
curl and Postman Desktop
- You will be introduced to some common errors and troubleshooting tips

## Contents of this page
1. [Prerequisites](#1)
2. [Update the `winLossRatio` using curl](#2)
3. [Update the `winLossRatio` using Postman Desktop](#3)
4. [Errors & troubleshooting](#4)
5. [Related topics](#5)
6. [Back to main menu](nav.md)

<a id="1"></a>
## Prerequisites

- Make sure your system is running the API server. See [Test your set up](test-system.md) if you need help with this.
- Make sure you've already added your team details into the Rec Hockey Service API. See [Create an entry for your team](tut-create-team.md) for assistance.

<a id="2"></a>
## Update the `winLossRatio` using curl

1. Start with a `GET` call to the `teams` resource to retrieve your team's details, or review our [teams resource](res-teams.md) doc to find the required fields.

2. Let's assume you are updating the `winLossRatio` for the Shoreline Squids (team `id` = 5) after winning their first game against the Bothell Blizzards. 

**Note** The `winLossRatio` field uses the format W-L-OTL where W is wins, L is losses, and OTL is overtime losses.

After updating the `winLossRatio` field, send the following `PATCH` call:

```bash
curl -X PATCH {base_url}/teams/5 \
-H "Content-Type: application/json" \
-d '{
  "id": 5,
  "teamName": "Shoreline Squids",
  "headquarters": "Shoreline, WA",
  "mascot": "Sandy the Squid",
  "winLossRatio": "1-0-0",
  "coach": "Finn Splash",
  "numberOfPlayers": 19
}'
```

The response should look like:

```bash
{
  "id": 5,
  "teamName": "Shoreline Squids",
  "headquarters": "Shoreline, WA",
  "mascot": "Sandy the Squid",
  "winLossRatio": "1-0-0",
  "coach": "Finn Splash",
  "numberOfPlayers": 19
}
```

3. When patching multiple fields, we recommend making a final `GET` request to ensure the data has been properly propagated to the database.

4. **NOTE** While it may seem cumbersome to download all resource data and return it just to update a single field, please review the [Limitations of our `json-server`](xtra-limitations.md) doc to understand and potentially troubleshoot this issue.

5. As the season progresses, you may want to retrieve the `winLossRatio` for all teams in the league to calculate standings. To do this, refer to our [Retrieve the league's win/loss records](tut-retrieve-wlr.md) tutorial.

<a id="3"></a>
## Update the score using Postman Desktop

1. Start with a `GET` call to the `teams` resource to retrieve your team's details, or review our [teams resource](res-teams.md) doc to find the required fields.

2. Let's assume you are updating the `winLossRatio` for the Bothell Blizzards (team `id` = 6) after losing their first game to the Redmond Rangers. 

**Note** The `winLossRatio` field uses the format W-L-OTL where W is wins, L is losses, and OTL is overtime losses.

After updating the `winLossRatio` field, send the following `PATCH` call:

    * **METHOD**: PATCH
    * **URL**: `{base_url}/teams/6`
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
  "winLossRatio": "0-1-0",
  "coach": "Chill Iceberg",
  "numberOfPlayers": 18
}
```

The response should look like:

```js
{
  "id": 6,
  "teamName": "Bothell Blizzards",
  "headquarters": "Bothell, WA",
  "mascot": "Blake the Blizzard",
  "winLossRatio": "0-1-0",
  "coach": "Chill Iceberg",
  "numberOfPlayers": 18
}
```

3. When patching multiple fields, we recommend making a final `GET` request to ensure the data has been properly propagated to the database.

4. **NOTE** While it may seem cumbersome to download all resource data and return it just to update a single field, please review the [Limitations of our `json-server`](xtra-limitations.md) doc to understand and potentially troubleshoot this issue.

5. As the season progresses, you may want to retrieve the `winLossRatio` for all teams in the league to calculate standings. To do this, refer to our [Retrieve the league's win/loss records](tut-retrieve-wlr.md) tutorial.

<a id="4"></a>
### Errors & troubleshooting

1. Other errors often occur because of a mistyped command, including:
    - Forgetting to put a backslash after one of your lines of code in curl
    - Using single quotes instead of double quotes when delivering your json data
    - Mistyping the URL
    - Forgetting a comma after a field entry in your JSON data (or leaving a trailing comma where it doesn't belong)
    - Other misc mis-formatting of commands and json payloads

**To troubleshoot:** Recheck your command closely and look for these potential errors.


<a id="5"></a>
## Related topics

Here are related tutorials you may want to look at:

1. [Create an entry for your team](tut-create-team.md)
2. [Add games to your team's calendar](tut-add-games.md)
3. [Retrieve the league's win/loss records](tut-retrieve-wlr.md)

### [Back to main menu](nav.md)
