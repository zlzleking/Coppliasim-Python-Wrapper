# Coppliasim-Python-Wrapper

## 개요
이 프로그램은 Coppliasim의 Python api를 조금 더 쉽게 사용할 수 있게 해 주는 래퍼입니다.
Coppliasim은 기본적으로 Lua 언어를 사용한 스크립트로 구동됩니다. 하지만 Lua언어의 특성 상 간단한 시뮬레이션은 작성하기 쉬우나, 복잡하거나 외부 환경과 연동된 시뮬레이션을 사용하기는 무리가 있습니다. 따라서 Coppliasim은 기본적으로 다른 언어와 연동된 API를 제공하나, Lua함수와 1:1대응되는 측면이 있어 익숙하지 않은 사람이 쉽게 사용하기는 힘듭니다. 따라서 이 래퍼가 만들어졌습니다.

## Coppliasim API의 특성
Coppliasim은 기본적으로 실행될 시 19997포트에 API 서버를 개방합니다. 이 포트를 통해 값을 입력받으면 시뮬레이션 내의 요소를 조작할 수 있습니다.

Coppliasim의 모든 요소는 양수 값의 Handle을 가지고 있습니다. 시뮬레이션에서 해당 요소를 조작하기 위해서는 항상 Handle을 입력해야 합니다. 만약 시뮬레이션 내에서 해당 요소의 Handle을 찾는데 실패했다면 0 혹은 음수의 값이 반환됩니다. Handle 값을 체크하지 않고 실행된다면 예기치 않은 결과를 야기할 수 있습니다.

Coppliasim 스크립트는 동기와 비동기 스크립트로 나눠져 있습니다. (메뉴의 Threaded와 Non-Threaded에 해당합니다.) 이 래퍼는 작동의 편의 상 모든 코드가 동기 환경에서 구동됩니다. 만약 이 부분을 고치거나 비동기화된 영역을 만들고 싶다면 [이 문서](https://www.coppeliarobotics.com/helpFiles/en/remoteApiConstants.htm#operationModes)를 참고해 주세요.

## 객체 설명
이 래퍼는 env객체와 bot객체로 구성됩니다. env객체는 coppliasim에서 제공하는 일반적인 요소를 조작하는 데에 사용됩니다. 따라서 해당 물체의 위치와 같은 것들을 변경할 수 있습니다. bot 객체는 coppliasim의 IK 그룹으로 엮인 물체를 조작하는 데에 사용됩니다. 따라서 Tip과 Target의 handle을 입력받아 생성해야 합니다.

## 사용법
기본적으로 env 객체를 만든 다음 bot 객체를 생성해서 사용하면 됩니다. env객체가 생성될 때 시뮬레이션과 연결이 수립됩니다. bot 객체는 env객체를 입력받아서 생성해야 합니다.

### 의존성
Coppliasim의 python api를 기반으로 동작하기 때문에 관련 파일을 같은 디렉토리에 넣어야 동작합니다. 기본적으로는 [이 문서](https://www.coppeliarobotics.com/helpFiles/en/remoteApiClientSide.htm)를 참조해 주세요.

