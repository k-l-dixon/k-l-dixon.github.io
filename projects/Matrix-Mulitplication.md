---
layout: project
type: project
published: true
image: images/Matrix-Mulitplication.png
title: MatMul
permalink: projects
# All dates must be YYYY-MM-DD format!
date: 2021-11-04
labels:
  - C
  - Matrix Mulitplication
summary: 
---



Computer science uses matrices as means for providing approximations of complicated computations.  As the complexity of these computations grow even more, distributing memory amongst multiple processors becomes necessary.  To accomplish this, we leverage matrix multiplication algorithms to support applications such as graphics, image processing, and genetic sequencing.  Multiplying one matrix to another matrix and storing the result in yet another matrix is the concept behind this area.

There are several different matrix multiplication algorithms.  This was a team effort project (school project)  aimed to use the “outer product” matrix multiplication algorithm using message passing.  We developed code using the algorithm that would then be tested using Docker containers as well as a cluster.

I was primarily involved in combined efforts debugging and testing of the code.  Once complete, results were analyzed for comparison in time and complexity.  Afterwards, we were able to craft a report to present.       

below is an exerpt of some of the code we were able to compose:

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

