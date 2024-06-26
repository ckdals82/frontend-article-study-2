# Glob 패턴

다들 한 번쯤은 `*.ts` 형식의 경로 표현식을 작성해 본 경험이 있으실 거라 생각해요. 이 형식은 리눅스에서 파일을 찾을 때 사용하던 패턴 매칭 기법으로 **Glob 패턴**이라 불립니다.

현재 이 패턴은 리눅스 뿐만 아니라 대부분의 프로그래밍 언어에서도 지원하고 있습니다. 예를 들어 프론트엔드 개발 환경을 구축할 때 작성하게 되는 config.js 파일에도 이 패턴을 활용해 특정 파일에만 일부 설정을 적용하기도 합니다.

그만큼 너무 익숙한 패턴이지만, 정확한 의미를 모르고 감으로 사용하고 있는 경우가 빈번한 듯 하여 Glob 패턴에서 자주 쓰이는 문법들을 소개해 보려 합니다.

# 종류

## ?

딱 **한 글자**에 매칭되는 기호입니다. 

`a?` 라는 패턴은 `a1`, `az` 등의 문자열과 매칭됩니다.

## *

**여러 글자**에 매칭되는 기호입니다. 길이가 0인 문자열도 매칭됩니다.

예를 들어 `ts` 확장자를 가진 파일을 찾고 싶다면, `*.ts` 로 표현할 수 있습니다.

## **

**0개 이상의 하위 폴더**와 매칭되는 기호입니다. recursive folder를 의미하며 부분 경로라고 이해하면 쉽습니다.

예를 들어 `document/**/*.ts`는 document 폴더와 document의 자식 폴더 전체에서 ts 확장자를 가진 파일을 의미합니다. 그리고 `document/*/*.ts`는 document 폴더의 한 깊이 자식 폴더에서 ts 확장자를 가진 파일을 의미합니다.

config 파일에서 자주 볼 수 있는 `**/*.ts` 패턴은 현재 폴더 및 하위 폴더에 존재하는 모든 ts 확장자를 가진 파일을 의미합니다.

## {}

**괄호 안에 들어간 문자열**과 매칭되는 기호입니다. `{}` 내부에는 문자열이 올 수 있고, `콤마`로 구분하여 여러 개의 문자열을 작성할 수 있습니다.

예를 들어 `*.{ts,js}`는 `*.ts와 *.js`를 의미하고 이는 결국 ts나 js 확장자를 가진 파일을 의미합니다.

`{react}`는 react라는 문자열을 포함하는 문자열을 찾는 의미입니다. 이때 `{!react}` 라고 작성하면 react라는 문자열을 포함하지 않는 것과 매칭됩니다.

## []

**괄호 안에 들어간 각각의 글자**와 매칭되는 기호입니다. [] 내부에는 매칭하고자 하는 문자를 공백 없이 작성하면 되고 a-z와 같이 문자의 범위를 넣어줄 수도 있습니다.

예를 들어 `*[abc]*.ts`는 ts 파일 중 이름에 a 또는 b 또는 c가 들어가는 파일을 의미합니다.

## ()

있어도 되고 없어도 되는 부분과 매칭되는 기호입니다. 빈문자열도 매칭됩니다.

예를 들어 현재 폴더 및 하위 폴더를 대상으로 js나 jsx 확장자를 가진 파일을 검색하고 싶다면 `**/*.js?(x)` 패턴을 사용할 수 있습니다.

# glob과 정규 표현식의 차이

두 패턴은 문법이 유사하지만 미묘하게 다릅니다.

glob은 주로 파일을 검색하는 용으로 많이 사용되고, 정규 표현식은 glob보다 문법이 상세하기 때문에 정교한 문자열 검색을 위해 사용됩니다.

# 마치며

저처럼 느낌적으로 이해하고 사용하셨다면, 이번에 알아가는 기회가 되셨으면 합니다 😁

감사합니다.