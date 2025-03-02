
2025-03-02 15:57

Tags: #cn #selectiverepeat #reliability_protocol

# Selective Repeat

### Main Idea

- **Sender and receiver window**
	- Sender and receiver agree on a window size
	- The sender keeps list of packets that are sent but the ack isnt received for them
	- The receiver keeps a list of packets that are received but are not yet processed
- **Sender Side**
	- The sender sends the maximum no of packets allowed by the window size without waiting for an ack and starts a timer for each packet
	- If the ack is not received before the timeout then the sender assumes the packet got lost and re-transmits packets which didn't get an ack in return
	- The timer could be dynamically calculated to account for network congestion or excessive load on receiver side
- **Receiver Side**
	- The receiver accepts packets even if they are out of order
	- Stores all the packets it has received in a buffer
	- Sorts and processes them and sends them to the application

To code this application 5 units need to be taken care of
- Sending frames
- Receiving acknowledgement 
- Keeping track of sent frames and receive frames (use arrays) and sending frames until all frames are sent and all acknowledgement is received
- If frame sent and ack not received then send ack again


### Algorithm
1. Add imports (stdio.h, stdlib.h, time.h, unistd.h)
2. Define global variables(window size, total frames to send, probability of loss)
3. Create function to send frame(loss prob: 30%)
4. Create function to send ack(loss prob: 30%)
5. Create function to store the sent and received frame and ack
	1. If frame not send call 3
	2. If frame sent and ack not received call 4
	3. If base frame acknowledged then slide the window and increment base for the next window
6. Repeat until all frames are done


### Code
```C
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
#include<unistd.h>

#define WINDOW_SIZE 3
#define TOTAL_FRAMES 10
#define MAX_FRAMES 10
#define LOSS_PROBABILITY 3


// Simulate frame transmission
int send_frame(int frame_number) {
	printf("Sending frame %d...\n", frame_number);
	sleep(1); // Simulate delay
	int rand_value = rand() % 10; // Generate random number between 0 and 99 and take remainder after dividing by 10
	if (rand_value < LOSS_PROBABILITY) {
		printf("Frame %d lost during transmission!\n", frame_number);
		return 0;
	}
	printf("Frame %d sent successfully.\n", frame_number);
	return 1;
}


// Simulate receiving acknowledgment
int receive_ack(int frame_number) {
	printf("Receiving acknowledgment for frame %d...\n", frame_number);
	sleep(1); // Simulate delay
	int rand_value = rand() % 10; // Generate random number between 0 and 99 and take remainder after dividing by 10
	if (rand_value < LOSS_PROBABILITY) {
	printf("Acknowledgment for frame %d lost!\n", frame_number);
	return 0;
	}
	printf("Acknowledgment for frame %d received.\n", frame_number);
	return 1;
}


// Selective Repeat ARQ Protocol
void selective_repeat_arq() {
	int sent_frames[TOTAL_FRAMES] = {0}; // Track sent frames
	int ack_received[TOTAL_FRAMES] = {0}; // Track acknowledgments received
	int base = 0; // Start of sliding window


	while (base < TOTAL_FRAMES) {
		// Send frames within the window
		for (int i = base; i < base + WINDOW_SIZE && i < TOTAL_FRAMES; i++) {
			if (!sent_frames[i]) {
				sent_frames[i] = send_frame(i); // Send frame if not sent
			}
		}


		// Check for acknowledgments
		for (int i = base; i < base + WINDOW_SIZE && i < TOTAL_FRAMES; i++) {
			if (sent_frames[i] && !ack_received[i]) {
				ack_received[i] = receive_ack(i); // Mark ack if received
			}
		}


		// Slide the window if the base frame is acknowledged
		while (base < TOTAL_FRAMES && ack_received[base]) {
			printf("Frame %d fully acknowledged.\n", base);
			base++;
		}
		//printf("Sliding Window Forward\n");
		
	}
	printf("All frames sent and acknowledged successfully.\n");
}


// Main function
int main() {
srand(time(0)); // Seed random number generator
selective_repeat_arq();
return 0;
}


```



# References
---


	