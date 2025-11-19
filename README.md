# Minimum Cars Problem

## Problem Description

A group of friends is going on a trip. They all meet at the starting point using `N` cars. Each car is represented by two arrays:

- `P[K]`: number of people in each car  
- `S[K]`: number of seats available in each car  

The goal is to **use as few cars as possible** to carry all the people, leaving the rest parked.

### Examples

1. `P = [1, 4, 1]`, `S = [1, 5, 1]` → return `2`  
   (One person from car 0 moves to car 1. Car 0 stays parked.)

2. `P = [4, 4, 2, 4]`, `S = [5, 5, 2, 5]` → return `3`  
   (People from car 2 move to other cars. Car 2 stays parked.)

3. `P = [2, 3, 4, 2]`, `S = [2, 5, 7, 2]` → return `2`  
   (People from cars 0 and 3 move to cars 1 and 2.)

---

## Solution Approaches

### 1. Greedy Approach (Largest Seats First) 

Pick the cars with the **largest seat capacity first** until all people can fit.  

**TypeScript Code:**

```ts
function minimumCarsGreedy(P: number[], S: number[]): number {
    const totalPeople = P.reduce((a, b) => a + b, 0);
    const seats = [...S].sort((a, b) => b - a);

    let usedSeats = 0;
    let carsUsed = 0;

    for (const capacity of seats) {
        usedSeats += capacity;
        carsUsed++;
        if (usedSeats >= totalPeople) break;
    }

    return carsUsed;
}




