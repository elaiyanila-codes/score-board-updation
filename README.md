# score-board-updation
#include <stdio.h>
    return -1; // Player not found
}

// Function to delete a player by name
void deletePlayer(struct Player players[], int *numPlayers, char playerName[]) {
    int index = searchPlayer(players, *numPlayers, playerName);
    if (index != -1) {
        // Shift elements to overwrite the player to be deleted
        for (int i = index; i < *numPlayers - 1; i++) {
            players[i] = players[i + 1];
        }
        (*numPlayers)--;
        printf("Player '%s' deleted successfully!\n", playerName);
    }
}

int main() {
    struct Player players[10]; // Array to hold players
    int numPlayers = 0; // Variable to track the number of players
    int choice;
    char playerName[50];

    do {
        printf("\nMenu:\n");
        printf("1. Add Player\n");
        printf("2. Search Player\n");
        printf("3. Delete Player\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter player name: ");
                scanf("%s", playerName);
                addPlayer(players, &numPlayers, playerName);
                break;
            case 2:
                printf("Enter player name to search: ");
                scanf("%s", playerName);
                searchPlayer(players, numPlayers, playerName);
                break;
            case 3:
                printf("Enter player name to delete: ");
                scanf("%s", playerName);
                deletePlayer(players, &numPlayers, playerName);
                break;
            case 4:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 4);

    return 0;
}
