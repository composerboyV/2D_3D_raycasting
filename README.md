# 🎮 Cub3D - Raycasting Engine

![Language](https://img.shields.io/badge/Language-C-00599C?style=for-the-badge&logo=c&logoColor=white)
![Library](https://img.shields.io/badge/Library-MinilibX-orange?style=for-the-badge)
![Subject](https://img.shields.io/badge/Subject-Computer_Graphics-blue?style=for-the-badge)

> **Wolfenstein 3D** 스타일의 레이캐스팅(Raycasting) 엔진을 구현한 3D 그래픽 프로젝트입니다.  
> 2D 맵을 3D 시점으로 렌더링하며, **DDA 알고리즘**과 **텍스처 매핑** 기술을 깊이 있게 탐구했습니다.

---

## ✨ Key Features (핵심 기능)

이 프로젝트는 단순한 3D 렌더링을 넘어, 실제 게임과 같은 상호작용을 제공합니다.

-   🛠 **Raycasting Architecture**: DDA 알고리즘을 사용하여 벽과의 거리를 정밀하게 계산하고 렌더링합니다.
-   🎨 **Texture Mapping**: 동/서/남/북 방향에 따라 다른 텍스처를 적용하여 입체감을 극대화했습니다.
-   🏃 **Player Movement**:
    -   `WASD` 키를 이용한 부드러운 이동
    -   좌우 화살표 키를 이용한 시점 회전
    -   벽 충돌 감지 (Collision Detection) 및 미끄러짐 처리
-   🗺 **Robust Map Parsing**: 
    -   `.cub` 파일 형식 지원
    -   맵 유효성 검사 (벽으로 둘러싸여 있는지, 플레이어 위치가 올바른지 등)
    -   천장(Ceiling)과 바닥(Floor) 색상 커스터마이징

---

## 🛠 Tech Stack & Implementation

### 1. Raycasting (레이캐스팅)
레이캐스팅은 플레이어의 시점에서 광선(Ray)을 쏘아 벽에 부딪히는 지점을 찾는 기술입니다. 
- **FOV (Field of View)**: 66도 화각을 설정하여 자연스러운 시야각 제공
- **DDA Algorithm**: 그리드 기반 맵에서 광선이 벽에 닿는지 효율적으로 검사

### 2. Texture Management
- **XPM 이미지 파싱**: 직접 텍스처 데이터를 읽어와 메모리에 로드
- **Texture Coordinate Calculation**: 벽에 부딪힌 위치에 따라 텍스처의 어느 부분을 그려야 할지(TexX) 정확히 계산

### 3. Optimization
- **Double Buffering**: 화면 깜박임 방지를 위한 이미지 버퍼링 구현
- **Memory Management**: 누수 없는 깔끔한 메모리 해제 로직

---

## 🚀 Installation & Usage

### Prerequisites
- **GCC** or **Clang** Compiler
- **Make**
- **MinilibX** dependencies (Linux 환경에서는 `X11`, `XExt` 필요)

### Build & Run
레포지토리를 클론하고 `make`를 실행하세요.

```bash
# 1. 레포지토리 클론
git clone https://github.com/yourusername/cub3d.git
cd cub3d

# 2. 컴파일
make

# 3. 실행 (맵 파일 경로 지정)
./cub3D maps/test.cub
```

---

## 🎮 Controls

| Key | Action | 설명 |
| :---: | :---: | --- |
| `W` | Move Forward | 앞으로 이동 |
| `S` | Move Backward | 뒤로 이동 |
| `A` | Move Left | 왼쪽으로 게걸음(Strafe) |
| `D` | Move Right | 오른쪽으로 게걸음(Strafe) |
| `←` | Rotate Left | 시점 왼쪽 회전 |
| `→` | Rotate Right | 시점 오른쪽 회전 |
| `ESC` / `X` | Exit | 게임 종료 |

---

## � Map Configuration (`.cub`)

맵 파일은 텍스처 경로, 색상 정보, 그리고 맵 구조를 정의합니다.

```text
NO ./textures/north_wall.xpm  # 북쪽 벽 텍스처
SO ./textures/south_wall.xpm  # 남쪽 벽 텍스처
WE ./textures/west_wall.xpm   # 서쪽 벽 텍스처
EA ./textures/east_wall.xpm   # 동쪽 벽 텍스처

F 220,100,0  # 바닥 색상 (RGB)
C 225,30,0   # 천장 색상 (RGB)

        1111111111111111111111111
        1000000000110000000000001
        1011000001110000000000001
        100100000N000000000000001
111111111011000001110000000000001
100000000011000001110111111111111
111111111111111111111111111111111
```

- `1`: 벽 (Wall)
- `0`: 빈 공간 (Empty Space)
- `N`, `S`, `E`, `W`: 플레이어 시작 위치 및 시선 방향

---

<div align="center">
  <sub>Developed by <b>Junkwak</b> | 42 GyeongSan Project</sub>
</div>

