# LIS_notes
## Using LIS program to solve linear systems!

### Step 1. Load Lis

```
cd lis-2.0.34/test/
module load lis
```

### Step 2. (If never done) compile test1.c
```
mpicc -DUSE_MPI -I${mkLisInc} -L${mkLisLib} -llis test1.c -o test1
```

### Step 3. Solve the linear systems
We want to solve a generic linear system Ax=b



To solve the linear system we use the previewsly compiled program called "test1".
Test1 is able to solve any linear system using different methods. The methods available are:
* jacobi
* gauss-sidel (gs)
* conjugate gradient (cg)
* bicg
* bicgstab
* gmres
* ...


To set a method we add a flag ``` -i method_name ```  where method_name is one of the previewsly mentioned methods. If exist, the name between brakets must be used.

Moreover, we are able to set the parameters of the methods. In particular we can add the following parameters: 
* ``` -tol 1.0e-14 ``` to set the tollerance of the method to 10^-14
* 
  
