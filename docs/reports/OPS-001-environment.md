# OPS-001 環境驗證報告

- 對應工作單：#4 OPS-001
- 執行角色：claude-cowork
- 執行日期／批次：2026-09-11 batch-1（Asia/Taipei）
- 基準 commit：`28eac487197f2166557147293df5f5635473c16e`（main）
- 工作分支：`work/4-ops-001-env-verify`（本機建立，見「限制」一節）

## 環境確認

實際執行環境為既有雲端 shell（Linux 6.8.0-134-generic），工具版本：

```
$ git --version
git version 2.43.0

$ gh --version
gh version 2.45.0 (2025-07-18 Ubuntu 2.45.0-1ubuntu0.3)
```

`gh auth status` 顯示已登入帳號 `paramecium21-claude`（active）與 `parameciumvance`（非 active）。

## 實際執行命令與結果

### 1. 讀取領單規則與工作單

依序讀取 `AGENTS.md`、`CLAUDE.md`、`docs/workflow.md`、`docs/work-items.md`、`README.md`、`docs/project.md`，並以 `gh issue view 4 --json ...` 取得 Issue #4 完整內容與留言（無既有留言，Status 為 `ready`）。同時以 `gh issue view 1` 確認固定日報 Issue 目前無留言。

### 2. 領單留言

```
gh issue comment 4 --body "..."
```
結果：成功，留言連結
https://github.com/parameciumvance/paramecium_product/issues/4#issuecomment-5629261383

### 3. 嘗試將 Issue #4 的 `Status` 由 `ready` 改為 `doing`

```
gh issue edit 4 --body-file /tmp/issue4_body.txt
```
結果：**失敗**。

```
failed to update https://github.com/parameciumvance/paramecium_product/issues/4:
GraphQL: paramecium21-claude does not have the correct permissions to execute `UpdateIssue` (updateIssue)
```

### 4. 確認 repo 權限層級

```
$ gh repo view parameciumvance/paramecium_product --json viewerPermission
{"viewerPermission":"READ"}
```

`paramecium21-claude` 對本 repo 只有 READ 權限，無法編輯 Issue 欄位，也無法查詢 collaborator permission（`Must have push access to view collaborator permission.`）。

### 5. 嘗試建立分支並推送

```
$ git checkout -b work/4-ops-001-env-verify
Switched to a new branch 'work/4-ops-001-env-verify'

$ git push -u origin work/4-ops-001-env-verify --dry-run
remote: Permission to parameciumvance/paramecium_product.git denied to paramecium21-claude.
fatal: unable to access '...': The requested URL returned error: 403
```

結果：**失敗**，帳號無 push 權限，無法推送分支或建立 PR。

### 6. Markdown 本地連結核對

檢查 `README.md`、`CLAUDE.md`、`AGENTS.md`、`docs/*.md`、`docs/reports/README.md` 中所有非 `http` 開頭的相對連結，逐一確認目標檔案是否存在。

結果：全部 10 條本地連結皆指向存在的檔案，**沒有失效連結**。

### 7. 應用程式測試

目前 repository 只有專案協作文件，尚無應用程式程式碼、建置設定或測試套件。**尚無應用測試** — 未執行、也無可執行的測試。

## 重跑方法

1. `git fetch origin && git log -1 origin/main` 確認基準 commit。
2. 重複第 6 步的本地連結檢查：對每個 markdown 檔案中 `[text](relative/path)` 形式的連結，確認 `relative/path` 對應檔案存在。
3. 重複第 3、5 步驗證帳號權限是否已調整（預期在權限修正後應能成功）。

## 已知限制

- **帳號權限阻塞**：`paramecium21-claude` 目前對 `parameciumvance/paramecium_product` 僅有 READ 權限，無法編輯 Issue 欄位（含 `Status`）、無法 push 分支、無法開 PR。本工作單要求的「建立分支、提交 PR、將 Status 改為 doing/review」因此無法在此帳號下完成，需總監或老闆將帳號權限提升為至少 Write（或改用有權限的帳號）。
- 本報告與相關程式碼變更目前只存在於本機分支 `work/4-ops-001-env-verify`，尚未推送至 GitHub，待權限修正後補推並開 PR。
- 尚無應用程式，因此「應用測試」一項標記為未執行；本任務範圍僅涵蓋協作流程與文件驗證。
