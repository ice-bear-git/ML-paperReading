# CS 1502 Midterm -- Typable equation sheet

## State Machine
1. DFA -- GNFA -- RegExp -- NFA
2. NFA -- DFA -- GNFA -- RegExp
3. RegExp -- NFA -- DFA

### Formal Defination of *DFA M* and *NFA N*
* [Same] for 5-tuple (Q, Sigma, delta, q_0, F):
	- Q is a **set** called "States": {q_0, q_1, q_2}
	- Sigma is **set** called "Alphabet": {a, b}
	- delta means "Transition function": delta(qi, a)
	- q_0 is A **single** "Start State": q_0
	- F is a **set** of "Accept States": {q_3}

* Difference on "Transition function"
	- **Value/Set**: For DFA N, delta(q0, a)= q1; For NFA N, delta(q0, a)= {q1}  or {q1, q2} or "Empty Set".
	- **Number of Columns**: DFA has {1, 2} 2 cols; while **NFA has {1, 2, empty} 3 cols!**
	

### Equivalent DFA of every NFA
1. Q' = P(Q): 	say Q = {1, 2}; Then Q' = {empty, {1}, {2}, {1,2}}
2. Table of "Transition function" has as many rows as items inside Q' -- Using union to combine output states **set**.
3. **q_0'** becomes a **Set**!!! Contain all states in Q' that contains original q_0: e.g. q_0'=E(1) = {1,3} or {1}
4. F' becomes a **larger set** -- Contain all states in Q' that contains original items in F

### RegExp to NFA
![Basic](https://github.com/ice-bear-git/ML-paperReading/blob/main/Visualization/CS1502_1.png)
If a language is described by a RegExp -- it must be regular
![Example 1](https://github.com/ice-bear-git/ML-paperReading/blob/main/Visualization/CS1502_2.png)
Consider 
![Example 2](https://github.com/ice-bear-git/ML-paperReading/blob/main/Visualization/CS1502_3.png)

## Turing Machine
* 当cur state已经在最左是，move left只会让它保持原始位置。所以，要在开始时，人为标记**起始位置为x or #**
* "Transition function": **delta(q_i, 0) = (q_j, 1, L)** -- 把右侧的0写成1，然后状态从qi到qj，并且把qj向左移动一位
* As looping exist, L(M) = A won't reject all string that is out of A.
* **Recognizable**: Accept all string in A, reject or looping on all string out of A
* **Decideable**: A **Recognizable** TM that is **without looping**
	- Usually, Without looping, those TM is called "deciders" directly.




## Proof by Pumping Lemma
Sigma = {0}  
B = {0^(i^2) | i>=0}

Assume that B is regular. SInce B is regular, the pumping lemma says that for any string s in B of length at least p, s can be divided into s = xyz and satisfy these conditions:  
1. xy^iz in B for any i >= 0
2. |y| > 0
3. |xy| <= p

Let s = 0^(p^2). Since s starts with p^2 0s, which is gearter than p. To satisfy condition 3, x and y contain nothing but 0s. In other words,  
x = 0^j for j >= 0  
y = 0^k for k > 0 (>0 to satisfy condition 2)  
z = 0^(p^2 - (j + k))  
Consider xy^2z = (0^j)(0^k)(0^k)(0^(p^2 - (j+k))) = 0^(p^2 + k)  
For 0^(p^2 + k) to be in B, (p^2 + k) must be i^2 for some i. In other words, as k > 0, (p^2 + k) should be (p+1)^2:  

(p^2 + k) = (p+1)^2  
p^2 + k = p^2 + 2p + 1
k = 2p + 1

However, since k must be within 1 <= k <= p, there is no k. A contradiction shows up. Thus, the language B is not regular.