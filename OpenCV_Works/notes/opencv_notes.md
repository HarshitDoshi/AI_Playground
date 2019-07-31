### Mat, the basic image container
----------------------------------
```
Mat A, C;
```

Initialize Mat objects with just the header parts.

```
A = imread(argv[1], IMREAD_COLOR);
```

```
Mat B(A);
```

Using the copy constructor.

```
C = A;
```

Using the assignment operator.

```
Mat D (A, Rect(10, 10, 100, 100));
```

Using a rectangular cutout from a picture.

```
Mat E = A(Range::all(), Range(1, 3));
```

Using row and column boundaries.

Here, all rows are selected and columns from 1 to 3 are selected.

Here, B, C, D, E and A all point to the same matrix location in the memory. Modifying one will modify all.

```
Mat F = A.clone();
Mat G;
A.copyTo(G);
```

Here, F and G are clones or copies of A. They are stored in different memory locations and refer to different matrices with the same data as A.

### Creating Mat objects explicitly:
------------------------------------
* Using the Mat constructor:

```
Mat M(2, 2, CV_8UC3, Scalar(0, 0, 255));
```

Here a 2x2 matrix is created. CV_8UC3 is the data type specification. It is as follows:

CV_[The number of bits per item][Signed or Unsigned][Type prefix]C[The channel number]

Thus, CV_8UC3 means we are using unsigned char types that are 8-bit long and each pixel has 3 of these to form the 3 channels.
Scalar is a 4 element short vector. Specifying it will initialize all matrix points with a custom value.

* Using C/C++ arrays and initialize via constructor:

```
int sz[3] = {2, 2, 2};
Mat L(3, sz, CV_8UC(1), Scalar::all(0));
```

Here, we first specify the number of dimensions first, which is 3 here, then we pass a pointer which specifies the length for each of these dimensions. Then we pass in the data type with channels (here 1 channel) and finally we specify the Scalar with all values being 0.

* Using Mat.create function:

```
M.create(4, 4, CV_8UC(2));
```

You cannot initialize the matrix values with this construction. It will only reallocate its matrix data memory
if the new size will not fit into the old one.

* MATLAB style initializer: zeroes, ones, eye

```
Mat E = Mat::eye(4, 4, CV_64F);
Mat O = Mat::ones(2, 2, CV_32F);
Mat Z = Mat::zeroes(3, 3, CV_8UC1);
```
