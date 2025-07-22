# `tiny-flash-attention`

### `this repo is my attempt at re-creating the flash-attention paper in cuda` 

the high level architecture taken from the [paper](https://arxiv.org/pdf/2205.14135)
<br></br>
<img width="1408" height="532" alt="image" src="https://github.com/user-attachments/assets/7c1d7c47-f05b-423e-aaf2-64041a6cd7cd" />



##### `the minimal forward pass is written in less then 150 lines of cuda`
##### `naming conventions followed are very similar to the paper`

#### `Profiling on my RTX-3050`
```
=== profiling manual attention ===
...
Self CPU time total: 52.389ms
Self CUDA time total: 52.545ms

=== profiling minimal flash attention === 
...  
Self CPU time total: 11.452ms
Self CUDA time total: 3.908ms
```


## `NOTE :`


* `the thread-per-row simplification makes the matrix multiplications very slow. This is probably why for longer
sequences and larger block sizes, this gets slower than the manual implementation.`


* `in the inner loop, i assign each thread to a row of the output matrix. This differs from the original implementation.`


* `Q,K,Vs are in float32 which is unlike the original implementation which uses float16.`

#### `back pass is to implemented`
#### `setting block sizes dynamically is also to be implemented`
