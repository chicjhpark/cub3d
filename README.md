# Cub3d
### Reference
- [울펜슈타인 3D](http://users.atw.hu/wolf3d/)
### Introduction
- 레이캐스팅을 이용하여 만든 3D 미로게임입나다.
```
$> make
$> ./cub3d map.cub
```
- Key
  - 왼쪽과 오른쪽 화살표 : 시점 회전
  - W, A, S, D : 이동
  - ESC : 종료
### Rules
|   |   |
| - | - |
| Allowed functions | open, close, read, write, printf, malloc, free, perror, strerror, exit, math 라이브러리 함수, [minilibx 라이브러리 함수](https://github.com/terry-yes/mlx_example) |
- 지도는 4개의 문자로만 구성되어야 합니다. (빈 공간인 경우 0, 벽인 경우 1, 아이템은 2, 플레이어의 시작 위치와 그에 따른 시점은 N, S, E, W)
  - 간단하고 유효한 맵의 예시입니다 :
  ```
  111111
  100101
  102001
  1100N1
  111111
  ```
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
- [레이캐스팅 강의](https://pikuma.com/courses/raycasting-engine-tutorial-algorithm-javascript)를 보면서 따라 만들었다.
- 

