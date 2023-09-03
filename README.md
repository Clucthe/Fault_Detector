# Fault_Detector
 Problem Statement

  The problem requires designing an algorithm and writing code to identify a structural fault in a     manufactured circuit chip.     The algorithm should be able to determine the input vector needed to detect the fault at a specific node in the circuit. The circuit is represented by a file and consists of boolean inputs and outputs connected through logic gates. The fault can be of two types: stuck-at-0 (SA0) or stuck-at-1 (SA1). The algorithm needs to efficiently and accurately identify the fault by providing the input vector and expected output value. The code should output the result to a file.

 The approach used to generate the algorithm.
The approach used in the provided code to generate the algorithm can be outlined as follows:
1. Reading Circuit and Fault Files:
   - The code uses the `fstream` class to read the circuit and fault files.
   - It opens the files and checks if they are successfully opened.
   - The circuit file is read line by line, skipping empty lines and comments.
   - Each line is split into a net and an equation using the '=' symbol as the delimiter.
   - Leading and trailing whitespaces are removed from the net and equation strings.
   - The net and equation pairs are stored in a map data structure called `circuit`.
2. Reading Fault Information:
   - Similar to reading the circuit file, the fault file is read line by line.
   - Empty lines and comments are skipped.
   - Each line is split into a parameter and a value using the '=' symbol as the delimiter.
   - Leading and trailing whitespaces are removed from the parameter and value strings.
   - The fault location and type are stored in variables `location` and `type`, respectively.
3. Preprocessing Circuit Information:
   - The original circuit map is iterated to modify the keys and values.
   - For each key in the circuit map, if it starts with the string "net_", it is updated by removing the "net_" prefix.
   - The associated values are processed to remove any occurrence of the "net_" prefix as well.
   - The updated key and modified values are stored in a new circuit map called `circuitnew`.
4. Calculating Outputs for Sample Tests:
   - The program defines a helper function called `calculate1` that takes two integers and an operator string ('&', '|', or '^').
   - It performs the logical operation on the two integers based on the operator and returns the result.
   - The program defines a helper function called `appendSolutionMap` that takes various parameters including the `solution` map, the `circuit` map, the sample tests, and flags for ideal and faulty scenarios.
   - This function is responsible for calculating and updating the output values for each net in the circuit based on the sample tests and scenario flags.
   - It iterates over the circuit elements and processes each equation to calculate the output value.
   - The calculated values are stored in the `solution` map, which has keys corresponding to the nets and values as pairs of ideal and faulty outputs.
5. Iterating over Sample Tests and Output Generation:
   - The program defines variables for ideal and faulty scenarios, initially set to true and false, respectively.
   - It defines a `solution` map to store the output values.
   - The program iterates over the sample tests and the circuit elements for each test.
   - The `appendSolutionMap` function is called to update the `solution` map for each net in the circuit.
   - After completing both the ideal and faulty scenarios, the program checks if the ideal and faulty outputs for the "Z" net differ.
   - If they differ, it writes the test inputs to an output file named "output.txt".
6. Conclusion:
   - The program loops through the sample tests, performing calculations on the circuit based on the inputs.
   - It handles both ideal and faulty scenarios, storing the output values in the `solution` map.
   - The algorithm identifies test inputs that produce different ideal and faulty outputs for the "Z" net and writes them to an output file.
   - The code follows a structured approach, utilizing maps and helper functions to organize and process the circuit information and sample tests efficiently.

