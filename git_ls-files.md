# ls-files

ls-files 명령은 Index(스테이징 영역)과 관련된 정보를 출력하는 명령

## 기본 명령
'''
git ls-files
'''
- Index 에 등록된 모든 파일 정보를 출력
- Tracked 파일 목록 확인

## 옵션

-s / --stage : 모드, Blob id, 경로를 출력
-u / --unmerged : 병합 충돌 파일만 출력
-k / --killed : 삭제된 파일

-d / --deleted : Working Directory 에서 삭제된 Tracked File
-m / --modified : 수정된 파일
--cached : Index 에 존재하는 파일

# Staing Area

git commit 은 Staging Area 의 변경사항을 커밋한다.

Staging Area 가 변경사항이 없다는 것은 Working Directory 와 동일한 상태를 의미한다.

git ls-files -s 명령은 Index 에 존재하는 모든 파일 목록을 조회한다.

커밋 이후에도 ls-files -s 명령의 결과는 동일하다.

## 비어있다. 의 의미

Index 가 비어있다. 커밋할 변경사항이 없다. Index 에 커밋되지 않은 변경사항이 없다는 의미. Index 와 Working Directory 가 동일한 상태라는 의미

Git은 항상 Index 에 현재 작업 중인 스냅샷을 유지한다. 

# tree

## tree

- 커밋 시점의 파일과 디렉토리 구조를 나타낸다
- 커밋 객체가 참조하는 고정된 스냅샷
- 읽기 전용 / 변경되지 않음

확인 
  - git cat-file -p HEAD^{tree}  
  - 마지막 커밋의 tree를 출력

## index

- 독립적인 데이터 구조
- index를 통해 Staging Area를 관리
- HEAD가 가리키는 커밋 기준으로 index가 초기화(동기화) 된다.
- 커밋 시점에 index를 참조하여 tree를 새롭게 생성한다.

확인
  - git ls-files -s
  - git cat-file -p HEAD 와 동일하면 tree와 동기화된 상태

### 초기화
마지막 commit 의 tree 기준으로 index 초기화

### 변경
워킹 디렉토리의 변경사항은 index 에 자동으로 반영되지 않는다
git add 명령이 실행되어야 index 가 변경된다.

### 커밋

index 상태를 기반으로 tree 를 생성
생성된 tree 는 commit 에 포함되며 HEAD가 이를 참조한다

### 동기화

커밋 이후에 index 는 새롭게 생성된 tree 객체로 다시 동기화된다.

## index 엔트리 구조

파일별로 다음 정보를 저장

- 파일 경로
- Blob id
- File Mode
- 타임스탬프
- 파일 크기
- 상태 플래그 (추가, 삭제, 수정 등)

### 상태 플래그

Modified : Working Directory 변경 발생. index에 반영 안됨. git diff 로 감지
Staged : 변경사항이 index 에 반영됨. git diff --cached 로 확인
Unmerged : 병합 충돌
Deleted : 파일이 삭제됨

상태 플래그 보기

1. Staged 변경사항 확인
```
git diff --cached --name-satus
```
