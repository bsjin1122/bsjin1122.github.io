---
title: "[Oracle] "
excerpt: "Test"
categories: [TIL, Oracle]
tags:
  - [Oracle]

toc: true
toc_sticky: true

date: 2024-09-24
last_modified_at: 2024-09-24
---

## 메타데이터(metadata)

- 데이터베이스 = 자료 창고
  - 데이터 모델링 = 자료창고를 건설하기 위한 설계도면
  - 어떤 종류의 데이터인지 구조화하기 위한 데이터
- 데이터를 구조화하기 위한 데이터
  - 다른 데이터를 설명해주는 속성 데이터라는 의미로 : 메타데이터라고 부른다.
    > 정보를 효율적으로 찾아내기 위해, 일정한 규칙에 따라 데이터베이스 스키마에 부여되는 데이터이다.

## 데이터 딕셔너리

- 메타데이터를 구조화하여, 체계적으로 갖춘 시스템 목록(system catalog)를 데이터 딕셔너리라고 부른다.
- 딕셔너리의 소유자 : SYS (oracle 서버에 의해 관리됨)
  - 더 간편하게 제공한 뷰 테이블: DICTIONARY
  - `SELECT * FROM DICTIONARY;`

| 유형     | 기능                                                                                              |
| -------- | ------------------------------------------------------------------------------------------------- |
| USER_XXX | 현재 사용자가 생성한 객체에 관련된 정보를 제공                                                    |
| ALL_XXX  | 현재 사용자가 접근 가능한 모든 객체에 관련된 정보를 제공                                          |
| DBA_XXX  | DBA 권한을 가진 사용자만이 접근할 수 있는 정보를 제공<br> \*tip: 복수                             |
| V$\_XXX  | 데이터베이스 성능분석/통계 정보를 제공하며, X$ 테이블에 대한 뷰 V\$*\*\* 목록보기 <br> *tip: 단수 |
| GV$\_XXX | GV$\*\*\*\* 목록 보기                                                                             |
| X$\_XXX  | 데이터베이스 성능 분석, 통계 정보를 제공하는 테이블 x$\*\*\* 목록 보기                            |

### 자주 사용되는 딕셔너리

- DBA_OBEJCTS
- DBA_SEGMENTS
- DBA_TAB_COLUMNS
  <br>

그 외

- DBA_SYS_PRIVS -- 직접 부여된 시스템 권한
  - ADMIN_OPTION: 해당 권한을 다른 사용자에게 부여할 수 있는지 여부 (YES, NO)
- DBA_ROLE_PRIVS: 사용자 또는 역할에 부여된 역할을 보여주는 뷰
  - 역할 자체가 시스템 및객체 권한을 포함할 수 있다.
- V$INSTANCE
- V$SESSION
- V$PROCESS -- 실행중인 프로세스를 확인할 수 있다.
- V$LOG -- REDO LOG 에 대한 내용을 보여준다.
  - SqlPlus로 접속후 alter system checkpoint; 로 한 다음 다시 확인해보면 알 수 있다.
- GV$INSTANCE -- 접속된 노드 2개를 같이 보여준다.
