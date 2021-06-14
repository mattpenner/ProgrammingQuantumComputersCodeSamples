# ProgrammingQuantumComputersCodeSamples
QCEngine experiments to go along with Programming Quantum Computers O'Reilly book

Note: Copy and paste the experiments into the quantum simulator at [https://oreilly-qc.github.io](https://oreilly-qc.github.io).  


## Chapter 6
### Example 6-1
Based on the original 6-1 but with labels for clarity
```js
// Programming Quantum Computers
//   by Eric Johnston, Nic Harrigan and Mercedes Gimeno-Segovia
//   O'Reilly Media

// To run this online, go to http://oreilly-qc.github.io?p=6-1

var number_to_flip = 3;
var number_of_iterations = 4;

var num_qubits = 4;
qc.reset(num_qubits);
var reg = qint.new(num_qubits, 'reg')
reg.write(0);
reg.hadamard();

for (var i = 0; i < number_of_iterations; ++i)
{
    qc.nop();
    
    // Flip the marked value
    qc.label("Flip|Mirror #" + i);
    reg.not(~number_to_flip);
    reg.cphase(180);
    reg.not(~number_to_flip);

    reg.Grover();

    // Peek at the probability
    prob = reg.peekProbability(number_to_flip);
    qc.label();
}
```
