#include <stdio.h>
#include <stdbool.h>
#define NUM_SEATS 10

// Global array to store seat availability
bool seats[NUM_SEATS] = {false};

// Function to display available seats
void displaySeats() {
    printf("Available Seats:\n");
    for (int i = 0; i < NUM_SEATS; i++) {
        if (!seats[i]) {
            printf("Seat %d: Available\n", i + 1);
        } else {
            printf("Seat %d: Booked\n", i + 1);
        }
    }
}

// Function to book a seat
void bookSeat() {
    int seatNum;
    displaySeats();
    printf("Enter seat number to book: ");
    scanf("%d", &seatNum);

    if (seatNum < 1 || seatNum > NUM_SEATS) {
        printf("Invalid seat number.\n");
        return;
    }

    if (seats[seatNum - 1]) {
        printf("Seat %d is already booked.\n", seatNum);
    } else {
        seats[seatNum - 1] = true;
        printf("Seat %d booked successfully.\n", seatNum);
    }
}

// Function to cancel a reservation
void cancelReservation() {
    int seatNum;
    displaySeats();
    printf("Enter seat number to cancel reservation: ");
    scanf("%d", &seatNum);

    if (seatNum < 1 || seatNum > NUM_SEATS) {
        printf("Invalid seat number.\n");
        return;
    }

    if (!seats[seatNum - 1]) {
        printf("No reservation found for seat %d.\n", seatNum);
    } else {
        seats[seatNum - 1] = false;
        printf("Reservation for seat %d canceled successfully.\n", seatNum);
    }
}

int main() {
    int choice;

    do {
        printf("\nAirline Reservation System\n");
        printf("1. Display Available Seats\n");
        printf("2. Book a Seat\n");
        printf("3. Cancel Reservation\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                displaySeats();
                break;
            case 2:
                bookSeat();
                break;
            case 3:
                cancelReservation();
                break;
            case 4:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice. Please enter a number between 1 and 4.\n");
        }
    } while (choice != 4);

    return 0;
}
