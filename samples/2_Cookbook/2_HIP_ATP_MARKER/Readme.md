## Using hipEvents to measure performance ###

This tutorial is follow-up of the previous two tutorial where we learn how to write our first hip program, in which we compute Matrix Transpose and in second one, we added feature to measure time taken for memory transfer and kernel execution. In this tutorial, we won't make amy changes to the source code. We'll explain how to use the  codexl/rocm-profiler for hip timeline tracing.


## Introduction:

CodeXL and rocm-profiler are the tool used for profiling the application, which is of prominent use in optimizing the application by means of finding the memory bottlenecks and etc.

## Requirement:
[CodeXL Installation](http://gpuopen.com/compute-product/codexl/) 

## prerequiste knowledge:

Programmers familiar with CUDA, OpenCL will be able to quickly learn and start coding with the HIP API. In case you are not, don't worry. You choose to start with the best one. We'll be explaining everything assuming you are completely new to gpgpu programming.

## Simple Matrix Transpose 

We will be using the Simple Matrix Transpose source code from the previous tutorial as it is.

## Using CodeXL markers for HIP Functions

HIP can generate markers at function being/end which are displayed on the CodeXL timeline view. To do this, you need to install ROCm-Profiler and enable HIP to generate the markers:

1. Install ROCm-Profiler Installing HIP from the rocm pre-built packages, installs the ROCm-Profiler as well. Alternatively, you can build ROCm-Profiler using the instructions given below.

2. Build HIP with ATP markers enabled HIP pre-built packages are enabled with ATP marker support by default. To enable ATP marker support when building HIP from source, use the option -DCOMPILE_HIP_ATP_MARKER=1 during the cmake configure step.

3. Set HIP_ATP_MARKER
`export HIP_ATP_MARKER=1`

4. Recompile the target application

5. Run with profiler enabled to generate ATP file.
`/opt/rocm/bin/rocm-profiler -o <outputATPFileName> -A <applicationName> <applicationArguments>`

##Using HIP_TRACE_API

You can also print the HIP function strings to stderr using HIP_TRACE_API environment variable. This can also be combined with the more detailed debug information provided by the HIP_DB switch. For example:
`HIP_TRACE_API=1 HIP_DB=0x2 ./myHipApp`
Note this trace mode uses colors. "less -r" can handle raw control characters and will display the debug output in proper colors.

## More Info:
- [HIP FAQ](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/docs/markdown/hip_faq.md)
- [HIP Kernel Language](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/docs/markdown/hip_kernel_language.md)
- [HIP Runtime API (Doxygen)](http://gpuopen-professionalcompute-tools.github.io/HIP)
- [HIP Porting Guide](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/docs/markdown/hip_porting_guide.md)
- [HIP Terminology](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/docs/markdown/hip_terms.md) (including Rosetta Stone of GPU computing terms across CUDA/HIP/HC/AMP/OpenL)
- [hipify-clang](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/hipify-clang/README.md)
- [Developer/CONTRIBUTING Info](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/CONTRIBUTING.md)
- [Release Notes](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/RELEASE.md)
