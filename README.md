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

     1. #### 용량의 제한 f(a,b)<=c(a,b) 
        
        -> 용량은 두 정점 사이에서 최대로 흐를 수 있는 양을 의미한다.
     2. #### 유량의 대칭성 f(a,b)=-f(b,a)
     3. #### 유량 보존의 법칙 f(a,b)들의 합=0 

        ->  source, sink를 제외한 각 정점에서 들어오고, 나가는 유량의 합은 일치해야 한다.



    
## | 포드 풀커슨(Ford-Fulkerson) 알고리즘 작동방식


> 1.   네트워크 내 모든 간선들의 유량=0으로 초기화 한다.
>
> 2.   깊이우선탐색(DFS)을 사용하여, source->sink로 흐를 수 있는 경로를 탐색한다. 
>
> 3.   찾은 경로 내 간선들의 잔여 용량이 가장 적은 값을 유량으로 흘려 보낸다.
>
> 4.   더 이상의 경로를 찾을 수 없을 때까지 반복한다.



#### ex) 
 아래와 같은 예시가 있다.

![1](https://user-images.githubusercontent.com/101811119/165832692-e94ba0dd-6ae0-453e-a84e-cf2a1c51f0a1.png)

먼저 깊이우선탐색(DFS)을 사용하여 증가경로를 찾는다.

찾은 경로는 "S->A->B->T" 이고, 이때 흘려 보낼 수 있는 최대 유량은 1 이다.
![2](https://user-images.githubusercontent.com/101811119/165820276-7b20b01d-e322-4dd3-8295-0e0793971bb5.png)

이때, 유량의 대칭성(f(a,b)=-f(b,a))에 따라서 역간선을 표시하면 아래와 같다.
![3](https://user-images.githubusercontent.com/101811119/165820391-fcee9188-7ffe-44bf-a84c-5ea6e6e94ee7.png)

따라서, 새로운 경로인 "S->B->A->T"를 찾을 수 있고, 이때 흘려 보낼 수 있는 최대 유량은 1이다.
![4](https://user-images.githubusercontent.com/101811119/165820399-6fad062c-879f-4bf7-84b6-3a67b632f576.png)


-> 더 이상의 경로를 찾을 수 없으므로, 최대 유량은 1+1=2, 2가 된다.

## | 포드 풀커슨(Ford-Fulkerson) 알고리즘 코드 실행 결과


## | 포드 풀커슨(Ford-Fulkerson) 알고리즘 성능 분석

만약, 그래프가 아래와 같이 용량이 큰 상황을 분석해 본다면

![11](https://user-images.githubusercontent.com/101811119/165832753-4d8215fb-6701-4812-b225-f92c107ae1aa.png)


작동방식은 위에 적어둔 것을 참고한다.
 "S->A->B->T" 경로, 최대 유량은 1이므로 아래와 같다.

![22](https://user-images.githubusercontent.com/101811119/165832769-ee20e293-64a7-4546-8c17-100eef471959.png)


역간선 작성, 이후 "S->B->A->T"경로, 최대 유량은 1이므로 아래와 같다.

![33](https://user-images.githubusercontent.com/101811119/165832775-edda32e6-cf3a-41b5-a092-397ceee70d4d.png)


이 과정을 10000번 반복해야 최대 유량 20000을 구할 수 있다.

-> 용량이 크면 클수록 더 많이 반복하는 복잡한 과정이 된다.

포드 풀커슨(Ford-Fulkerson) 알고리즘의 시간복잡도는 O((V+E)F).
#

### | 에드몬드-카프(Edmonds-Karp) 알고리즘


반면,  포드 풀커슨(Ford-Fulkerson) 알고리즘과 전체적인 과정은 비슷하지만, '깊이우선탐색(DFS)'이 아닌, '너비우선탐색(BFS)'을 사용하는 에드몬드-카프(Edmonds-Karp) 알고리즘으로 생각해 본다면

"S->A->T"경로, 최대 유량 10000이므로 아래와 같다.

![111](https://user-images.githubusercontent.com/101811119/165832790-4daaad97-78f2-40f0-bcee-f0cceb3b0714.png)


이후, "S->B->T"경로, 최대 유량 10000이므로 아래와 같다.

![222](https://user-images.githubusercontent.com/101811119/165832811-1e68872d-b877-4de1-951a-2a152a3ffbd0.png)

에드몬드-카프(Edmonds-Karp) 알고리즘을 사용하면, 2번만 탐색하면, 최대 유량 20000을 찾아낸 것을 알 수 있다.

#

### |  포드 풀커슨(Ford-Fulkerson) 알고리즘과 에드몬드-카프(Edmonds-Karp) 알고리즘의 비교


-> 위와 같은 상황에서, 용량이 커지면 커질수록 에드몬드-카프(Edmonds-Karp) 알고리즘이 더 효율적인 작동을 한다.

