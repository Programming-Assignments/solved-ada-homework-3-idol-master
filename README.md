Download Link: https://assignmentchef.com/product/solved-ada-homework-3-idol-master
<br>
<strong>Problem A – Idol Master! (Programming) </strong>

<strong>Problem Description</strong>

<strong>The story. </strong>As we all know, students in the NΠU CSIE department often idolize peers whom they look up to. Due to this phenomenon, WillyPillow decides to design a game called <em>Idol Master!</em>. In the game, each character either has the character it admires the most as its idol or has no idols. In the source code, each character is represented by the following structure:

struct Character {

// The character’s idol, null if empty. std::shared_ptr&lt;Character&gt; idol;

// Other data related to the character. CharacterData data;

};

Introduced in C++11, std::shared ptr is a smart pointer supporting reference counting. Specifically, an instance of the pointer tracks the number of its existing copies, and destructs the referenced object if the number falls to zero.

WillyPillow has a list of characters and their corresponding idols together with a list of characters that appears in a certain scene. (Due to the nature of the scene, it is guaranteed that no character in it is the idol of another character.) However, the memory usage of his game is too high, so he needs to remove some characters from the scene. As he wants to compare how much memory he can save by removing different sets of characters, he needs to know the number of character objects that can be destructed, i.e., its corresponding character is destroyed or all character objects that link to it are destructed, if we remove a given set of characters.

<strong>Problem formulation. </strong>Formally speaking, we say a vertex with a zero in-degree is <em>not referenced </em>and shall be removed. A vertex is <em>destructed </em>if it is removed either manually or due to being <em>nonreferenced</em>.

You are given a directed graph <em>G </em>in which the out-degree of each vertex is at most 1 <a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>, and multiple queries on the same graph <em>G</em>. Each query results in a new graph <em>G</em><sup>0 </sup>that is constructed by removing a set of vertices <em>X </em>and their outgoing edges on <em>G</em>. You can assume that all vertices in <em>X </em>have no incoming edges. Please implement a program to compute the number of vertices that are <em>destructed </em>on <em>G</em><sup>0 </sup>for each query.

Note that <em>destructing </em>one vertex may cause another vertex to become <em>non-referenced </em>and be <em>destructed </em>as well. In addition, if a vertex not in <em>X </em>already has a zero in-degree in <em>G</em>, then it is <em>not destructed </em>(one can imagine that they are connected to by a special hidden vertex).

<strong>Input Format</strong>

The first line contains the number of vertices, <em>N</em>.

The second line consists of <em>N </em>integers. The <em>i</em>-th integer, <em>p<sub>i </sub></em>(0 ≤ <em>p<sub>i </sub></em>≤ <em>N</em>) indicates that there is an edge <em>i </em>→ <em>p<sub>i</sub></em>. Notably, <em>p<sub>i </sub></em>= 0 if the out-degree of <em>i </em>is zero.

The third line consists of the number of queries <em>Q</em>.

<em>Q </em>lines follow, the <em>i</em>-th of which starts with an integer <em>x<sub>i </sub></em>(<em>x<sub>i </sub></em>≥ 1), denoting the number of vertices to be removed, and is followed by <em>x<sub>i </sub></em>integers, denoting the set of vertices to be removed.

<strong>Test Group 0:                                                                     Test Group 2 :</strong>

<ul>

 <li>Sample Input <em>N </em>≤ 2<sup>18</sup></li>

 <li><sup>P</sup><em>x<sub>i </sub></em>≤ 2<em>N</em></li>

</ul>

<strong>Test Group 1 (15%):</strong>

<ul>

 <li><em>N </em>≤ 2<sup>13</sup></li>

 <li><sup>P</sup><em>x<sub>i </sub></em>≤ 2<em>N</em></li>

</ul>

<strong>Output Format</strong>

For each query, output a line indicating the number of vertices that can be deleted according to the rules above.

<strong>Sample Input 1                                                        Sample Output 1</strong>

4                                                                                                            1

4 2 4 1

1

1 3

<strong>Sample Input 2                                                        Sample Output 2</strong>

8                                                                                                            3

1 6 6 6 1 2 3 4                                                                                  4

12                                                                                                         1

<h1>2 5 7                                                                                                    2</h1>

<h1>2 7 8                                                                                                    2</h1>

1 5                                                                                                        3

<h1>1 8                                                                                                        1</h1>

<ul>

 <li>8 4</li>

 <li>5 7 2</li>

 <li>5 1</li>

 <li>7 8 2</li>

</ul>

1 7                                                                                                        1

1 5

1 8

<h1>1 5</h1>

<strong>Problem B – Traveling Pony Problem (Programming) (15 points)</strong>

<strong>Problem Description</strong>

A little pony is traveling in a city. He starts from his home <em>s </em>and goes to the destination <em>t</em>. However, each road in the city has two values <em>d<sub>i </sub></em>and <em>l<sub>i</sub></em>, the length of the road and the level of danger. To ensure his safety, the pony needs to be well-prepared before the trip. He has a non-negative value <em>L </em>indicating the amount of protection. To pass a road safely, he needs to ensure that <em>L </em>≥ <em>l<sub>i</sub></em>. Since the protection is expensive, he wants to minimize the amount of protection. Your goal is to calculate the shortest path under the condition that a minimum amount of protection is needed.

<strong>Input</strong>

The map can be considered as an undirected graph. Each road is an edge on the graph. And the pony travels from a vertex <em>s</em>, which is his home, to a vertex <em>t</em>, which is the destination.

The first line of the input consists of 2 integers <em>n</em>, <em>m</em>, which indicate the number of vertices and the number of edges. The second line consists of 2 integers <em>s </em>and <em>t</em>, indicating pony’s home and the destination. On the follow <em>m </em>lines, there are 4 integers <em>x<sub>i</sub></em>, <em>y<sub>i</sub></em>, <em>d<sub>i</sub></em>, and <em>l<sub>i</sub></em>, which means an edge connecting vertices <em>x<sub>i </sub></em>and <em>y<sub>i</sub></em>; the distance between <em>x<sub>i </sub></em>and <em>y<sub>i </sub></em>is <em>d<sub>i</sub></em>, and the level of danger is <em>l<sub>i</sub></em>.

<ul>

 <li>2 ≤ <em>n </em>≤ 200000</li>

 <li>1 ≤ <em>m </em>≤ 500000</li>

 <li>0 ≤ <em>s,t &lt; n</em></li>

 <li>0 ≤ <em>x<sub>i</sub>,y<sub>i </sub>&lt; n</em>, <em>x<sub>i </sub></em>6= <em>y<sub>i </sub></em>for 0 ≤ <em>i &lt; m</em></li>

 <li>There is no two edges connecting a same pair of vertices.</li>

 <li>0 ≤ <em>d<sub>i</sub>,l<sub>i </sub></em>≤ 10<sup>9</sup></li>

 <li>The graph is connected.</li>

</ul>

<strong>Output</strong>

You need to output two non-negative integers <em>D </em>and <em>L</em>. <em>D </em>is the length of shortest path if the pony only goes through roads whose danger level ≤ <em>L</em>; <em>L </em>is the minimum amount of protection needed that the pony can arrive the destination safely.

<strong>Subtask 1 (30 %)</strong>

<ul>

 <li><em>l</em><sub>0 </sub>= <em>l</em><sub>1 </sub>= <em>… </em>= <em>l<sub>m</sub></em>−<sub>1</sub></li>

</ul>

<strong>Subtask 2 (30 %)</strong>

<ul>

 <li><em>l<sub>i </sub></em>6= <em>l<sub>j </sub></em>for 0 ≤ <em>i,j &lt; m </em>and <em>i </em>6= <em>j</em></li>

</ul>

<strong>Subtask 3 (40 %)</strong>

<ul>

 <li>No other constraints.</li>

</ul>




<strong>Sample Input 1</strong>

5 5

0 4

<ul>

 <li>1 1 3</li>

 <li>2 2 1</li>

 <li>3 1 2</li>

 <li>4 1 3</li>

</ul>

0 4 1 4

<strong>Sample Output 1</strong>

5 3

<strong>Sample Input 2</strong>

5 5

0 4

0 1 1 3

<ul>

 <li>2 2 2</li>

 <li>3 1 4</li>

 <li>3 2 2</li>

 <li>4 2 5</li>

</ul>

<strong>Sample Output 2</strong>

<ul>

 <li>5</li>

</ul>




<strong>Problem C – Magic Song (Programming) (20 points)</strong>

<strong>Problem Description</strong>

You have a collection of songs. Each song contains some “jump points”, and when a song plays to a jump point, you can optionally jump to another song. Your goal is to determine how to jump between songs so as to maximize the length of played music.

<strong>Input</strong>

The first line of the input file contains an integer indicating <em>T</em>, the number test cases.

For each test case, the first line contains two integers, <em>N </em>and <em>M</em>, indicating the number of songs and the number of total “jump points”, respectively. The second line contains <em>N </em>integers separated by spaces, <em>a</em><sub>1</sub><em>,a</em><sub>2</sub><em>…</em>, <em>a<sub>i</sub></em>, indicating the length of <em>i</em>-th song (in terms of the number of notes). The following <em>M </em>lines, each of which contains four integers separated by spaces, <em>s</em><sub>1</sub><em>,t</em><sub>1</sub><em>,s</em><sub>2</sub><em>,t</em><sub>2</sub>, indicating that the ending of the <em>t</em><sub>1</sub>-th note of the <em>s</em><sub>1</sub>-th song could jump to the beginning of <em>t</em><sub>2</sub>-th note of the <em>s</em><sub>2</sub>-th song.

<ul>

 <li>1 ≤ <em>T </em>≤ 10</li>

 <li>1 ≤ <em>N </em>≤ 10<sup>5</sup></li>

 <li>0 ≤ <em>M </em>≤ 5 × 10<sup>5</sup></li>

 <li>1 ≤ <em>a<sub>i </sub></em>≤ 10<sup>8</sup></li>

 <li>1 ≤ <em>s</em><sub>1</sub><em>,s</em><sub>2 </sub>≤ <em>N</em></li>

 <li>1 ≤ <em>t</em><sub>1 </sub>≤ <em>a<sub>s</sub></em><sub>1</sub></li>

 <li>1 ≤ <em>t</em><sub>2 </sub>≤ <em>a<sub>s</sub></em><sub>2</sub></li>

</ul>

<strong>Test Group 1 (30 %)                                                                   Test Group 2 (30 %)</strong>

<ul>

 <li>1 ≤ <em>N,M </em>≤ 10<sup>4</sup></li>

</ul>

<strong>Test Group 3 (40 %)</strong>

<ul>

 <li>1 ≤ <em>N,M </em>≤ 10<sup>3</sup></li>

 <li>1 ≤ <em>a<sub>i </sub></em>≤ 10<sup>3 </sup> No other constraints.</li>

</ul>

<strong>Output</strong>

Please output an integer indicating the maximum number of notes that you can play. If the music can be played forever, output “LoveLive!”.

<strong>Sample Input 1</strong>

<h1>1</h1>

3 3

10 10 10

<ul>

 <li>5 2 3</li>

 <li>7 1 6</li>

</ul>

2 3 3 5

<strong>Sample Output 1</strong>

15

<strong>Sample Input 2</strong>

1

1 1

10

1 6 1 3

<strong>Sample Output 2</strong>

LoveLive!

<strong>Hint</strong>

Some example of suite: https://www.youtube.com/watch?v=95tLMjeK0kw https://www.bilibili.com/video/av5986635

<strong>Problem D – Basic Problems in Graphs (Hand-Written) (20 points)</strong>

<ol>

 <li>Give one example of a directed graph with four vertices, A, B, C, and D, such that both depthfirst search and breadth-first search discover the vertices in the <strong>same order </strong>when starting at A. Give one example of a directed graph where DFS and BFS discover the vertices in <strong>different orders </strong>when starting at A. (“Discover” means the time that the algorithm first reaches the vertex, when the vertex color becomes gray in CLRS textbook.) You can assume that both DFS and BFS iterate over outgoing neighbors in an alphabetical order. (4 points, 2 points for each example)</li>

 <li>Prove or disprove that the minimum spanning tree is the same as the shortest path tree. Please give one example to explain your proof. (You need to show 3 graphs, 1 for the original graph, 1 for the shortest path tree on that graph, and 1 for the minimum spanning tree on that graph. Note that the number of vertices in your graph should be no greater than 5.) (4 points)</li>

 <li>We are given a network of <em>V </em>cities and <em>E </em> All roads are one-way, i.e., if a road goes from the city <em>u </em>to the city <em>v</em>, then there will be no roads from <em>v </em>to <em>u</em>. In addition, the roads would <strong>not form any cycle</strong>. That is, you cannot start from a city <em>v</em>, go through several cities, and go back to <em>v</em>. Finally, we assume that there is a capital that can go to all other cities in the network.</li>

</ol>

We want to compute the minimum number of days for a tourist to go from the capital to each non-capital city. When a tourist encounters a city <em>v</em>, he will spend <em>c</em>(<em>v</em>) <em>&gt; </em>0 days to visit all attractions in <em>v</em>. When a tourist goes from the city <em>u </em>to the city <em>v</em>, he will spend <em>r</em>(<em>u,v</em>) <em>&gt; </em>0 days on the road. Now given the function <em>c </em>for all cities, and the function <em>r </em>for all roads, please compute the minimum number of days for a tourist to go from the capital to each non-capital city. We use <em>M</em>(<em>v</em>) to denote this minimum number of days from the capital to a city <em>v</em>. We illustrate the problem with an example of four cities <em>A</em>, <em>B</em>, <em>C</em>, <em>D </em>and four roads. Let <em>A </em>be the capital and <em>c</em>(<em>A</em>) = <em>c</em>(<em>B</em>) = <em>c</em>(<em>C</em>) = <em>c</em>(<em>D</em>) = 1, and <em>r</em>(<em>A,B</em>) = <em>r</em>(<em>A,C</em>) = <em>r</em>(<em>B,D</em>) = 2, and <em>r</em>(<em>C,D</em>) = 10. Then <em>M</em>(<em>D</em>) = <em>c</em>(<em>A</em>) + <em>r</em>(<em>A,B</em>) + <em>c</em>(<em>B</em>) + <em>r</em>(<em>B,D</em>) + <em>c</em>(<em>D</em>) = 7. Similarly <em>M</em>(<em>B</em>) = <em>M</em>(<em>C</em>) = 4.

<ul>

 <li>Please derive an <em>optimal </em>algorithm to compute the function <em>M </em>for all cities other than the capital. (6 points)</li>

 <li>Please analyze the time complexity of your algorithm and prove that it is correct. (You need to show why your algorithm gives the minimum number of days from the capital to a city <em>v</em>.) (6 points)</li>

</ul>

<strong>Problem E – Mailing Fees (Hand-Written) (22 points)</strong>

Your computer bought on the Double Eleventh Day has broken, so you have to send it to a factory to repair. There are <em>N </em>factories and <em>E </em>roads, and you need to send your device to one of them. When you send it to any factory, you have to pay the mailing fees. As shown in the following graph, the starting position is the node 0; each vertex represents one factory, and an edge between two factories shows the mailing fee. You can ask a factory to transfer your computer to another one, and you still have to pay the mailing fees. Note that you need to pay the mailing fees for the factory sending back your device too. Your goal is to find out the minimum amount you have to spend on the mailing fee for a round trip to and from each factory.

In the example below: there are 8 factories (nodes 1 to 9) and you are at the location 0. The weights of edges indicate the mailing fees you have to pay for sending your computer.

The answer for the above example is

<table width="257">

 <tbody>

  <tr>

   <td width="61">factory</td>

   <td width="197">Mailing fees from the source</td>

  </tr>

  <tr>

   <td width="61">1</td>

   <td width="197">8</td>

  </tr>

  <tr>

   <td width="61">2</td>

   <td width="197">24</td>

  </tr>

  <tr>

   <td width="61">3</td>

   <td width="197">38</td>

  </tr>

  <tr>

   <td width="61">4</td>

   <td width="197">42</td>

  </tr>

  <tr>

   <td width="61">5</td>

   <td width="197">22</td>

  </tr>

  <tr>

   <td width="61">6</td>

   <td width="197">18</td>

  </tr>

  <tr>

   <td width="61">7</td>

   <td width="197">16</td>

  </tr>

  <tr>

   <td width="61">8</td>

   <td width="197">28</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>(4pts) Please write down a pseudo code to solve the problem.</li>

 <li>(5pts) Due to some unexpected reasons, the paths to the factory change from bi-directional to uni-directional (as shown in the figure below). Please use the function you created above and explain how you can find the lowest mailing fee for a round trip to and from each factory. Your algorithm should run in <em>O</em>(<em>ElogE</em>) time complexity. Briefly explain the correctness and why your algorithm meets the time complexity requirement.</li>

</ul>

<em>Note: You do not have to write a pseudo code for this question.</em>

<ul>

 <li>(4pts) Now there are some offers provided by factories; some mailing fees change to negative, meaning that you can “earn” some money when using that path for sending your device. Please write a pseudo code to solve this problem. If there exists a cycle that you can actually “earn” money, please output “I am rich!”</li>

</ul>

<em>Y </em>our algorithm should run in <em>O</em>(<em>N </em>∗ <em>E</em>) time complexity (<em>E </em>is the number of edges). Briefly explain the correctness and why your algorithm meets the time complexity requirement.

<ul>

 <li>(3pts) Briefly compare these two algorithms you use in subproblem 2 and 3 (time and space complexity) and discuss their advantages and disadvantages.</li>

 <li>(6pts) Now each factory has a reliability value, we define a “trustful cycle” if the ratio of total reliability to total mailing fees is strictly larger than <em>K </em>(<em>K </em>∈ N). You can assume that there are no negative mailing fees for this subproblem. For example, in the example below, <em>K </em>= 10, the simple cycle route 30 → 40 → 20 → 30 has the total reliability 30 + 40 + 20 = 90, and total mailing fees 2 + 3 + 1 = 6. The ratio between them is 15, which is larger than <em>K</em>.</li>

</ul>

Please provide an algorithm to find if there exists a “trustful cycle”. Your algorithm should run in <em>O</em>(<em>N </em>∗<em>E</em>) time complexity. Briefly explain the correctness and why your algorithm meets the time complexity requirement.

Hint: you can try reweighting the graph.

<strong>Problem F – Gaussian is Too Slow (Hand-Written) (8 points)</strong>

There are <em>N </em>unknown variables, namely <em>x</em><sub>1</sub><em>…x<sub>n</sub></em>. Your task is to solve all variables by picking <em>N </em>equations from the “equation pool” below and make sure your solution of <em>x </em>is non-singular. The following describes the equations’ characteristics inside the equation pool:

<ul>

 <li>all coefficients for the unknown variables are 1. (ex: <em>x</em><sub>1 </sub>+<em>x</em><sub>2 </sub>is in the equation pool but <em>x</em><sub>1 </sub>+2<em>x</em><sub>2 </sub>is not.)</li>

 <li>all variables inside an equation are consecutive. (ex: <em>x</em><sub>2 </sub>+ <em>x</em><sub>3 </sub>+ <em>x</em><sub>4 </sub>and <em>x</em><sub>3 </sub>are in the equation pool but <em>x</em><sub>2 </sub>+ <em>x</em><sub>4 </sub>and <em>x</em><sub>6 </sub>+ <em>x</em><sub>1 </sub>are not).</li>

 <li>each equation has their own “cost”. (ex: equation <em>x</em><sub>1 </sub>+ <em>x</em><sub>2 </sub>cost is 6, <em>x</em><sub>2 </sub>+ <em>x</em><sub>3 </sub>is 3 )</li>

 <li>you can assume all functions you choose will have a consistent solution for <em>x</em>.</li>

</ul>

Your task is to solve all variables <em>x </em>by picking <em>N </em>equations so that the total cost can be minimized. As an example <em>N </em>= 3 and the “equation pool”:

<table width="137">

 <tbody>

  <tr>

   <td width="96">equation</td>

   <td width="42">cost</td>

  </tr>

  <tr>

   <td width="96"><em>x</em><sub>1</sub></td>

   <td width="42">1</td>

  </tr>

  <tr>

   <td width="96"><em>x</em>1 + <em>x</em>2</td>

   <td width="42">5</td>

  </tr>

  <tr>

   <td width="96"><em>x</em>1 + <em>x</em>2 + <em>x</em>3</td>

   <td width="42">2</td>

  </tr>

  <tr>

   <td width="96"><em>x</em><sub>2</sub></td>

   <td width="42">6</td>

  </tr>

  <tr>

   <td width="96"><em>x</em>2 + <em>x</em>3</td>

   <td width="42">3</td>

  </tr>

  <tr>

   <td width="96"><em>x</em><sub>3</sub></td>

   <td width="42">4</td>

  </tr>

 </tbody>

</table>

The solution for this example is to pick the equations <em>x</em><sub>1</sub>, <em>x</em><sub>1 </sub>+ <em>x</em><sub>2 </sub>+ <em>x</em><sub>3 </sub>and <em>x</em><sub>3</sub>. Thus, the total cost will be 1 + 2 + 4 = 7.

Please reduce this problem to any algorithm you learned before (for example: Dijkstra, BellmanFord, Warshall, Kruskal, DP,…etc). Your algorithm should run in <em>O</em>(<em>N</em><sup>2</sup>) time complexity. Briefly explain the correctness and why your algorithm meets the time complexity requirement.

Hint: you might need to add an extra node for this question.

<em>Note: You do not need to write a pseudo code for this question. You just have to describe how you reduce this problem to any algorithm.</em>

<a href="#_ftnref1" name="_ftn1">[1]</a> This is known as a directed pseudoforest.