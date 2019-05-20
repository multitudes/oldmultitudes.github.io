---
layout: post
title:  "Quantum Country"
date:   2010-04-09
categories: iOS, developer
comments: true
published: true
---


<div class="message">
"Sure you are joking!" 
<br><cite>Freely taken from the Richard Feynmann biography</cite>
</div>

![image](/assets/img/CSharpScriptingPost.jpg)

This is a draft.  
(This are my own notes about the "Quantum Country" article written by Matushek and Nielsen, see sources).  
Here on Earth, the principal originator of computers was the English mathematician Alan Turing. In his paper  “On Computable Numbers, with an Application to the Entscheidungsproblem” (published in 1936), he was attacking a problem about the nature of mathematics posed by the German mathematician David Hilbert in 1928.
Hilbert’s problem asked whether a general algorithm exists, which a mathematician can follow which would let them figure out whether any given mathematical statement is provable.
Attacking Hilbert’s problem forced Turing to precise exactly what was meant by an algorithm. 
To do this, Turing described what we now call a Turing machine: a single, universal programmable computing device that Turing argued could perform any algorithm whatsoever. Turing’s machine became the gold standard: an algorithm was what we could perform on a Turing machine.
David Deutsch suggested a deeper approach to the problem of defining what is meant by an algorithm.
Algorithms have to be performed on some kind of physical system. It can be any system.
Will aliens have computers? 
In this sense, computers aren’t just human inventions. 
They are a fundamental feature of the universe, the answer to a simple and profound question about how the universe works. 
And they have likely been discovered over and over again by many alien intelligences. 
Deutsch observed that ordinary, everyday computers based on Turing’s model have a lot of trouble simulating quantum mechanical systems (Researchers such as Yu Manin and Richard Feynman had previously observed this, and as a result had speculated about computers based on quantum mechanics.)
To answer his question affirmatively, Deutsch was forced to invent a new type of computing system, a quantum computer. 
Those quantum computers can do everything conventional computers can do, but are also capable of efficiently simulating quantum-mechanical processes.

### The state of a qubit

In ordinary, everyday computers the fundamental unit of information is the bit.  
In a manner similar to the way conventional computers are made up of bits, quantum computers are made up of quantum bits, or qubits. Just like a bit, a qubit has a state. But whereas the state of a bit is a number (0 or 1) , the state of a qubit is a vector.   
* The state of a qubit is a vector in a two-dimensional vector space. This vector space is known as state space. *  

### The computational basis states

I’ve described what the state of a qubit is, but how (or whether) that’s connected to the state of a classical bit. (Henceforth we’ll use the phrase “classical bit” instead of “conventional bit”, after “classical physics”). In fact, there are two special quantum states which correspond to the 
0 and 1 states of a classical bit. The quantum state corresponding to 0 is usually denoted |0⟩.  
This special state |0⟩ is called a computational basis state.  
This notation is called the ket notation, and things like |0⟩ are called kets.  
A ket is just a vector, and when we say something is a ket, all we mean is that it’s a vector.  

there is another computational basis state, denoted |1⟩.  
which plays the same role as 1 does for a bit.  
I’ve been talking about quantum states as two-dimensional vectors. What I didn’t yet mention is that in general they’re complex vectors, that is, they can have complex numbers as entries.  

The discovery of quantum mechanics wasn’t a single event, but occurred over 25 years of work, from 1900 to 1925. Many Nobel prizes were won for milestones along the way. That includes Albert Einstein’s Nobel Prize, won primarily for work related to quantum mechanics (not relativity, as people sometimes assume).  

Let’s get familiar with some more nomenclature commonly used for quantum states.  

One of the most common terms is superposition.  

All they mean is that the state is a linear combination of ∣0⟩ and ∣1⟩.  

Another common term is amplitude. An amplitude is the coefficient for a particular state in superposition.  
We’ve learnt that a quantum state is a two-dimensional complex vector. Actually, it can’t be just any old vector, a fact you might have guessed from the very particular amplitudes in some of the examples above. There’s a constraint. The constraint is this: the sums of the squares of the amplitudes must be equal to 1.   
For a more general quantum state, the amplitudes can be complex numbers, The constraint is now that the sum of the squares of the amplitudes is 1.  

This is called the normalization constraint.  

Summing up all these ideas in one sentence: the quantum state of a qubit is a vector of unit length in a two-dimensional complex vector space known as state space.  


### Introducing quantum logic gates

A quantum logic gate is simply a way of manipulating quantum information.  

#### The quantum NOT gate

Historically, the notation X traces its origin to 1927, with the physicist Wolfgang Pauli. 
I’ll use the terms X gate and NOT gate interchangeably.
quantum wire

There’s a third representation for the X gate that’s worth knowing about, a representation as a 2×2 matrix

a single quantum wire:
	__________

This circuit is just a single qubit being preserved in time. To be more explicit, if some arbitrary quantum state ∣ψ⟩ is input to the circuit, then the exact same state ∣ψ⟩ is output (it’s common practice to use the Greek letter ψ to denote an arbitrary quantum state):  
In many physical systems, the quantum wire is actually one of the hardest quantum computations to implement!  
The reason is that quantum states are often incredibly fragile. If your qubit is being stored in some tiny system – perhaps a single photon or a single atom – then it’s very, very easy to disturb that state.  

#### A multi-gate quantum circuit

It’s just a circuit with two X gates in a row:  
That is, XX is the identity operation, and so the output  XX∣ψ⟩ is just the original input ∣ψ⟩.  
Composing multiple quantum gates corresponds to the operation of matrix multiplication.  
Doing matrix multiplications is a pretty common way of analyzing quantum circuits.  

#### The Hadamard gate
See in the article
H matrice representation:

#### Measuring a qubit

There is, in fact, no way to figure out α and β if they start out unknown. To put it a slightly different way, the quantum state of any system – whether it be a qubit or a some other system – is not directly observable.  

See article

So the way a quantum computation works is that we manipulate a quantum state using a series of quantum gates, and then at the end of the computation (typically) we do a measurement to read out the result of the computation. If our quantum computer is just a single qubit, then that result will be a single classical bit. If, as is more usually the case, it’s multiple qubits, then the measurement result will be multiple classical bits.  
A fundamental fact about this measurement process is that it disturbs the state of the quantum system. In particular, it doesn’t just leave the quantum state alone. After the measurement, if you get the outcome 0 then the state of the qubit afterwards (the “posterior state”) is the computational basis state |0⟩.  
On the other hand, if you get the outcome 1 then the posterior state of the qubit is the computational basis state ∣1⟩.  

A key point to note is that after the measurement, no matter what the outcome, α and β are gone.   
it means you can’t store an infinite amount of classical information in a qubit. After all, α is a complex number, and you could imagine storing lots of classical bits in the binary expansion of the real component of α. If there was some experimental way you could measure the value of α exactly, then you could extract that classical information. But without a way of measuring α that’s not possible.  

#### General single-qubit gates

A general single-qubit gate works similarly. In particular, a general single-qubit gate can be represented as a 2×2 unitary matrix, U.  
What does it mean for a matrix U to be unitary? It’s easiest to answer this question algebraically:  

U†U = I   

where it simply means the adjoint of U,  times U, is equal to the identity matrix. That adjoint is, recall, the complex transpose of U.  

See article  

Note that the † is also sometimes called the dagger operation, or Hermitian conjugation, or just the conjugation operation.  

The NOT gate X was introduced by the physicist Wolfgang Pauli in the early days of quantum mechanics. He introduced two other matrices, Y and Z, which are also useful quantum gates. The three gates, X,Y, and Z are known collectively as the Pauli matrices. The Y and Z gates will be useful extra tools in our toolkit of quantum gates; in terms of the earlier analogy they expand the repertoire of moves we have available to us. They’re crucial, for example, in protocols such as quantum teleportation and quantum error correction.  

See article  
These matrices are unitary, and so legitimate quantum gates.  





### Sources:




<hr>
