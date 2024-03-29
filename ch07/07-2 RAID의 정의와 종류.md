생성일 | 2024.01.10
작성자 | 이지현
# 07-2 RAID의 정의와 종류

### 요약
- RAID란 데이터의 안전성 혹은 높은 성능을 위해 여러 하드 디스크나 SSD를 마치 하나의 장치처럼 사용하는 기술
- RAID 0은 데이터를 단순히 병렬로 분산하여 저장하고, RAID 1은 완전한 복사본을 만든다.
- RAID 4는 패리티를 저장한 장치를 따로 두는 방식이고, RAID 5는 패리티를 분산하여 저장하는방식이다.
- RAID 6은 서로 다른 두 개의 패리티를 두는 방식이다.

---
## RAID의 정의

> 보조기억장치에도 수명이 있다.

RAID: 하드 디스크와 SSD를 사용하는 기술로, 데이터의 안전성 혹은 높은 성능을 위해 여러 개의 물리적 보조기억장치를 마치 하나의 논리적 보조기억장치처럼 사용하는 기술

---

## RAID의 종류

RAID 레벨: RAID 구성 방법
RAID2, 3은 현재 잘 활용되지 않는다.

### RAID 0
여러 개의 보조기억장치에 데이터를 단순히 나누어 저장하는 구성 방식
저장되는 데이터가 하드 디스크 개수만큼 나뉘어 저장되는 것
- 스트라입(stripe): 마치 줄무늬처럼 분산되어 저장된  데이터
- 스트라이핑(striping): 분산하여 저장하는 것
-> 저장된 데이터를 읽고 쓰는 속도가 빨라진다.

이론상, 4TB 저장 장치 한 개를 읽고 쓰는 속도보다 RAID 0으로 구성된 1TB 저장 장치 네 개의 속도가 네 배가량 빠르다.
그러나, 구성된 하드 디스크 중 하나에 문제가 생긴다면 다른 모든 하드 디스크의 정보를 읽는 데 문제가 생길 수 있다.

### RAID 1
RAID 0의 단점을 보완하기 위해 나온 방식으로 복사본을 생성한다.
- 미러링(mirroring): 거울처럼 완전한 복사본을 만드는 구성이기에 RAID 1을 달리 부르는 말
같은 구성에서 복사본을 저장하는 데 쓰이는 디스크가 있기 때문에 쓰는 속도는 RAID 0 보다 느리다. 즉, 디스크가 한정되었을 때 사용 가능한 용량이 적어지고, 용량을 늘리기 위해서는 비용적인 문제가 있다.

### RAID 4
RAID 1처럼 복사본을 만드는 대신 오류를 검출하고 복구하기 위한 정보(패리티 비트)를 저장한 장치를 두는 구성 방식
패티리를 저장한 장치를 이용해 다른 장치들의 오류를 검출하고, 오류가 있다면 복구한다.
RAID 1보다 적은 하드 디스크로도 데이터를 안전하게 보관할 수 있다.

> [!패리티 비트]
> 패리티 비트는 오류 검출만 가능할 뿐 오류 복구는 불가능하다. 하지만 RAID에서는 패리티 값으로 오류 수정도 가능하다.

그러나 새로운 데이터가 저장될 때마다 패리티를 저장하는 디스크에도 데이터를 쓰게 되므로 패리티를 저장하는 장치에 병목 현상이 발생한다.
### RAID 5
RAID 4의 문제점을 개선하여 패리티 정보를 분산하여 저장하는 식

### RAID 6
기본적인 구성은 RAID 5와 같으나, 서로 다른 두 개의 패리티를 두는 방식
오류를 검출하고 복구할 수 있는 수단을 두 개로 둔 것으로 RAID 4, 5 보다 안전한 구성이다.
그러나, 함께 저장할 패리티가 두 배로 는 만큼 쓰기 속도는 RAID 5보다 느리다.

이외의 방식
RAID 10 : RAID 0 + RAID 1
RAID 50 : RAID 0 + RAID 5

> RAID 레벨마다 장단점이 있으므로 어떤 상황에서 무엇을 최우선으로 원하는지에 따라 최적의 RAID 레벨이 달라질 수 있다. 그렇기에 각 RAID 레벨의 대략적인 구성과 특징을 아는 것이 중요하다.

----
### 퀴즈

디스커션 링크: