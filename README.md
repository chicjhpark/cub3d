# Cub3d
### Reference
- [울펜슈타인 3D](http://users.atw.hu/wolf3d/)
### Introduction
- 레이캐스팅을 이용하여 만든 3D 미로게임
```
$> make
$> ./cub3d map.cub
```
![cub3d](https://user-images.githubusercontent.com/69841779/212979263-b5c86f3e-f1f9-443b-a6b0-c9de863f2f6f.gif)
- Key
  - 왼쪽과 오른쪽 화살표 : 시점 회전
  - W, A, S, D : 이동
  - ESC : 종료
### Rules
- [minilibx](https://github.com/terry-yes/mlx_example) 를 사용합니다.
- 지도는 4개의 문자로만 구성되어야 합니다. (빈 공간인 경우 0, 벽인 경우 1, 아이템은 2, 플레이어의 시작 위치와 그에 따른 시점은 N, S, E, W)
  - 지도는 벽으로 둘러쌓여 있어야 합니다.
- 각 요소 (지도 제외) 의 첫 번째 정보는 (하나 또는 두개의 문자로 구성된) 유형 식별자입니다.
  - 해상도 : R 1920 1080
  - 북쪽 벽 텍스쳐 : NO ./path_to_the_north_texture
  - 남쪽 벽 텍스쳐 : SO ./path_to_the_south_texture
  - 서쪽 벽 텍스쳐 : WE ./path_to_the_west_texture
  - 동쪽 벽 텍스쳐 : EA ./path_to_the_east_texture
  - 아이템 텍스쳐 : S ./path_to_the_sprite_texture
  - 바닥 색상 : F 220,100,0
  - 천장 색상 : C 225,30,0
### Development Report
- [Raycasting Engine Programming](https://pikuma.com/courses/raycasting-engine-tutorial-algorithm-javascript)
> 이 동영상 강의를 보면서 레이캐스팅을 삼각함수로 구현하는 방법을 배웠다.

![2D_raycasting](https://user-images.githubusercontent.com/69841779/212916240-e334277b-5caa-4437-8b9c-47407919e1cd.gif)
> 3D를 구현하기 전 2D로 구현한 프로그램이다.
```
while (column < 320)
  1. 광선을 뽑는다.
  2. 광선이 벽과 교차할 때까지 추적한다.
  3. 교차점(x,y)과 거리(광선의 길이)를 기록한다.
  4. 광선이 오른쪽 광선각도로 이동하도록 각도의 증가량을 더한다. (+=60(degree)/320(width))
```
- 벽에 부딪힐 때까지의 거리
  1. 가장 좋은 방법은 수평과 수직의 교차점을 별도로 확인하는 것이다.
  2. 수직 또는 수평 교차로에 벽이 있으면 확인을 멈춘다.
  3. 수직 및 수평의 교차점까지의 거리를 비교하고 가장 가까운 점을 선택한다.
  - yintercept = floor(Py / 32) * 32
  - xintercept = Px + (Py - Ay) / tan(𝞱)
  - xstep = 가로선(x축) 교차점까지의 거리, n번째 x선에서 n + 1 선까지의 거리, 삼각형의 밑변
  - ystep = 세로선(y축) 교차점까지의 거리, n번째 y선에서 n - 1 선까지의 거리, 삼각형의 높이
  - xintercept = A점까지의 x축 거리
  - yintercept = A점까지의 y축 거리
- 수평 교차로
  1. 첫 번째 수평의 좌표를 찾는다.
  2. 세로선까지의 거리를 찾는다.
  3. 가로선까지의 거리를 찾는다.
  4. 교차점(x, y)을 지도의 배열로 변환 [i, j]
  5. if (교차점이 벽에 부딪힌 경우)
    1. 수평 적중 거리를 저장
    2. else (다음 수평 교차로 찾기)
  - ystep = GRID_SIZE
  - xstep = GRID_SIZE / tan(ray_ang)
- 수직 교차로
  1. 첫 번째 수직선 교차점의 좌표를 찾는다.
  2. 가로선까지의 거리를 찾는다.
  3. 세로선까지의 거리를 찾는다.
  4. 교차점(x, y)을 지도의 배열로 변환 [i, j]
  5. if (교차점이 벽에 부딪힌 경우)
      수직 적중 거리를 저장
     else (다음 수직 교차로 찾기)
  - xstep = GRID_SIZE
  - ystep = GRID_SIZE * tan(ray_ang)
