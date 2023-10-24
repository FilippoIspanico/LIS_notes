# LIS_notes
## Using LIS program to solve linear systems!

### Step 1. Load Lis

Move to the Lis folder and load the modules

```
cd lis-2.0.34/test/
source /u/sw/etc/bash.bashrc && module load gcc-glibc eigen && module load lis && module list
```
Note that this command also load eigen por sacaso. 
### Step 2. (If never done) compile test1.c
```
mpicc -DUSE_MPI -I${mkLisInc} -L${mkLisLib} -llis test1.c -o test1
```

### Step 3. Solve the linear systems
We want to solve a generic linear system Ax=b

In order to do so we use the previewsly compiled program called "test1".
Test1 is able to solve any linear system using different numerical methods. It is a parallel program that runs using either mpi or openMP
To run it in MPI use :

``` mpirun -n NUMBER_OF_PROCESSES ./test1 ``` 


To solve any linear system test1 must be able to take as input any matrix A and b. It can do so but using matrix format. 
If ``` A.mtx ``` and ``` b.mtx ``` are the parameters of the linear system then the call to test1 becomes


``` mpirun -n NUMBER_OF_PROCESSES ./test1  A.mtx b.mtx sol.txt hist.txt``` 

Where sol.txt and hist.txt are two file were the program will store the data about the solution. 
I believe that if we want to solve the problem with b vector begin the vectors of ones( or twos...) then instead of using a matrix format file just use 1 (2...) in the call




The methods available are:
* jacobi
* gauss-sidel (gs)
* conjugate gradient (cg)
* bicg
* bicgstab
* gmres
* ...


To set a method we add a flag ``` -i method_name ```  where method_name is one of the previewsly mentioned methods. If exist, the name between brakets must be used. The call becomes

``` mpirun -n 4 ./test1 A.mtx b.mtx sol.txt hist.txt -i method_name ```

The default method is 

Moreover, we are able to set the parameters of the methods. In particular we can add the following parameters: 
* ``` -tol 1.0e-14 ``` to set the tollerance of the method to 10^-14
* ``` -maxiter 100 ``` to set the max # of iteration to 100
* ``` -restart 20 ``` what is restart?    
* ``` -p jacobi ``` to set jacobi as a preconditioner ?

For instance: 
```mpirun -n NUMBER_OF_PROCESSES ./test1  A.mtx b.mtx sol.txt hist.txt -i bicgstab -maxiter 100 ```


  
