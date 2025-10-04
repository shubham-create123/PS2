# PS2

This ps is based on the famous deutsch-jozsa algorithm we are given a black box funtion which takes three bits string as input and return one bit as output.
so there are a total of eight possible combination of inputs so the people gets divided into groups who belives that the funciton is either: 


1) balenced function: gives 0 for half and 1 for the other half of input combinations
2) constant function: gives either 0 or 1 for all the possible input combinations


The classical way to solve this problem involve hit and trial by checking each and every possible combination of inputs and examining all the corresponding outputs to verify wheather the function is constand or balenced.
But we are not doing it the classical way so we can use quantum computing method to examine all the combination all at once using the deutsch-jozsa algorithm.

firstly i will talk about the algorithn and all the conceptual understanding part and then i will move towards how i implement it in code {tbh i am not very familiar with coding and faced many difficulties, the code written is with the help of qiskit implementation section of IBM and a bit help from gpt, i want to grow more on this section)

fistly we need two sets of qubits 1: input qubits (in this case it is 3 as mentioned in the question) and 2: an ancilla qubit which will be used in the phase kickback mechanism.
Then we pass the ancilla qubit with the pauli-X gate which convert it into a |1> and then pass it to a hadamard gate which further convert it into |-> which is needed for the phase kickback mechanism.
Nwxt step we apply hadamard gate to every input qubit all at once to create superposition. |0> -----> |+>.

Then we actually use the function on the entire system, the oracle function works by transforming the state  ∣x⟩∣y⟩ to ∣x⟩∣y⊕f(x)⟩.
Now the mechanism of phase kickback comes into picture: 

If f(x)=0, the ancilla state becomes ∣y⊕0⟩, which is just ∣y⟩. So, ∣−⟩ is left unchanged.
If f(x)=1, the ancilla state becomes ∣y⊕1⟩. Applying this to ∣−⟩ gives us −∣−⟩. The state is unchanged, but it has acquired a negative phase.

