<div style="display: flex; align-items: center; justify-content: space-between;">
  <h1>Test your development system</h1>
  <img src="rec-hockey-service-logo_4x4.jpeg" alt="Rec Hockey League Logo" style="width: 100px; height: 100px; margin-left: 20px;">
</div>

1. Create and checkout a test branch of your clone of the Rec Hockey API repo. Your `GitHub repo workspace` 
is the directory that contains your clone of the `rec-hockey-api` repo.

    ```bash
    cd <your GitHub repo workspace>
    ls
    # (see the uw-rhs directory in the list)
    cd rec-hockey-api
    git checkout -b -<the branch you want to test>
    cd api
    sh start-server.sh
    ```

    If your development system is installed correctly, you should see
    the service start and display the URL of the service, usually `http://localhost:3000`.

2. Make a test call to the service.

    ```shell
    curl {base_url}/teams
    ```

3. If the service is running correctly, you should see a list of teams from the service, such as in this example.

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
```

- If you don't see the list of teams, or receive an error in any step
of the procedure, investigate and correct the error before continuing.
Some common situations that cause errors include:

1. You mistyped a command.
2. You aren't in the correct directory.
3. A required software component didn't install correctly.
4. A required software component isn't up-to-date.

- If you see the list of teams from the service, you're ready for the [Quick start](quick-start.md).

## [Back to main menu](nav.md)