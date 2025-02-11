## 検証1

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

## 検証1

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
