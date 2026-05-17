# Project 2 Extra Credit

**Name:** Ayushman Bajracharya

## Project Description

This project simulates a network of queues with one central server and multiple downstream servers. Customers arrive based on exponential interarrival times, first receive service at the central server, and are then routed to one of the regular downstream servers.

The simulation compares two different systems:

### System 1

The central server sends each customer to an awake downstream server.  
Downstream server queues are allowed, so customers may wait if the selected server is busy.

### System 2

The central server sends a customer only to an awake, idle downstream server.  
If no awake and free server is available, the central server becomes blocked and new arrivals are dropped until service can continue.

The simulation runs until **10,000 customer departures** are completed. Results are compared for both **n = 3** and **n = 5** downstream servers.

## Extra Credit Features

This version includes the required extra credit additions:

### 1. Server Status at Each Clock Time

At each clock time, the status of every server is printed.

Server status codes:

- `B` = Busy
- `I` = Idle
- `V` = Vacation

### 2. Customer Object Pool

The program uses a fixed pool array of **100 customer objects**.

Instead of dynamically creating and deleting customers, the simulation reuses customer objects from the pool. When a customer completes service, that customer object is returned to the pool and can be reused by a future arrival.

### 3. Vacation and Wake-Up Events in the FEL

Server vacation and wake-up events are included in the **Future Event List (FEL)**.

These inactive-server events are marked with `[RED]` in the output so they are easier to identify and distinguish from regular arrival and departure events.

## Rates Used

| Parameter | Rate |
|---|---:|
| External arrival rate, `lambda0` | 8 |
| Central server service rate | 10 |
| Sleep/vacation ending rate, `lambda2` | 5 |
| Server 1 service rate | 14 |
| Server 2 service rate | 15 |
| Server 3 service rate | 20 |
| Server 4 service rate | 20 |
| Server 5 service rate | 20 |

## Compile Command

```bash
g++ -std=c++11 SimulationProject2ExtraCredit.cpp -o extra
