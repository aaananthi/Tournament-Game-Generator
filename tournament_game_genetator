def get_number_of_teams():
    n = int(input("Enter the number of teams in the tournament: "))
    if n < 2:
        print("The minimum number of teams is 2, try again.")
        n = get_number_of_teams()

    return n

def check_team_name(name):
    words_list = list(name.split(" "))
    if len(words_list) > 2:
        print("Team names may have at most 2 words, try again.")
        return False
    if len(words_list) == 1 and len(words_list[0]) < 2:
        print("Team names must have at least 2 characters, try again.")
        return False

    return True

def get_team_names(num_teams):
    names = []

    for i in range(num_teams):
        name = input(f"Enter the name for team #{i + 1}: ")
        while not check_team_name(name):
            name = input(f"Enter the name for team #{i + 1}: ")
        names.append(name)
   
    return names

def get_number_of_games_played(num_teams):
    n = int(input("Enter the number of games played by each team: "))
    if n < (num_teams - 1):
        print("Invalid number of games. Each team plays each other at least once in the regular season, try again.")
        n = get_number_of_games_played(num_teams)
    return n

def check_team_wins(win, games_played):
    if win > games_played:
        print(f"The maximum number of wins is {games_played}, try again.")
        return False

    if win < 0:
        print("The minimum number of wins is 0, try again.")
        return False

    return True

def get_team_wins(team_names, games_played):
    wins = {}

    for name in team_names:
        win = int(input(f"Enter the number of wins Team {name} had: "))
        while not check_team_wins(win, games_played):
            win = int(input(f"Enter the number of wins Team {name} had: "))
        wins[name] = win
    return wins

# Main program execution
num_teams = get_number_of_teams()
team_names = get_team_names(num_teams)
games_played = get_number_of_games_played(num_teams)
team_wins = get_team_wins(team_names, games_played)

print("Generating the games to be played in the first round of the tournament...")

sorted_teams = sorted(team_wins.items(), key = lambda x: x[1], reverse = True)

for i in range(len(sorted_teams)// 2):
    print("Home: ", sorted_teams[len(sorted_teams) - i - 1][0], "VS Away: ", sorted_teams[i][0])
