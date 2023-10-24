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

