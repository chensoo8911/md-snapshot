# Changelog

本檔案記錄 md-snapshot 的變更歷史。格式參考 [Keep a Changelog](https://keepachangelog.com/zh-TW/1.1.0/)。

版本號採 [Semantic Versioning](https://semver.org/lang/zh-TW/)：MAJOR.MINOR.PATCH。

## [Unreleased]

## [1.1.0] — 2026-10-29

### Added
- **快照前先用 sha1 去重**：內容跟最新一份快照一模一樣就不存、直接回報「已跳過」。快照的價值是「這天跟前一天不一樣」，存重複的只會讓人誤以為中間有改過。比對用 sha1 而不是檔案大小，因為大小相同不代表內容相同。
- **同一天多次快照自動加流水號**（`_YYYYMMDD-2.md`、`-3`…），不再詢問、也一律禁止覆寫，避免當天較早那份被蓋掉。

### Changed
- skill 名稱拿掉 `claude-` 前綴（`claude-md-snapshot` → `md-snapshot`），觸發詞不變。
- 精簡 SKILL.md 的 description，降低每個 session 常駐的 context 成本。
- 要大改全域 CLAUDE.md 前可直接快照、不必先問，讓「改前留底」變成順手的事。
- `.gitignore` 補擋 `.DS_Store`、`backups/`、`/CLAUDE.md`，避免本機備份與維護筆記被推上公開 repo。

## [1.0.0] — 2026-07-15

### Added
- 首次正式發版：把全域 CLAUDE.md 另存日期快照的 skill。觸發詞「快照全md」。
- 快照資料夾／檔名前綴改用個人設定檔 `~/.config/md-snapshot/env`，沒有設定則用通用預設值，供他人使用不寫死任何個人路徑。
