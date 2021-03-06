---
title:  "정올반 프로젝트 - 그래프 컬러링"
date: 2019-02-01 01:26:00
categories:
- SunrinKoi
tags:
- Sunrin-Koi
---

겨울방학동안 교내 정올반에서 2인 1조로 프로젝트를 진행했습니다.<br>
대주제는 휴리스틱으로 정했고, 소주제는 팀 별로 각자 정하게 되었습니다.<br>
저는 유전 알고리즘을 이용한 그래프 컬러링 문제(GCP, Graph Coloring Problem) 해결을 주제로 프로젝트를 진행했습니다.<br>
그 외에 다른 팀의 주제를 보면,
1. 크롬 공룡 게임 학습
2. 아타리 학습
3. SAT문제

등 다양한 주제로 프로젝트를 진행했습니다.

---

그래프는 다항 시간 안에 해결할 수 있는 방법이 알려지지 않았지만, 어떤 데이터가 주어지면 그 데이터가 정답인지는 다항 시간 안에 판별할 수 있는 NP-Complete클래스에 속하는 문제입니다. 다항 시간 안에 해결하는 방법이 아직 알려지지 않았기 때문에, 이 문제를 효율적으로 해결하기 위해 다양한 연구가 진행이 되어왔습니다.<br>
이 프로젝트에서는 간단하면서도 강력한 유전 알고리즘을 이용해 GCP를 해결해보기로 했습니다.

---

유전 알고리즘을 돌리기 위해 몇 가지를 먼저 결정해야 합니다.<br>
아래 항목을 결정할 때 <b>효율성</b>과 <b>구현 난이도</b> 두 가지를 중점적으로 고려했습니다.

1. <b>해의 표현</b><br>
그래프의 정점의 개수를 V, 사용할 색깔의 수를 K라고 하면, 각 유전자는 0부터 K-1까지의 정수로 이루어진 길이 V의 순열로 나타냅니다.
2. <b>적합도 함수</b><br>
임의의 간선 {u, v}에 대해 정점 u, v의 색깔이 같은 간선의 개수를 기준으로 적합도를 판별하고, 적합도의 값을 0으로 만드는 것이 이 프로그램의 목적입니다.
3. <b>선택 연산</b><br>
두 개의 유전자 중 더 우월한 유전자를 부모 유전자로 사용하는 토너먼트 선택 기법을 사용합니다.
4. <b>교차 연산</b><bR>
유전자에서 각 점에 대해 두 부모 유전자 중 랜덤하게 하나를 골라 채용하는 균등 교차 기법을 사용합니다.
5. <b>변이 연산</b><br>
유전자의 매 점마다 0.15%의 확률로 0부터 K-1까지의 정수 중 하나로 교체하는 변이 연산을 수행합니다.
6. <b>대치 연산</b><br>
매 세대마다 토너먼트 선택에서 탈락된 유전자들을 교차 연산에서 생성된 유전자로 교체합니다.
7. <b>정지 조건</b><br>
적합도 함수의 값이 0인 유전자를 찾거나, 50만 세대가 넘어가면 진화를 종료합니다.

---

성능 측정 코드(C++), visualization 코드(JS), 보고서, 발표 슬라이드 모두 <a href = "https://github.com/justiceHui/GCP-by-GeneticAlgorithm/">깃허브</a>에서 보실 수 있습니다.

참고로, 추가적인 최적화가 추후에 진행될 수 있습니다.
