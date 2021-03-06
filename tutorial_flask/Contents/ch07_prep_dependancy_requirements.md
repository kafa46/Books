# 준비 5. 의존성 파일 `requirement.txt` 생성 

## 의존성의 개념

`의존성 파일`이라는 것이 왜 필요할까요?
개발자들은 개발(코딩)을 안정적으로 진행하고 테스트하기 위하여 독립된 환경,
즉 가상환경(virtual environment)를 만들어서 코딩을 합니다.

이렇게 완성된 코드는 `git`을 이용해 원격 저장소에 업로드하여 공유하거나 협업하게 됩니다.
때로는 이메일이나 카톡으로 소스코드를 주고 받을수도 있습니다.
문제는 나에게 코드를 공유한 사람이 어떤 환경에서 개발했는지 알 수 없다는 겁니다.

따라서, 코드를 공유할 사람(다른 사람에게 전달하는 개발자)은  
본인의 가상환경에서  어떤 패키지나 라이브러리를 설치하여 개발했는지도 같이 알려줘야 합니다.
이렇게 코드를 전달하는 사람의 가상환경을 정리한 파일을 `의존성 파일`이라고 합니다.

`의존성 파일`은 파이썬에서 지원하는 패키지 관리자 `pip`를 이용해 손쉽게 작성할 수 있습니다.

그런데 한 가지 문제는 `의존성 파일` 이름은 누구나 마음대로 지을 수 있다는 것입니다.
어떤 개발자는 `dependancy.txt`라고 지을 수 있고,
또 다른 개발자는 `virtual_env.txt`라고 지을 수도 있겠죠?
그래서 `의존성 파일`의 이름을 누가 보더라도 쉽게 알도록 통일하기로 했습니다.
그 통일된 이름이 `requirements.txt` 입니다.

의존성 파일 `requirements.txt`를 만들어 보겠습니다.
먼저 본인이 개발한 가상환경에 진입합니다.
앞에서 배운대로 `conda activate 가상환경이름`을 통해서 가상환경을 활성화 하겠죠?

```{figure} ../imgs/vscode_09_create_requirements.txt.png
---
width: 500
align: left
alt: create requirements.txt
name: create_requirements.txt
---
VS Code에서 의존성 파일 `requirements.txt` 만들기
```

먼저 작업한 가상환경으로 들어갑니다.

`requirements.txt` 파일을 만들기 위해
`pip3 freeze > requirements.txt`라는 명령어를 입력하고 엔터를 칩니다.

- 윈도우즈 운영체제일 경우 `pip` 명령어를 사용하고, 리눅스/macOS일 경우 `pip3` 명령어를 사용합니다.
- `freeze`는 현재 환경에서 사용하고 있는 모든 패키지 목록을 모니터(콘솔, 터미널)에 출력하라는 명령어 입니다.
- `>`는 모니터(터미널, 콘솔)에 출력되는 내용의 방향을 바꾸라는 말입니다. 
  - 방향을 바꾼다는 것을 `재지향(redirection)`한다고 표현합니다. 
  - 모니로 출력되는 방향을 바꿔서 파일로 출력하도록 합니다.
- `requirements.txt`는 `>`에 의해 출력의 방향이 모니터에서 파일로 바꾼 경우, 내용을 저장할 파일 이름 입니다
  - 파일 이름은 아무거나 사용해도 됩니다.
  - `의존성 파일` 이름을 `requirements.txt`로 정했기 때문에 그대로 사용한 것입니다.

`pip3 freeze > requirements.txt`가 실행되면
VS Code 우측의 파일 탐색기에 `requirements.txt` 파일이 생성된 것을 확인할 수 있습니다.

`requirements.txt` 파일을 클릭하면 내용을 확인할 수 있습니다. 
`requirements.txt`에 기록된 내용은 현재 환경에서 사용하고 있는 모든 패키지를 이름과 버전 정보가 포함되어 있습니다.
소스코드를 전달받은 개발자는 `requirements.txt`를 확인하고 어떤 개발 환경에서 개발했는지 쉽게 알 수 있습니다.

`requirements.txt` 파일을 이용하면 소스코드를 나에게 전달한 사람과 
동일한 가상환경을 다음과 같이 손쉽게 생성할 수 있습니다.

- 가상환경을 하나 만듭니다.
- 새로 만든 가상환경에 들어갑니다.
- 아래와 같이 명령어를 주면 `requirements.txt`에 있는 모든 패키지가 자동으로 설치됩니다.

    ```bash
    pip3 install -r requrirements.txt
    ```
