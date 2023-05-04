Download Link: https://assignmentchef.com/product/solved-csci3180-assignment-4-logic-programming-and-ml-functional-programming
<br>
Declarative programming is a programming paradigm that emphasises the expression of “what” the problem is over “how” to solve the problem. You will gain experience of declarative programming with Prolog (Logic Programming) and ML (Functional Programming) in this assignment.

You are supposed to test your work on the machine solar1.cse.cuhk.edu.hk using

<ul>

 <li>SICStus 3.12.7</li>

 <li>Standard ML of New Jersey, Version 110.0.7</li>

</ul>

They can be invoked using the commands sics and sml respectively.

1           Logic Programming

Implement the predicates or queries of the following problems in a Prolog program file named “asg4.pl”, and recall the successor notation s() to represent natural numbers in this task. You should clearly indicate using <em>comments </em>the corresponding question number of each problem.

<ol>

 <li>Recall the list operations taught in lectures and tutorials.

  <ul>

   <li>Define element last(X, L) which is true if the last element in list L is X. Example:</li>

  </ul></li>

</ol>

?- element last(e, [a,b,c,d,e]). yes

<ul>

 <li>Define element n(X, L, N) which is true if the N-th element in list L is X. Example:</li>

</ul>

?- element n(c, [a,b,c,d,e], s(s(s(0)))). yes

<ul>

 <li>Define remove n(X, L1, N, L2) which is true if the resulting list L2 is obtained from L1 by removing the N-th element, and X is the removed element. Example:</li>

</ul>

?- remove n(X, [a,b,c,d,e], s(s(s(0))), L2).

<ul>

 <li>= c,</li>

</ul>

L2 = [a, b, d, e]

<ul>

 <li>Based on (c), give a query to find which list will become [c,b,d,e] after removing its second element “a”.</li>

 <li>Define insert n(X, L1, N, L2) which is true if the resulting list L2 is obtained by inserting X to the position before the N-th element of list L1. Example:</li>

</ul>

?- insert n(h, [a,b,c], s(s(0)), L2). L2 = [a,h,b,c]

<ul>

 <li>Define repeat three(L1, L2) which is true if the resulting list L2 has each element in list L1 repeated three times. Example:</li>

</ul>

?- repeat three([a,b,c,d,e],X).

<ul>

 <li>= [a,a,a,b,b,b,c,c,c,d,d,d,e,e,e]</li>

</ul>

<ul>

 <li>Based on (f), give a query to find which list will become [i,i,i,m,m,m,n,n,n] after repeating each element of it for three times.</li>

</ul>

<ol start="2">

 <li>A <em>multi-way tree </em>is composed of a root and a sequence of sub-trees (children), which are multi-way tree themselves. The list of sub-trees of a certain node is ordered from left to right and also called a <em>forest</em>. The root of a multi-way tree is a node containing a value. Diagrammatically, a multi-way tree consists of a set of nodes and lines connecting parents</li>

</ol>

Figure 1: An example of multi-way tree

and children. The nodes are depicted by circles with values written inside. A multi-way tree is never empty.

In Prolog, we can represent a multi-way tree by the term “mt(X, F)”, where X denotes the root and F denotes the forest of sub-trees. Please finish the following questions using the successor notation s() to represent natural numbers in this task. You can use the sum/3 predicate from the lecture.

<ul>

 <li>Represent the multi-way tree in Figure 1 as a Prolog term, with order of the sub-trees from left to right. (Hint: represent forest as a list of multi-way tree(s)).</li>

 <li>Define the predicate is tree(Term) which is true if Term represents a multi-way tree.</li>

 <li>Define the predicate num node(Tree, N) which is true if N is the number of nodes of the given multi-way tree Tree.</li>

 <li>Define sum length(Tree, L) which is true if L is the sum of lengths of all internal paths in Tree. The length of an internal path from the root node <em>r </em>to an internal node <em>n </em>is the distance from <em>r </em>to <em>n</em>. For example, the sum of lengths of all internal paths in the multi-way tree in Figure 1 is: 1 (b) + 1 (c) + 1 (d) + 2 (e) + 2 (f) + 2 (g) = 9</li>

</ul>

(i.e., s(s(s(s(s(s(s(s(s(0))))))))).

<h1>2           Functional Programming</h1>

Implement the required functions of the following problems in an ML program file named “asg4.ml”. You should clearly indicate using comments the corresponding question number of each problem.

This task involves a card game simplified from Texas Hold’em. In each round, two players will get five cards respectively. The player who has the better hand will win the game. You have to implement several ML helper functions to determine the better hand.

Please consider the following eight different hands. (We refer to the rules defined on <a href="https://www.pagat.com/poker/rules/ranking.html">https:</a>

<a href="https://www.pagat.com/poker/rules/ranking.html">//www.pagat.com/poker/rules/ranking.html</a><a href="https://www.pagat.com/poker/rules/ranking.html">.</a>)

<ul>

 <li><strong>Four of a kind</strong></li>

</ul>

Four cards of the same rank – such as four queens. The fifth card, known as the kicker, can be anything. Between two fours of a kind, the one with the higher set of four cards is higher, so 3-3-3-3-A is beaten by 4-4-4-4-2. If two players have four of a kind of the same rank, the rank of the kicker decides.

<ul>

 <li><strong>Full House</strong></li>

</ul>

This combination consists of three cards of one rank and two cards of another rank – for example three sevens and two tens. When comparing full houses, the rank of the three cards determines which is higher. For example 9-9-9-4-4 beats 8-8-8-A-A. If the threes of a kind are equal, the rank of the pairs decides.

<ul>

 <li><strong>Flush</strong></li>

</ul>

Five cards of the same suit. When comparing two flushes, the highest card determines which is higher. If the highest cards are equal then the second highest card is compared; if those are equal too, then the third highest card, and so on. For example &#x2660;K-&#x2660;J-&#x2660;9-&#x2660;3-&#x2660;2 beats &#x2666;K-&#x2666;J-&#x2666;7-&#x2666;6-&#x2666;5 because the nine beats the seven. If all five cards are equal, the flushes are equal.

<ul>

 <li><strong>Straight</strong></li>

</ul>

Five cards of mixed suits in sequence. For example &#x2660;Q-&#x2666;J-&#x2665;10-&#x2660;9-&#x2663;8. When comparing two sequences, the one with the higher ranking top card is better. Ace can count high or low in a straight, but not both at once. So A-K-Q-J-10 and 5-4-3-2-A are valid straights, but 2-A-K-Q-J is not. 5-4-3-2-A, known as a wheel, is the lowest kind of straight, the top card being the five.

<ul>

 <li><strong>Three of a Kind</strong></li>

</ul>

Three cards of the same rank plus two unequal cards. When comparing two threes of a kind the rank of the three equal cards determines which is higher. If the sets of three are of equal rank, then the higher of the two remaining cards in each hand are compared, and if those are equal, the lower odd card is compared. So for example 5-5-5-3-2 beats K-4-4-4-5, which beats Q-9-4-4-4, which beats Q-8-4-4-4.

<ul>

 <li><strong>Two Pairs</strong></li>

</ul>

A pair consists of two cards of equal rank. In a hand with two pairs, the two pairs are of different ranks (otherwise you would have four of a kind), and there is an odd card to make the hand up to five cards. When comparing hands with two pairs, the hand with the highest pair wins, irrespective of the rank of the other cards – so J-J-2-2-A beats 10-10-9-9-8 because the jacks beat the tens. If the higher pairs are equal, the lower pairs are compared, so that for example 8-8-6-6-3 beats 8-8-5-5-4. Finally, if both pairs are the same, the odd cards are compared, so Q-Q-5-5-4 beats Q-Q-5-5-3.

<ul>

 <li><strong>Pair</strong></li>

</ul>

A hand with two cards of equal rank and three cards which are different from these and from one another. When comparing two such hands, the hand with the higher pair is better – so for example 6-6-4-3-2 beats 5-5-4-3-2. If the pairs are equal, compare the highest ranking odd cards from each hand; if these are equal compare the second highest odd card, and if these are equal too compare the lowest odd cards. So J-J-9-3-2 beats J-J-8-7-3 because the 9 beats the 8.

<ul>

 <li><strong>Nothing</strong></li>

</ul>

Five cards which do not form any of the combinations listed above. The cards must all be of different ranks, not consecutive, and contain at least two different suits. When comparing two such hands, the one with the better highest card wins. If the highest cards are equal the second cards are compared; if they are equal too the third cards are compared, and so on. So A-J-9-5-3 beats A-10-9-6-4 because the jack beats the ten.

Note that cards are already sorted in <em>descending </em>order according to the rank (with A always ordered last). The order of cards of the same rank is <em>arbitrary</em>. Each card has two attributes, i.e., suit and rank. The type definition of a card in ML is shown below. The joker cards are not included in this game. To further simplify the problem, we convert all ranks to integers. i.e., A =

1, J = 11, Q = 12, and K = 13.

datatype suit = Clubs | Diamonds | Hearts | Spades;

When you implement the following functions, please use <em>pattern matching </em>as much as possible.

<ol>

 <li>Write an ML function check flush, which takes a list of five cards and returns if the hand is a flush.</li>

 <li>Write an ML function compare flush, which takes two <em>flush </em>card lists. The return value is a string selected from three candidates. <em>e.</em>, “Hand 1 wins”, “Hand 2 wins” and “This is a tie”.</li>

 <li>Write an ML function check straight, which takes a list of five cards and returns if the hand is a straight.</li>

 <li>Write an ML function compare straight, which takes two <em>straight </em>card lists. The return value is a string selected from three candidates. <em>e.</em>, “Hand 1 wins”, “Hand 2 wins” and “This is a tie”.</li>

 <li>Write an ML function count patterns, which takes a list of five cards and returns the hand type (Nothing, Pair, Two Pairs, Three of a Kind, Full House, Four of a Kind) and a list of rank-quantity pairs. Note that the list should be ordered according to the order of comparison of each type of hand.</li>

</ol>

Here are some examples to help you understand the problem:

<ul>

 <li>The card list [(Clubs, 13), (Clubs, 11), (Spades, 7), (Spades, 3), (Hearts, 2)] should return (Nothing, [(13, 1), (11, 1), (7, 1), (3, 1), (2, 1)]).</li>

 <li>The card list [(Spades, 11), (Spades, 9), (Hearts, 8), (Diamond, 8), (Diamonds, 3)] should return (Pair, [(8, 2), (11, 1), (9, 1), (3, 1)]).</li>

 <li>The card list [(Clubs, 13), (Spades, 13), (Hearts, 6), (Spades, 1), (Diamonds, 1)] should return (Two Pairs, [(13, 2), (1, 2), (6, 1)]).</li>

 <li>The card list [(Clubs, 10), (Clubs, 9), (Hearts, 9), (Spades, 9), (Spades, 3)] should return (Three of a Kind, [(9, 3), (10, 1), (3, 1)]).</li>

 <li>The card list [(Diamonds, 6), (Clubs, 6), (Spades, 6), (Spades, 4), (Diamonds, 4)] should return (Full House, [(6, 3), (4, 2)]).</li>

 <li>The card list [(Diamonds, 11), (Spades, 11), (Clubs, 11), (Hearts, 11), (Hearts, 10)] should return (Four of a Kind, [(11, 4), (10, 1)]).</li>

</ul>

<ol start="6">

 <li>Write an ML function compare count, which takes two card lists and returns a string selected from three candidates. <em>e.</em>, “Hand 1 wins”, “Hand 2 wins” and “This is a tie”. You only need to consider the remaining six cases except flush and straight, and assume that Nothing <em>&lt; </em>Pair <em>&lt; </em>Two Pairs <em>&lt; </em>Three of a Kind <em>&lt; </em>Full House <em>&lt; </em>Four of a Kind.</li>

</ol>