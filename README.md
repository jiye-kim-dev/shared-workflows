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
    uses: jiye-kim-dev/shared-workflows/.github/workflows/pr-ticket-summary.yml@v1
```