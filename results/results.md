# Wordpress results

The table below shows the average runtime required to solve a problem for a given amount of Wordpress instances and a number of virtual machine offers. In our testing, we used two solvers: Chuffed and Google OR-Tools; and we ran the tests with a 40 minute timeout limit.

| Number of Wordpress Instances | Number of VM Offers | Chuffed | OR-Tools |
| ----------------------------- | ------------------- | ------- | -------- |
| 3 | 20 | 2.09s | 3.51s |
| 3 | 40 | 3.85s | 8.40s |
| 3 | 250 | 52.00s | 96.19s |
| 3 | 500 | 461.84s | 191.21s |
| 4 | 20 | 25.85s | 23.27s |
| 4 | 40 | 116.69s | 56.27s |
| 4 | 250 | 1956.60s | 502.89s |
| 4 | 500 | - | 989.54s |
| 5 | 20 | 601.39s | 150.28s |
| 5 | 40 | 2310.67s | 426.10s |
| 6 | 20 | - | 494.06s |
| 6 | 40 | - | 1175.98s |

This table shows the necessity of using *Symmetry Breaking* techniques. This implies that we add aditional constraints, thus aiming to reduce the number of symmetrical solutions and the searching space (two solutions are considered symmetrical if the total leasing price is the same, but they have different assignment matrices).

