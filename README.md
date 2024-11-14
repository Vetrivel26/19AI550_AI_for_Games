# Ex.No: 1  Implementation of HotPotato game using Queue 
### DATE:                                                                    
### REGISTER NUMBER : 212221240060
### AIM: 
To write a python program to simulate the process of passing an item among players and eliminating players based on the given rules until a single winner is determined.
### Algorithm:
1. Initialize the Queue: Create a queue and enqueue all the participants.
2. Pass the Potato: Dequeue the first person in the queue and enqueue them at the end. This simulates passing the potato.
3. Count the Passes: Repeat the passing for a given number of times.
4. Eliminate the Holder: After the set number of passes, remove the person who holds the potato (dequeue the front of the queue).
5. Repeat: Continue the process until only one person remains in the queue.
### Program:
```
import queue
import random
import time

def hot_potato(names, num):
    sim_queue = queue.Queue()

    for name in names:
        sim_queue.put(name)

    while sim_queue.qsize() > 1:
        for _ in range(num):
            sim_queue.put(sim_queue.get())
        eliminated = sim_queue.get()
        print(f"{eliminated} is eliminated!")

    return sim_queue.get()

def main():
    players = ["Alice", "Bob", "Charlie", "David", "Eve"]
    #num_passes = random.randint(1, 10)
    num_passes=1
    print("Hot Potato Game Start!")
    time.sleep(1)
    winner = hot_potato(players, num_passes)
    print(f"\nThe winner is: {winner}")

if _name_ == "_main_":
    main()
```


### Output:
![WhatsApp Image 2024-08-09 at 11 34 19_17a2290e](https://github.com/user-attachments/assets/ced7fab2-8824-4fbf-a522-3e05ddf4492a)


### Result:
Thus the simple HotPotato game was implemented using Queue.
