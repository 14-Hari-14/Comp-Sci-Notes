
2025-03-02 13:18

Tags: #cn #stopandwait #reliability_protocol 

# Stop And Wait

### Main Idea
The sender sends some data packets (one at a time) and waits for an acknowledgement from the receiver. 

### Key points
- Sender sends a packet
- If the packet is received then ACK packet is sent to convey acknowledgement
- If the packet is not received or if the ACK packet isn't successfully sent then the sender sends the packet again


### Code 
```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <unistd.h>  // for sleep()

//Global Variables Required
#define TIMEOUT 3  // Timeout duration in seconds
#define TOTAL_PACKETS 5  // Number of packets to send
#define SEND_PROB 7 //


int simulate_acknowledgment() {
    // Simulate a 70% chance of successful acknowledgment
    return rand() % 10 < SEND_PROB;
}

int main() {

    srand(time(0));  // Seed for random number generation
    int packet = 1;
    bool ack_received;

  

    while (packet <= TOTAL_PACKETS) {
    
        printf("Sender: Sending packet %d...\n", packet);

        // Simulate waiting for acknowledgment

        sleep(1);  // Simulate transmission delay
        ack_received = simulate_acknowledgment();

  

        if (ack_received) {
            printf("Receiver: ACK for packet %d received.\n\n", packet);
            packet++;  // Move to the next packet
        } 
        else {
            printf("Receiver: ACK for packet %d lost! Retransmitting...\n\n", packet);
            sleep(TIMEOUT);  // Simulate timeout before retransmission

        }

    }

    printf("All packets sent successfully!\n");
    return 0;

}
```


### Algorithm
1. Add imports(stdio.h, stdlib.h, time.h, unistd.h)
2. Define global variables(no of packets, timeout duration, probability of loss)
3. Create a function to simulate a % chance of packet reaching(for ex 70%) 
	1. return rand() % 10 < 7 //generate a number between 0-99 and if the remainder after getting divided by 10 is less send true else send false
4. Create the main function
5. Create a random seed based on time so that the chance of acknowledgement looks random
	1. srand(time(0))
6. Init packet = 1, bool ack_received to contain true or false value after simulation
7. while packet <= Total packet send the packet call the function in step 3 
	1. If true is returned send successful transmission and increment packet
	2. Else return unsuccessful transmission and sleep for the duration of TIMEOUT
8. End the program after termination of while loop
# References
---


	