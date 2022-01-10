# Python Enhancement Proposal (PEP) 8 Tutorial

이 책은 Python Enhancement Proposal (PEP)는 파이썬을 개선하기 위한 제안서, 즉 PEP에 대한 전반적인 개념을 설명하고 그 중에서도 Python 코딩 스타일에 대한 권고사항에 대한 PEP 8에 대한 튜토리얼을 제공하기 위해 작성되었습니다.

이 책의 저자는 파이썬을 좋아하고 즐겨 사용하는 청주대학교 인공지능소프트웨어전공 교수입니다.


```{admonition} 저자소개

청주대학교 소프트웨어융합학부 인공지능소프트웨어전공

노기섭 교수

Contact
- E-mail: kafa46@cju.ac.kr
- Phone: 043-229-8496 (유선)
- Mobile: Not open to public (private, 비공개)


```{figure} ./imgs/prof_noh.jpg
---
class: bg-primary mb-1
width: 200px
align: left
name: pythonic-image
---
청주대 노기섭 교수
```
---


PEP는 보다 나은 파이썬을 위한 다양한 의견을 체계적으로 정리한 문서를 의미합니다.

파이썬을 배우는 사람들은 먼저 문법을 배우고 다양한 예제 실습을 통해 프로그래밍 능력을 키워 갑니다. 파이썬 문법을 배우고 다양한 예제를 실습하는 것은 매우 중요합니다. 하지만 어느 수준 이상 올라가게 되면 더 이상 혼자서 코딩을 할 수 없게 됩니다.

일반적인 소프트웨어 개발의 경우 다양한 기능을 구현해야 하므로 다음과 같은 과정을 거치게 됩니다.

- 기능 단위로 소프트웨어를 구조화하고 각 기능을 분할합니다.
- 개발자 개인별로 구현해야할 기능을 나눠 갖습니다.
- 각자 단위 기능 개발을 끝내면 하나의 프로그램으로 통합합니다.
- 전체 기능을 테스트합니다.
- 프로그램을 배포(서비스 개시)하고 운영유지 단계로 진입합니다.
- 운영유지 단계에서는 다양한 변경 요구사항을 반영하여 지속적인 업그레이드를 합니다.

위 과정에서 일관된 코딩 스타일의 필요성이 등장합니다.

왜냐하면 다음과 같은 사건들이 끊임없이 발생하기 때문입니다.

```{admonition} 일관된 코딩 스타일이 필요한 경우

- 다른 팀원이 구현해서 보내준 소스코드를 받아보니 코드 분석이 어렵다.
- 모든 팀원의 코드를 통합(하나의 프로젝트로 완성) 해보니 코딩 스타일이 중구난방이다.
- Github에서 필요한 소스코드를 받았는데 해석이 어렵다.
- 우리 회사에서 개발한 소프트웨어를 다른 회사에서 유지보수하게 되었는데, 유지보수 개발자들이 우리 코드를 이해해지 못해 계속 컴플레인 한다.
- 내가 짠 코드인데 몇 달이 지나고 나니 나도 해석하기 어렵다. 
```

위와 같은 이유로 파이썬 개발자들은 공통된 Convention을 필요로 하게 되었습니다. 
코딩 Convention을 쉽게 이야기 하면 우리가 영어공부를 할 때 관용적 표현을 배우는 것과 비슷합니다.
**관용**이란 습관으로 굳어진 것을 의미합니다. 한자로 보면 '버릇 관 (慣)'과 '쓸 용(用)'이 합쳐서 오랫동안 써서 굳어진 대로 늘 사용하는 것을 뜻합니다. **관용적 표현**이라는 것은 관용적으로 굳어진 것들을 사용한다는 의미가 되겠습니다.

파이썬은 '프로그래밍 언어' 입니다. '언어'는 어떤 객체(object) 사이에서 소통하기 위한 수단입니다. 프로그래머라는 객체가 컴퓨터라는 객체와 소통하기 위해서는 당연히 언어가 필요합니다. 프로그래머가 컴퓨터와 소통하기 위한 언어는 다양합니다. Java, C, C++, Fortran, Go 등등 수없이 많습니다. 그 중에서 여러분들은 Python이라는 언어를 가지고 컴퓨터와 소통하고 있을 겁니다. 

Python도 언어이기 때문에 문법과 다양한 표현법이 존재합니다. 똑같은 기능을 구현하더라도 코딩하는 방법(코딩 스타일)은 다양하게 존재합니다. 프로그래머 입맛에 따라 거의 무한대의 방법이 존재할 겁니다. 하지만 영어(언어)의 관용구처럼 Python(언어)도 관용적 표현, 즉 관용적 코딩 스타일이 자연스럽게 생기게 됩니다. 이렇게 생긴 파이썬 관용적 표현들을 따라 코딩하는 것을 'Pythonic (파이쏘닉)' 하다고 말합니다. 


```{figure} ./imgs/pythonic.jpg
---
class: bg-primary mb-1
width: 350px
align: center
name: pythonic-image
---
Pythonic Image (source: https://tali.tistory.com/1356)
```

파이쏘닉한 소스코드는 다른 개발자들이 편하게 소스코드를 읽고 해석할 수 있기 때문에 **개발 속도**와 **유지보수 효율성**을 높일 수 있는 중요한 방법 중 하나입니다. 우리가 그걸 알면서 굳이 사용하지 않을 필요는 없는 겁니다.

그래서 등장한 것이 통일된 코딩 규칙을 갖자는 것입니다. 그 통일된 규칙을 체계적으로 정리한 것이 PEP 8입니다.
파이썬을 배우는 사람들은 문법과 실습에 집중하면서 자연스럽게 Pythonic 코드를 간접적으로 배우게 됩니다. 

하지만 어떤 경우는 전혀 그렇지 못한 경우도 있을 것입니다. Pythonic 하게 코딩하는 것은 그리 어려운 것이 아닙니다. Python 문법을 공부한 사람이라면 한두번 설명만 들으면 누구라도 할 수 있습니다.

PEP는 수많은 종류가 있습니다. 이번 튜토리얼은 PEP의 개념 'Style Guide for Python Code'로 불리는 PEP 8에 대하여 설명하겠습니다.

---

튜토리얼은 크게 2개의 Part로 구성되어 있습니다.

* Chapter 1: PEP의 개념과 종류에 대한 소개
* Chapter 2 ~ 10: PEP 8 구체적 설명 (Step by Step)

PEP 8은 파이썬의 코딩 스타일을 제안하는 내용입니다. 전문 개발자가 되기 위해 알아두어야 합니다. 파이썬 전문 개발자가 아니도라도 프로그래머들이 사용하는 코딩 스타일을 알고 있다면 협업이나 코드 분석을 쉽게 할 수 있는 장점이 있습니다. 

다시 말하면 프로그래밍 생산성을 높일 수 있다는 의미입니다. 파이썬 문법을 배우고 다양한 예제를 풀어보는 등 공부는 많이 하지만 코딩 스타일을 정확하게 배우는 경우는 드물게 됩니다. 이번 튜토리얼을 통해 보다 전문적인 지식을 얻기 바랍니다.

```{note}
튜토리얼은 파이썬 공식 홈페이지에 게시된 문서를 참고하여 작성되었습니다. 

**Python PEP**: https://www.python.org/dev/peps
```
