算法本身这里不进行阐述，主要总结一点`cuda`的经验。
- 区分好`device memory`和`host memory`，写cpu代码时注意不能直接引用（`eg:*num`）。
- 没必要为每个元素启动一个线程，浪费。对于循环迭代cuda并行时可以用循环次数个线程即可。（这也是lab project describe里提示了的。）
- 一种有意思的nextPow2
- 注意溢出问题，注意并发时的问题（当涉及写覆盖时，不要input和output用同一个，而是用一个新的数组，**不要舍不得内存使用**）
- cuda里面也有`atomic`
- 用`cuda-gdb`调试时，在核函数里打断点才可以看到`device data`，注意加上`-g -G`选项。
- 用`p *array@size`查看数组size个元素。 