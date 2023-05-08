Download Link: https://assignmentchef.com/product/solved-quantum-homework-2
<br>
Prove that one can check the satisfiability of a 2-CNF (a conjunction of disjunctions, each containing 2 literals) in polynomial time.

<ol>

 <li>SAT, also known as Boolean satisfiability problem, is a problem of assigning boolean values to variables to satisfy a given boolean formula. Formula usually would be in CNF form (conjunctive normal form). This is a formula having conjunction of multiple clauses, where each clause is a disjunction of literals. Each literal is a boolean variable. 2-SAT (2-satisfiability) is a restriction of the SAT problem, in 2-SAT every clause has atmost up to two literals.</li>

</ol>

(<em>a </em>∨ ¬<em>b</em>) ∧ (¬<em>a </em>∨ <em>b</em>) ∧ (¬<em>a </em>∨ ¬<em>b</em>) ∧ (<em>a </em>∨ ¬<em>c</em>)

<ol start="2">

 <li>Idea is to use the resolution method to convert given propositional logic (CNF), <em>F</em>, to</li>

</ol>

equivalent set of disjunction clauses <em>F</em>. Once we get the disjunctions(<em>F</em>), we look for a clause that is false to know if the given CNF is unsatisfiable. By the rule of contradiction, we check the satisfiablity by looking for false disjunctions in the given formula. For a 2-CNF, resolution method will give only clauses with 2-literals or 1-literal or empty set and this conversion is of complexity order Linear <em>O</em>(<em>n </em>+ <em>m</em>), where <em>n </em>is number of literals, <em>m </em>is number of clauses.

<ol start="3">

 <li><em>F </em>is not satisfiable if and only if <em>F </em>contains the empty clause. We call a clause, in a CNF, empty clause if it is false. To figure out the empty clause, first we need to convert the problem to a different form, the so-called implicative normal form. We create a implication graph for our formula. For each literal <em>x</em>, there will be two vertices (<em>x</em>, ¬<em>x</em>) as its edge. For the example in the point 1, below are their implications.</li>

</ol>

¬<em>a </em>⇒ ¬<em>b              a </em>⇒ <em>b              a </em>⇒ ¬<em>b               </em>¬<em>a </em>⇒ ¬<em>c</em>

<em>b </em>⇒ <em>a               </em>¬<em>b </em>⇒ ¬<em>a               b </em>⇒ ¬<em>a              c </em>⇒ <em>a</em>

<ol start="4">

 <li>Using the above implications we can draw the implication graph. 2-CNF formula <em>F </em>is unsatisfiable if and only if there exists a literal <em>x </em>such that <em>x </em>is reachable from ¬<em>x </em>and ¬<em>x </em>is reachble from <em>x </em>in the implication graph <em>G<sub>F</sub></em>. From the implications from point 3, we can say there is not direct path from <em>x<sub>i </sub></em>to ¬<em>x<sub>i </sub></em>or vice versa in the set of variables (<em>a,b,c</em>). That is no direct path between (<em>a </em>→ ¬<em>a</em>)<em>,</em>(<em>b </em>→ ¬<em>b</em>)<em>,</em>(<em>c </em>→ ¬<em>c</em>). That said, the example 2-CNF is satisfiable.</li>

 <li>To determine the paths between vertices of a Graph G, we compute <em>adjacencymatrices A</em>(<em>G</em>) for Graph <em>G</em>. Then we compute matrix <em>B<sup>k </sup></em>= <em>A</em>∨<em>I </em>where <em>I </em>is the identity matrix. We can define the operations ∨ and ∧ on Boolean matrices with usual matrix addition and multiplication respectively.</li>

 <li><em>B<sup>k </sup></em>corresponds to the existence of a path of length at most k. If there is a path between <em>x </em>and ¬<em>x</em>, then there is a path of length 6 <em>n</em>, where <em>n </em>is the number of vertices. This computation is of complexity order <em>O</em>(<em>n</em><sup>3</sup><em>logn</em>).</li>

 <li>Both the computations for resolution method and Adjacency matrices, <em>O</em>(<em>n</em>+<em>m</em>)+<em>O</em>(<em>n</em><sup>3</sup><em>logn</em>) is of the format <em>cn<sup>d</sup></em>. Thus we can say 2-CNF can be computed in polynomial time.</li>

</ol>

1

<strong>3.3.<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> </strong>Suppose we have an NP –<em>oracle </em>– a magic device that can immediately solve any instance of SAT problem for us. In other words, for any propositional formula the oracle tells whether it is satisfiable or not. Prove that there is a polynomial-time algorithm that finds a satisfying assignment to a given formula by making a polynomial number of queries to the oracle. (A similar statement is true for the Hamiltonian cycle: finding a Hamiltonian cycle in a graph is at most polynomially harder than checking for its existence)

<ol>

 <li>We have the NP – <em>oracle </em>with us which tells us if a given SAT propositional formula, <em>F</em>, is satisfiable or not. Let the set of variables in our formula be <em>x</em><a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a><em>,x</em><a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a><em>,….,x<sub>n </sub></em>and <em>x<sub>i </sub></em>be any <em>i</em>th variable in the given set. Below are the steps we follow to get the assignment for a satisfiable forumula.</li>

</ol>

<strong>Step 0: </strong>Verify the formula <em>F </em>is Satisfiable or not. If not, we do not have to look for assignment. Stop looking. If yes proceed.

<strong>Step 1: </strong>If <em>F </em>is satisfiable, select the variable <em>x<sub>i </sub></em>where <em>i </em>= 0. Assign <em>x</em><sub>0 </sub>= <em>True </em>and substitute

in the formula <em>F</em>. Let <em>F </em>be the new formula where <em>F </em>= <em>F </em>∧ <em>x<sub>i</sub></em>. Check <em>F </em>for satisfiablity using

<em>NP </em>− <em>oracle</em>. If <em>F </em>is satisfiable let <em>F </em>= <em>F </em>and repeat the step for next variables <em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>…x<sub>n</sub></em>. If <em>F </em>is not satisfiable, proceed to step2.

<strong>Step 2: </strong>If <em>F</em>, from step1, is not satisfiable, assign <em>x</em><sub>0 </sub>= <em>False,F </em>= <em>F </em>∧ ¬<em>x<sub>i </sub></em>and <em>F </em>= <em>F </em>and proceed for next variables <em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>…x<sub>n</sub></em>.

<strong>Step 3: </strong>Using above steps, we determine values for all the variables such that <em>F </em>is satisfiable, to get the final satisfying assignment for <em>F</em>.

<a href="#_ftnref1" name="_ftn1">[1]</a> <strong>.8. </strong>Prove that the predicate ”x is the binary representation of a composite integer” belongs to NP.

<a href="#_ftnref2" name="_ftn2">[2]</a> <strong>. </strong>A number <em>S </em>is composite if it has a factor <em>t </em>and <em>t &lt; s</em>. A non-deterministic Turing machine can choose factors such that there exists 1 <em>&lt; t &lt; S </em>whose multiplication of the factors is our number

S.

<a href="#_ftnref3" name="_ftn3">[3]</a> <strong>. </strong>As multiplication can be done in polynomical time, we can say this process is of the below form and can say that this predicate belongs to class NP

<em>L</em>(<em>x</em>) = ∃<em>y</em>((|<em>y</em>| <em>&lt; q</em>(|<em>x</em>|)) ∧ <em>R</em>(<em>x,y</em>))

<em>L</em>(<em>x</em>) ∈ <em>NP</em>

<strong>.8. </strong>Prove that the predicate ”x is the binary representation of a composite integer” belongs to NP.

[1] <strong>. </strong>A number <em>S </em>is composite if it has a factor <em>t </em>and <em>t &lt; s</em>. A non-deterministic Turing machine can choose factors such that there exists 1 <em>&lt; t &lt; S </em>whose multiplication of the factors is our number

S.

[1] <strong>. </strong>As multiplication can be done in polynomical time, we can say this process is of the below form and can say that this predicate belongs to class NP

<em>L</em>(<em>x</em>) = ∃<em>y</em>((|<em>y</em>| <em>&lt; q</em>(|<em>x</em>|)) ∧ <em>R</em>(<em>x,y</em>))

<em>L</em>(<em>x</em>) ∈ <em>NP</em>

<ol>

 <li>We can see from above steps, we query (<em>n </em>+ 1) times which is of the polynomial time.</li>

</ol>