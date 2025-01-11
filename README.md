# Trapezoidal-Rule_using-MPI

이 프로젝트는 MPI(Message Passing Interface)를 활용하여 수치적분 방법 중 하나인 사다리꼴 적분법(Trapezoidal Rule)을 구현한 것입니다. 병렬 컴퓨팅의 성능 향상을 확인하고, 확장성과 정밀도를 평가하는 실험 결과를 포함하고 있습니다.
# 



#### **소개**
수치 적분의 정밀도가 높아질수록 연산량이 증가하므로, 병렬 컴퓨팅을 활용한 효율적인 계산이 중요해지고 있습니다. 이 프로젝트는 MPI를 활용해 분산 메모리 환경에서 병렬 처리를 통해 사다리꼴 적분법을 구현합니다. 주요 목표는 다음과 같습니다

- 직렬(Serial)과 병렬(Parallel) 실행 시간 비교

- 병렬 처리의 확장성(Scalability) 평가

- 사다리꼴 개수 증가에 따른 정밀도(Precision) 평가

<br>


#### 개발 환경
운영 체제: Ubuntu 22.04 (MacOS에서 UTM을 활용하여 가상화)

MPI 라이브러리: MPI(Message Passing Interface)

컴파일러: GCC (MPI 호환)

<br>

#### 프로그램 실행
```
mpicc -g -Wall -o MPI_Trapezoid1_f1 MPI_Trapezoid1_f1.c
```

직렬 실행: 


```
mpiexec -n 1 ./MPI_Trapezoid1_f1

```


병렬 실행 (예: 4개의 프로세스 사용): 
```
mpiexec -n 4 ./MPI_Trapezoid1_f1
```

파라미터 설정: 코드에서 함수 정의, 구간, 사다리꼴 개수 등을 변경하여 다양한 실험 수행 가능

<br>
---------------------------------------------------------------------------------------

#### 실험결과

##### part1) Serial vs Parallel execution time comparison

병렬화가 정확도에는 영향을 미치지 않음

낮은 Speedup과 Efficiency -> 이 작업의 낮은 계산 복잡도로 인해 병렬화의 장점이
병렬화 오버헤드에 의해 상쇄됨

작업량이 작은 경우 Serial 실행이 더 효율적
<br>
<br>

##### part2) Scalability Test
속도 향상은 더 큰 workload에서 더 잘 확장되는 경향이 있으며, 이는 더 복잡한
함수일수록 다수의 프로세스를 활용하는 것이 효율적
<br>
<br>

##### part3) Precision Test
사다리꼴 개수가 증가할수록 향상되며,
적분의 정확도가 높아짐
