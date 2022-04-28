# Ford-Fulkerson Algorithm

## | 포드 풀커슨(Ford-Fulkerson) 알고리즘
 - 네트워크 유량 알고리즘의 가장 기본적인 알고리즘


    ## | 네트워크 유량(Network flow) 알고리즘
    
      그래프를 '용량'에 대해 다루는 알고리즘으로, source -> sink 로 최대의 유량을 흘려 보내는 방법을 다루는 문제이다.
    
    - Source / Sink : 네트워크의 시작 부분 / 네트워크가 끝나는 부분
    - c(a,b) : 정점 a에서 b로 가는 간선의 용량 
    - f(a,b) : 정점 a에서 b로 흐르는 유량
    - 증가경로 : source->sink로 유량을 보낼 수 있는 경로
    - 잔여용량 : 간선의 용량과 현재 흐를 수 있는 유량의 차이, 즉 용량-유량(=c(a,b)-f(a,b))



     ### < 3가지 조건 >

     1. 용량의 제한 f(a,b)<=c(a,b)
      
        -> 용량은 두 정점 사이에서 최대로 흐를 수 있는 양을 의미한다.
     2. 유량의 대칭성 f(a,b)=-f(b,a)
     3. 유량 보존의 법칙 f(a,b)들의 합=0 

        ->  source, sink를 제외한 각 정점에서 들어오고, 나가는 유량의 합은 일치해야 한다.


    
## | 포드 풀커슨(Ford-Fulkerson) 알고리즘 작동방식
#
1.  네트워크 내 모든 간선들의 유량=0으로 초기화 한다.
2.  깊이우선탐색(DFS)을 사용하여, source->sink로 흐를 수 있는 경로를 탐색한다. 
3.  찾은 경로 내 간선들의 잔여 용량이 가장 적은 값을 유량으로 흘려 보낸다.
4.  더 이상의 경로를 찾을 수 없을 때까지 반복한다.

![1](https://user-images.githubusercontent.com/101811119/165811934-d38d6871-480b-4e60-9ec8-44f2d3226803.png)
![111](https://user-images.githubusercontent.com/101811119/165812754-7143b4ec-8df9-4d36-89ca-1831b6e0c485.png)

![11](https://user-images.githubusercontent.com/101811119/165812574-3dfd3633-b9b6-478a-b0eb-819b2c485101.png)


## | 포드 풀커슨(Ford-Fulkerson) 알고리즘 코드 실행 결과
#

## | 포드 풀커슨(Ford-Fulkerson) 알고리즘 성능 분석
#
