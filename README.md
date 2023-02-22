# QC Mentorship Program

This is the repo with the solution of Task 2 Is Rectangle for admission to QC Mentorship Program.

Text of the task:

  Given four positive integers A, B, C, D, determine if there’s a rectangle such that the lengths of its sides are A, B, C and D (in any order).

  If any such rectangle exist return 1 else return 0.

Two approaches have been used:
<ol>
<li>
Approach #1: create a quantum circuit to compare two bitstrings, and use it to compare each pair of the given numbers. In such an approach, for each pair, I encode each bit of the bitstrings of the two numbers in a different qubit, and implement a quantum circuit which compares the content of the qubits. Since each qubit is in a base state, measurement will give correct output with probability 1.
</li>
<li>
Approach #2: building on top of approach #1, I use entanglement to compare two pairs of different numbers with the same circuit, at the same time. Therefore, the number of times the quantum circuit is created is halved, reducing the execution time.
</li>
</ol>

As it can be seen, results show that Approach #2 results to be faster than Approach #1 (6min 52s versus 8min 5s, on an Intel i7-7700HQ), due to the higher number of circuits to run required by Approach #1. Yet, I experienced cases in which Approach #1 resulted to be faster than approach #2. Why? The answer is simple: even though the number of circuits to create and run is higher for approach #1, the number of qubits used, which is logarithmic w.r.t the maximum number of the inputs, is lower for approach #1 (because of the ancilla qubit used by approach #2), and we know that, for emulators, an increase in the number of qubits implies an exponential increase in the execution time. Additionally, Approach #2 requires more shots to run, while Approach #1 only requires 1 shot, since it gives the correct output with probability = 1. Unfortunately, I cannot run such circuits on a real quantum hardware, so I can finally say that, for what concerns quantum emulators, Approach #2 generally wins, but the real performance effectively depends on the instance of the problem.
