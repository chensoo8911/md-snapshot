# md-snapshot — CLAUDE.md 快照備份（Claude Code Skill）

在大幅修改全域 `~/.claude/CLAUDE.md` 前，先複製一份帶日期的快照，方便之後比對或還原。

## 這是什麼

- **輸入**：你說「快照全md」。
- **動作**：用 `cp`（絕不用 `mv`）把 `~/.claude/CLAUDE.md` 複製一份到快照資料夾，檔名帶當天日期。
- **首次使用**會問你要存去哪個資料夾、檔名前綴叫什麼，之後記住（寫進 `~/.config/md-snapshot/env`），不用每次再問。

## 安裝

```bash
git clone <REPO_URL> md-snapshot
mkdir -p ~/.claude/skills/md-snapshot
cp md-snapshot/SKILL.md ~/.claude/skills/md-snapshot/SKILL.md
```

或用 symlink（source of truth 留在 clone 下來的 repo，之後 `git pull` 就自動更新）：

```bash
git clone <REPO_URL> ~/somewhere/md-snapshot
ln -s ~/somewhere/md-snapshot ~/.claude/skills/md-snapshot
```

裝好後重開 Claude Code session，說「快照全md」就會觸發。

## 觸發詞

「快照全md」

## 個人設定

`~/.config/md-snapshot/env`（不進版控，只在你機器上）：

```bash
SNAPSHOT_DIR="~/CLAUDE-snapshots"
NAME_PREFIX="CLAUDE"
```

沒有這個檔案時用上面的通用預設值。

## 安全鐵則

- 一定用 `cp`（複製），絕不用 `mv`（搬移）——正本必須留在原位，否則 Claude Code 讀不到全域設定。
- 快照資料夾不放進 `~/.claude/` 裡面，備份跟正本分開放。
- 同一天已有快照時，先問要覆寫還是加流水號，不直接覆寫。

## License

MIT
