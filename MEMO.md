## 検証1

```
- name: "Checkout GitHub Action"
  uses: actions/checkout@v4
  with:
    fetch-depth: 0
```
の記述がどこを参照するか

### mainブランチマージ時 > Action1 (push trigger で起動)

`main`

### mainブランチマージ時 > Action2 (workflow_run trigger で起動)

`main`

### productionブランチマージ時 > Action1 (push trigger で起動)

`production`

### productionブランチマージ時 > Action2 (workflow_run trigger で起動)

`main`

### 手動実行時 > Action1

「Use workflow from」で指定されたブランチ

### 手動実行時 > Action2

「Use workflow from」で指定されたブランチ


### 手動実行時 > Action1から連鎖して実行されるAction2

`main`

## 検証2

```
- name: "Checkout workflow_dispatch GitHub Action"
  if: github.event_name == 'workflow_dispatch'
  uses: actions/checkout@v4
  with:
    ref: ${{ github.event.workflow_run.head_branch }}
    fetch-depth:
- name: "Checkout workflow_run GitHub Action"
  if: github.event_name == 'workflow_run'
  uses: actions/checkout@v4
  with:
    ref: ${{ github.event.workflow_run.head_branch }}
    fetch-depth: 0
```
の記述がどこを参照するか

### mainブランチマージ時 > Action1

`main`

### mainブランチマージ時 > Action2

`main`

### productionブランチマージ時 > Action1

`production`

### productionブランチマージ時 > Action2

`production`

### 手動実行時 > Action1

「Use workflow from」で指定されたブランチ

### 手動実行時 > Action2

「Use workflow from」で指定されたブランチ


### 手動実行時 > Action1から連鎖して実行されるAction2

「Use workflow from」で指定されたブランチ
