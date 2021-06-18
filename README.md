# Poisoned Bottle Problem
My C# console app solution to the poisoned 1000 bottle mathematical problem as defined here (solution 2): https://medium.com/i-math/a-king-1000-bottles-of-wine-10-prisoners-and-a-drop-of-poison-2dd1959a8dd2
> We have 1000 bottles of wine, one of which is poisoned and somehow we need to test all of the wine bottles using only 10 prisoners as taste testers. However we decide to administer the wine to the prisoners, we need to use the prisoners deaths as a code to trace back to the poisoned wine bottle.

A restriction is that only the prisoners' live/dead status can be tested 10 times to determine the poisoned bottle.

# My Solution
My solution code and interactive demo can be found [here](https://replit.com/@DaveWork26/PoisonedBottleProblem#main.cs).<br/>
<br/>
I've tested my solution by poisoning each of the 1000 bottles in turn, printing 'Tests passed:' and 'true' if all tests pass or 'false' if a test fails.<br/>
<br/>
The code is well documented using Microsoft's XML format to enable Visual Studio's Intellisense quick information feature for types and members.

## Algorithm
The algorithm for solution 2 is explained [here](https://medium.com/i-math/a-king-1000-bottles-of-wine-10-prisoners-and-a-drop-of-poison-2dd1959a8dd2), the essence of which is encoding and decoding the bottle numbers in binary, using one bit position to represent each prisoner. The tricky part is isolating the individual bits (prisoners) in the bottle number from the other bits (prisoners). To do this I used a bit mask containing only a single set bit in the required position to perform a bitwise "and" operation upon the bottle number and tested the resultant number: a zero value indicates the prisoner's bit is not set and a non-zero value indicates the prisoner's bit is set. <br/>
<br/>
Initially, I experimented with converting the bottle number to a binary string and analysing the string, but this proved superfluous - we are working in binary so stay with binary numbers.<br/>
Also, when generating the power of 2 bit pattern masks, I optimised the code to logically shift left the least significant bit (value 1) for each prisoner bit (left shifting is an assembler code command at the processor level and is therefore very fast if the compiler utilises this).
