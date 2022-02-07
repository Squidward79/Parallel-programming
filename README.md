# Parallel-programming
CUDA를 사용한 병렬 프로그래밍 프로젝트

## 프로젝트 기간 
2019년 6월 ( 약 2주 )

## 사용한 툴 
C++ / CUDA / OpenCV

<h2>
  
[프로젝트 PPT](parallel-programming.pdf)  
  
[CPU에 적용한 C++ 소스코드](cpu.cpp)  
  
[GPU에 적용한 CUDA 소스코드](gpu.cu)
  
</h2>


## 설명 
GPU와 CPU의 영상처리 성능비교를 위해 동일한 영상에 대해 같은 알고리즘을 처리하는 속도를 확인합니다.  
같은 알고리즘을 GPU에서는 CUDA를 사용하여 병렬 프로그래밍으로 처리하도록 작성하였습니다.  
고속도로 주행 동영상의 차선을 검출한 후 검출한 차선에 대하여 선을 그리는 프로그램입니다.

차선 검출에 대한 진행알고리즘은 다음과 같습니다.
1. 컬러영상을 Gray스케일로 전환한 후 Gaussian blur를 적용
2. 전환된 영상을 Canny edge를 사용하여 변환
3. 화면상의 모든 점에 대하여 Hough 변환 알고리즘을 적용
4. 적용한 결과를 선으로 표현

이 과정에서 GPU로 병렬화 시킨 부분은 다음과 같습니다.
1.  RGB영상을 Gray영상으로 변환하기
2.  5x5의 Gaussian 마스크 행렬을 통해 blur처리하기
3.  Hough 변환 알고리즘 적용하기

위의 동일한 알고리즘으로 CPU와 GPU 각각의 수행시간을 비교하였습니다.  
그 결과 CPU에 비해 GPU를 사용할 경우 약 20배정도 빠른 속도를 보여주었습니다.


