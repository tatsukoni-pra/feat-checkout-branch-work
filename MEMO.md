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

## 検証2

```
- name: "Checkout GitHub Action"
  uses: actions/checkout@v4
  with:
    fetch-depth: 0
```
の記述がどこを参照するか

### mainブランチマージ時 > Action1

### mainブランチマージ時 > Action2

### productionブランチマージ時 > Action1

### productionブランチマージ時 > Action2

### 手動実行時
