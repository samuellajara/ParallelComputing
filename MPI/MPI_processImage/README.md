<h2 align="center"> Parallel Computing MPI Image processing </h2>

<h6> 

Program with the MPI paradigm for distributed memory systems.

An image in gray tones stored in a binary file with a raw extension will be read, that is, the data will be of the unsigned char type and the file size will be height x width x 1byte.

The image read will be stored in a two-dimensional matrix by the root process, the processed images will be stored in binary files in raw format, a process performed by the root process.

Processors to implement (one will be chosen by passing parameter):
Filtered by mean (3 x 3 items)
Filtered by median (3 x 3 items)
Edge detection (SOBEL)

The output text file, generated by the root process, will contain the following information: input file name, image size, output file name, number of processes used, execution time (counted from when root already has the image in memory until before starting to save the file with the processed image).

In edge detection by SOBEL, those elements that do not have the 8 SI neighbors will be considered, performing symmetric extension for both rows (row -1 will be equal to 1, row N will be equal to N-2, being N the number of rows) as for columns.

The names of the files and other necessary parameters (image size and type of processing)
they will be passed as arguments in the execution statement.

As has been said, the "root" process will be in charge of reading and writing files, the "root" process will store all the information and distribute a set of rows to each "slave" process, it will receive the data from each "slave" process. and will write to file.

Compile Sentence:
➔ mpicc -o proc MPI_processingImage.c -lm

Execution Sentence:
➔ mpirun -np 5 proc lena4096x4096.raw 4096 4096 average outAverage4096.raw




</h6>
