---
layout: project
type: project
published: true
image: images/matmul.jpeg
title: Distributed-Memory Matrix Mulitplication
# All dates must be YYYY-MM-DD format!
date: 2021-11-04
labels:
  - C
  - Matrix Mulitplication
summary: Matrix multiplication algorithms can be applied in various ways and support applications such as graphics, image processing, and genetic sequencing.  
---



Matrix multiplication is an important operation in many numerical algorithms with significant effort devoted to optimizing these algorithms.  Computer science uses matrices as means for providing approximations of complicated computations.  As the complexity of these computations grow even more, distributing memory amongst multiple processors becomes necessary.  Distributed-memory matrix multiplication allows for secluded address space, through exchanging messages, for each operation process. To accomplish this, we leverage matrix multiplication algorithms to support applications such as graphics, image processing, and genetic sequencing.  Multiplying one matrix to another matrix and storing the result in yet another matrix is the concept behind this area.  

There are several different matrix multiplication algorithms.  This was a team effort project (school project) aimed to compare three common used algorithms in distributed-memory matrix multiplication: The Outer-Product Algorithm, Cannon's Algorithm, and the Fox Algorithm.  

### Outer-Product Multiplcation

Two Matrices, Matrix A and Matrix B, are multiplied by decomposing the matrices into sub pairs consisting of a column of Matrix A against a row of Matrix B.  The result of each computation is then merged into a third matrix, Matix C, as the result.   

### Cannon's Algorithm

Considering two N x N matrices divided into p blocks, Cannon’s algorithm regards the alignment of these matrices in calculating the output matrix C. The algorithm starts with a redistribution of matrices A and B. Each block row of matrix A and each block column of matrix B is shifted so that each processor in the first processor column and row contains a diagonal block of the matrix. Each block of matrix A and B are aligned so that each process can multiply submatrices independently.  Submatrices of A are shifted to the left by i while submatrices of B are shifted up by j at each iteration until all blocks are multiplied and combined into matrix C. One main advantage of the Cannon algorithm is that its storage requirements are constant and independent of the number of processors.

### Fox Algoritm

Considering two N x N matrices divided into p blocks, the Fox algorithm broadcasts subblocks of matrix A along their rows to multiply with matrix B for the output matrix C.  It requires no pre-skewing or post-skewing and depends on horizontal broadcasts of matrix A's diagonals and vertical shifts of matrix B. Matrix A would then broadcast the next subblock onto each row in A and the columns of matrix B shifts up and multiplied again to add into matrix C.  This process is iterated until our final result is stored in matrix C. 

The group developed code using the algorithm that would then be tested using Docker containers as well as a cluster.  I was primarily involved in combined efforts debugging and testing of the code.  Once complete, results were analyzed based on time, latency, cluster size, and speedup.       

below is an excerpt of some of the code we were able to compose:

```c
  for (int i = 0; i < n/sqrtp; i++)
  {
    for (int j = 0; j < n/sqrtp; j++)
    {
      *(arrA + i*(n/sqrtp) + j)  =  i %(n / sqrtp) + myRow * (n / sqrtp);
      printf("%.1f\t", *(arrA + i*(n/sqrtp) + j));
      *(arrC + i*(n/sqrtp) + j)  = 0;
    }
      printf("\n");
  }

  printf("\nProcess rank %d (coordinates: %d, %d), block of B:\n", rank, myRow, myCol);
  for (int i = 0; i < n/sqrtp; i++)
  {
    for (int j = 0; j < n/sqrtp; j++)
    {
      *(arrB + i*(n/sqrtp) + j) = (i % (n / sqrtp) + myRow * n / sqrtp) + (j % (n / sqrtp) + myCol * n / sqrtp);
      printf("%.1f\t", *(arrB + i*(n/sqrtp) + j));
    }
```

### Conclusion

From the simulation and the MANA experiments, we found that Cannon algorithm and Fox algorithm outperform the Outer-Product algorithm. Cannon algorithm also runs 1-2% faster than Fox algorithm in most cases. And the fox algorithms would benefit more from the parallel processing .The way we implemented those algorithms caused the difference in the previous experiments. 
	The implementation of Cannon uses MPI_Send and MPI_Recv for shifting, and it has an extra initial skewing that was also implemented by MPI_Send and MPI_Recv . The implementation of Fox uses MPI_Send and MPI_Recv for shifting and uses Bcast for diagonal broadcast while the implementation of Outer-Product uses two Bcast only.
	Based on the results of all experiments, a 1-to-N Bcast takes longer than N 1-to-1 MPI_Send and MPI_Recv. Such that the Canon algorithm performs best although it needs an initial skewing, and the Outer-Product algorithm performs worst because of its two Bcast operations. The Fox algorithm doesn’t have an initial phase so it performs as fast as the Cannon algorithm.	
Cannon’s algorithm gives us less overhead compared with Fox and Outer-Product algorithms. However, for Cannon and Fox algorithms, it’s hard to tell which one is actually better than the other.


