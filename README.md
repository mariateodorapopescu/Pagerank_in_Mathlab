# Pagerank Algorithm

## in PR_Inv:
- I started by doing the QR factorization with Gram-Schmidt. I took each
column vector of matrix A, and the following column vectors from the matrix
I "straighten" and regulate those after the one I took;
- I took the dimensions of A to know how much to allocate for Q and R.
firstly Q and R are null matrices, but also the inverse of A. I make a copy of a on V
-I normalized the column vector of V, I normalize it, then straighten the columns
remained according to the standard one
-I solved the system n times, finding one column each for B, i.e. the reverse
of A, taking one column each from the transposed Q
-Q * R * B = IN, from where I remove B; IN = eye(N) I write like this here. I pass it in
the other side and it results: R * B = Q'
-first I calculated the element on line m (last), column i
-B(:,i) is, in fact, the unknown x from SST
-the free term of the system is the i column vector of the QT matrix (Q')
- it is taken from the bottom up
- it's always the column and it's taken in columns

## in PageRank:
- after reading the data from the file (the algorithm is also repeated for Iterative,
Algebraic; I will detail it only for iteratives) I calculate the vectors
by the two methods
-then I pasted the content of the name variable with ".out" to create the name
the output file. I opened another file for writing and wrote
first the number of nodes, then the elements of the two required vectors.
-I made a copy of the second vector and sorted the copy with
the swap sort algorithm; then I took two forums,
and I checked for which indexes of R2 and its sorted copy correspond
the elements, thus writing the position and the relative position.
- then I also calculated the F from the statement, that is, the degree of belonging for the copy
sorted and displayed.

## in Iterative:
- I opened the file first. I read the number of nodes. I initialized what se
maybe with 0 or with 1, depending on the situation, for example A, K are zeros, O is ones
- I initialized the R and RU column vectors, RU being R calculated in the next step
- I read line by line. there are N nodes, so N lines with information. then in turn
I read the first node, the number of nodes adjacent to it and took each adjacent node
with it in a circle and I put 1s where the adjacent node did not meet with itself,
thus making the adjacency matrix.
- after reading I don't forget to close the file
- now that I have read the data from the file, I calculate the stochastic matrix M, with the help of
of the K matrix, the one of degrees, which is a diagonal matrix. I took the lines and counted,
how many 1's are in the adjacency matrix, i.e. how many nodes is adjacent to the node whose
column in the corresponding matrix. I could do this while reading, but I didn't realize it.
I put the calculated number on the main diagonal of the matrix K. I then reversed it
with the help of PR-Inv and I multiplied it with the adjacent one, finding, thus,
the stochastic matrix, according to the algorithm on the wiki.
-I continued to calculate R according to the algorithm on the wiki. R and RC are vectors,
so I multiply each element of R by 1/N, assuming that at the beginning it is distributed
exactly the number of accesses to the N pages, then I calculate iteratively until the difference
in the mode between R and R calculated in the next step is the threshold data.

## in Apartenenta:
-u(x)={0, x=0:val1;
        a*x+b, x=val1:val2; u continue
        1, x=val2:1;
- so that u is continuous, we passed the limit: lim(x->val1)(a*x+b)=0&&lim(x->val2)(a*x+b)=1
=> a=1/(val2-val1) and b=val1/(val1-val2) and I replaced a and b from the definition of the function
and I took cases

## in Algebraic:
- after reading the data from the file (the algorithm is also repeated for Iterative,
and for PageRank; I detailed only for Iterative), I took a column vector only
with ones, called O from Ones. and I multiplied each element of it
with ((1-d) / N); that will be O=[(1-d)/N; (1-d)/N; ...; (1-d)/N] from the algorithm
-R = [(1-d)/N; (1-d)/N; ...; (1-d)/N] + d * M * R, according to wiki
-B = eye(N) - d * M; if from the algorithm I pass what is with R in one part and
the rest elsewhere (initial: R = O + d * M * R => R - d * M * R = O)
=> (eye(N) (ie a kind of 1, as we gave a common factor) - d*M)*R = O
and I noted the coefficient of R with B (I don't know what to name them)
BINV is the inverse of B => B * R = O, calculated with PR-Inv
