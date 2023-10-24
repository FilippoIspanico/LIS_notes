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
We are also able to set some parameters such as 
