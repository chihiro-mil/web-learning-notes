# ブランチ
Gitの履歴を枝分かれさせて開発を進めるための機能。main(mastar)ブランチから枝分かれさせて作業。
同時に複数人で作業する時やテスト環境と本番環境で異なるバージョンを動かす時など

# マージ
ブランチで作成していた内容をmainブランチに統合すること

# ブランチ作成手順
1. ブランチ（update-sample）を作成
```bash
git branch update-sample
```

2. mainブランチから作成したブランチ（update-sample）に操作対象を切り替える
```bash
git switch update-sample
```

※作成したブランチ一覧と現在使用中のブランチの確認方法
```bash
git branch
```
現在使用中のブランチには（*）が付く
