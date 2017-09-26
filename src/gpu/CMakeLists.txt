project(GPU_LIB)
cmake_minimum_required(VERSION 2.8)

#find cuda
find_package(CUDA REQUIRED)

#build options
set(GENCODE -gencode arch=compute_52,code=sm_52;-G;-g)

set(SOURCES cudaErrors.cu gpu_finite_3d.cu gpu_funcs_3d.cu save.cu wave_fkernel.3d80.cu)
set(HEADERS gpu_finite_3d.h gpu_funcs_3d.h)

#cuda add lib
cuda_add_library(gpu_lib ${SOURCES} ${HEADERS})

