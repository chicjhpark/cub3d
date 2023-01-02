# Cub3d
### Introduction
- 레이캐스팅을 이용하여 만든 3D 미로게임입나다.
### Reference
- [울펜슈타인 3D](http://users.atw.hu/wolf3d/)
### Directions
```
$> make
$> ./cub3d map.cub
```
### Rules
|   |   |
| - | - |
| Allowed functions | open, close, read, write, printf, malloc, free, perror, strerror, exit, math 라이브러리 함수, [minilibx 라이브러리 함수](https://github.com/terry-yes/mlx_example) |
- 반드시 miniLibX를 사용해야 합니다. (운영체제에서 이용 가능한 라이브러리와 과제에서 제공되는 소스 중 하나를 사용하셔야 합니다) 만약 제공받은 소스를 이용해 작업하기로 했다면, Libft의 공통 지침 (Common Instructions) 과 같은 규칙을 따라야 합니다.
- 두 번째 인자가 없을 경우, 프로그램은 다음 규칙을 준수하면서 화면 창에 영상을 표시합니다.
  - 키보드의 왼쪽과 오른쪽 화살표 키는 카메라의 시점을 회전시킬 수 있어야 합니다. (왼쪽 및 오른쪽 보기)
  - W, A, S, D 키는 맵 내부에서 카메라를 이동시킬 수 있어야 합니다. (캐릭터의 이동)
  - ESC를 누르면 창이 닫히고 프로그램이 정상적으로 종료되어야 합니다.
  - 창 상단 표시줄에 있는 빨간색 십자가를 클릭하면 창이 닫히고 프로그램이 정상적으로 종료되어야 합니다.
  - 지도에 표시된 화면 크기가 디스플레이 해상도보다 크면, 현재 디스플레이의 해상도에 따라 윈도우 크기가 설정될 것입니다.
- 여러분의 프로그램은 먼저 .cub 확장자를 가진 지도 파일을 첫 번째 인자로 받아와야 합니다.
  - 지도는 4개의 문자로만 구성되어야 합니다. (빈 공간인 경우 0, 벽인 경우 1, 아이템은 2, 플레이어의 시작 위치와 그에 따른 시점은 N, S, E, W)
  - 간단하고 유효한 맵의 예시입니다 :
  ```
  111111
  100101
  102001
  1100N1
  111111
  ```
  - 지도는 벽으로 둘러쌓여 있어야 합니다. 그렇지 않다면 프로그램은 오류를 반환해야 합니다.
- 각 요소 (지도 제외) 의 첫 번째 정보는 (하나 또는 두개의 문자로 구성된) 유형 식별자이며, 각 객체에 대한 모든 구체적인 정보는 다음과 같은 엄격한 규칙을 따릅니다 :
  - 해상도 : R 1920 1080
  - 북쪽 벽 텍스쳐 : NO ./path_to_the_north_texture
  - 남쪽 벽 텍스쳐 : SO ./path_to_the_south_texture
  - 서쪽 벽 텍스쳐 : WE ./path_to_the_west_texture
  - 동쪽 벽 텍스쳐 : EA ./path_to_the_east_texture
  - 아이템 텍스쳐 : S ./path_to_the_sprite_texture
  - 바닥 색상 : F 220,100,0
  - 천장 색상 : C 225,30,0
### Development document
