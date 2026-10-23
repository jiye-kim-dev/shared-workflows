# shared-workflows
모든 repository 에서 사용할 workflow 모음

---

## How to use

#### reusable workflow

`on: workflow_call` 옵션 명명한 채로 사용하고 싶은 워크플로 지정 

```yaml
on:
  workflow_call:
    inputs:
      ticket-prefix:
        type: string
        default: JOB

jobs:
  summarize:
    runs-on: ubuntu-latest
    steps:
    # ...
```

이후, 사용하고 싶은 개인 레퍼지토리에서 링크 연결
```yaml
name: PR ticket summary

on:
  pull_request:
    branches: [develop]

jobs:
  summary:
    uses: jiye-kim-dev/shared-workflows/.github/workflows/pr_ticket_summary.yml@v1
```

--- 


## List
- pr_ticket_summery : Jira 티켓 기준으로 Commit Message 내용 취합
- release_tag : Production 배포시 버전 관리를 위한 자동 태깅처리