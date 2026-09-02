# Q1 他社の商品、サービスに関する教育を行うにあたって、知財上気を付ける点を整理しようとしています。国際・国内規格、業界団体規格、特許・学術論文、商品・サービス提供者の知財に分けて、注意するとよい点を整理してください。なお、商品・サービス提供者と業務提携している場合には、文書または口頭での確認の際に、留意するとよいことがあれば、１６項目お示しください。
A1 by chatgpt

はい。これは教育そのものより、**「第三者の知財を教材・デモ・演習・録画・配布資料にどこまで利用できるか」**を管理する問題として整理するとよいです。

まず大原則は次のとおりです。

> **「教育目的だから自由に使える」わけではありません。**
> 他社の商品・サービスを題材にする場合、著作権、商標、特許、営業秘密、契約上の利用制限、ソフトウェア／クラウドのライセンス条件を、それぞれ別に確認する必要があります。

文化庁も著作権教育資料を提供していますが、利用条件は個別に示されており、「教育」という目的だけで一般的な自由利用を認めるものではありません。([文化庁][1])

また、営業秘密については「有用性・秘密管理性・非公知性」が保護の重要な要件であり、提携先から受け取った未公開資料を教育に転用する場合は特に注意が必要です。経済産業省の営業秘密管理指針は2025年3月に改訂されています。([経済産業省][2])

---

# 1. 全体像：5種類の権利・制約を分離する

同じ「他社製品の教育」でも、例えば次のように権利が重なります。

| 対象           | 主な確認対象          |
| ------------ | --------------- |
| 製品名・サービス名    | 商標・ブランドガイドライン   |
| ロゴ           | 商標＋著作権等         |
| 画面のスクリーンショット | 著作権・契約・利用規約     |
| マニュアル        | 著作権             |
| 動画・Webinar   | 著作権・出演者等の権利     |
| API・SDK      | ライセンス・契約        |
| ソフトウェア       | EULA、OSSライセンス   |
| 製品の仕組み       | 特許・営業秘密         |
| ベンチマーク結果     | 契約・表示方法・競争法上の問題 |
| 未公開ロードマップ    | NDA・営業秘密        |
| 実機デモ         | 購入・利用契約条件       |
| 録画した教育       | 二次利用許諾の範囲       |

つまり、

```text
他社の商品・サービス
        │
        ├─ 著作権
        ├─ 商標
        ├─ 特許
        ├─ 営業秘密・ノウハウ
        └─ 契約・ライセンス
```

を**一括して「知財」と処理しない**ことが重要です。

---

# 2. 国際・国内規格から見る注意点

規格には「この場合は必ず許諾を取る」という万能な条文があるわけではありません。しかし、教育プロセスを管理する枠組みとして有用です。

## ① ISO 9001系：教育プロセスを管理する

考え方は、

```text
教育目的
 ↓
教材選定
 ↓
第三者コンテンツ確認
 ↓
利用許諾確認
 ↓
教材承認
 ↓
教育実施
 ↓
録画・再利用管理
```

です。

特に、**誰が教材を承認したか、どの版を使用したか、いつ許諾が切れるか**を記録するとよいでしょう。

---

## ② ISO/IEC 27001系：情報資産として管理する

提携先から受け取った資料について、

```text
公開情報
社内限定情報
提携先秘密情報
営業秘密
```

を区別します。

経済産業省も、営業秘密として保護を受けるための管理の重要性を示しており、秘密情報について契約書等の参考例も提供しています。([経済産業省][2])

教育資料に、

> 「Partner Confidential」

と書かれたスライドが1枚でも混入すれば、教育対象者を広げた場合に問題になる可能性があります。

---

## ③ ISO 10015系：教育・能力開発プロセス

教育の必要性だけでなく、

* 教材は適切か
* 教材の出所は明確か
* 教育対象者は適切か
* 教育記録をどう管理するか

を管理対象にします。

私はここに、

> **Third-Party IP Check**

という工程を追加することを勧めます。

---

## ④ 国内法との対応

日本では最低限、次を分けて確認します。

| 法律等     | 教育での典型的問題        |
| ------- | ---------------- |
| 著作権法    | マニュアル、画面、図、動画、文章 |
| 商標法     | 商品名、ロゴ、認定制度名     |
| 特許法     | 実施、製造、使用、演習      |
| 不正競争防止法 | 営業秘密、限定提供データ、混同  |
| 民法・契約   | NDA、提携契約、利用許諾    |
| 個人情報保護法 | デモ画面やログに個人情報     |

WIPOもIP教育において、著作権、商標、特許、意匠、不正競争等を別領域として扱っています。([WIPO][3])

---

# 3. 業界団体規格・ガイドラインで注意する点

業界によっては、法律よりさらに細かいルールがあります。

例えば、

### ソフトウェア業界

* OSSライセンス
* SDK利用規約
* Developer Agreement
* Certification Program Agreement

### 自動車業界

* AUTOSAR等の会員・ライセンス条件
* JASPAR等の知財・成果物の利用条件
* 各OEM・Tier 1とのNDA
* 規格書・仕様書の複製条件

### IT・クラウド

* Microsoft等のProduct Terms
* AWS等の利用規約
* API Terms
* Training Partner Agreement

### 半導体

* データシートの著作権
* NDA下のリファレンスデザイン
* SDK／EDAツールのライセンス

ここで特に重要なのは、

> **規格を購入した＝規格本文を自由に教材へコピーできる**

ではないことです。

規格書自体にも著作権・利用条件があります。

したがって、

```text
規格を読んで説明する
```

と

```text
規格本文を大量に複製して配布する
```

は別問題です。

---

# 4. 特許・学術論文についての注意点

## 特許

教育で特許を紹介するだけなら、通常は特許権の「実施」とは異なる問題ですが、

* 特許図面をどう利用するか
* クレームを教材に転載するか
* 実際に特許発明を実演するか
* 特許技術を教材として再現・製造するか

を分けます。

特に、

> 「教育用だから特許発明を自由に実施できる」

とは一概に言えません。

---

## 学術論文

注意点は非常に実務的です。

### 可能なことが多い

* 自分の言葉で内容を要約する
* 適切に出典を示して紹介する
* 短い引用を要件に従って行う

### 注意が必要

* PDFを丸ごと受講者に配布
* 図表をそのままPowerPointに転載
* 論文の図を改変して自社教材として再利用
* 有料論文をLMSに無断アップロード

つまり、

```text
論文を読んで教える
```

ことと、

```text
論文そのものをコピーして配布する
```

ことは別です。

---

# 5. 商品・サービス提供者自身の知財

これは最も見落とされやすい部分です。

例えば、あるクラウドサービスについて教育する場合、

```text
サービス名
ロゴ
画面
操作動画
マニュアル
API仕様
SDK
認定資格
トレーニング教材
```

には、それぞれ異なる権利・契約が存在し得ます。

特に注意すべきは次です。

### 商品名

商品名を単なる事実として説明することと、**自社が公式代理店・認定講師であるかのように表示すること**は違います。

### ロゴ

「製品名を文章で書く」より、ロゴ使用の方がブランドガイドラインの制約を受けやすいことがあります。

### スクリーンショット

教育上便利ですが、

* UI変更
* 著作権
* 利用規約
* 個人情報
* 顧客データ
* 秘密情報

が混在します。

### 公式教材

「購入した公式教材」を講師が利用できても、

> コピーして受講者100人へ配布する権利

まで含まれるとは限りません。

---

# 6. 業務提携している場合に確認するとよい16項目

ここが実務上もっとも重要です。

**口頭確認だけでも確認事項を整理できますが、重要な権利については、後で認識違いにならないよう文書化することを強く勧めます。**

## 16項目のチェックリスト

| No. | 確認事項    | 確認すべき内容                           |
| --: | ------- | --------------------------------- |
|   1 | 教育目的    | 販売促進、技術教育、社内研修、学校教育のどれか           |
|   2 | 教育対象者   | 自社社員、顧客、一般公開、学生、提携先か              |
|   3 | 利用地域    | 日本限定か、海外受講者を含むか                   |
|   4 | 商品名使用   | 正式名称、略称、旧名称の使用可否                  |
|   5 | ロゴ使用    | スライド、Web、動画、修了証への使用可否             |
|   6 | 画面利用    | スクリーンショット・録画・デモ画面の使用可否            |
|   7 | マニュアル転載 | 何ページ・何図まで転載可能か                    |
|   8 | 公式教材    | 複製、翻訳、改変、配布が可能か                   |
|   9 | 動画録画    | 教育を録画して再配信できるか                    |
|  10 | LMS掲載   | Moodle等へ教材を保存し受講者が後日閲覧できるか        |
|  11 | 翻訳      | 日本語化、英語化、要約版作成の可否                 |
|  12 | 改変      | 図、画面、教材を自社向けに編集してよいか              |
|  13 | 技術情報    | 未公開情報・ロードマップを教育で話してよいか            |
|  14 | 成果物の帰属  | 自社が作成した教材・演習問題の権利は誰に帰属するか         |
|  15 | ブランド表示  | 「公式」「認定」「提携」の表示条件                 |
|  16 | 終了後の扱い  | 提携終了時に教材・動画・LMSデータを削除するか、継続利用できるか |

---

# 7. 16項目は4層にすると確認漏れが減ります

私は次の分類をお勧めします。

```text
┌───────────────────────────┐
│ ① Scope                  │
│ 目的・対象者・地域        │
│ 1,2,3                     │
├───────────────────────────┤
│ ② Content                │
│ 名称・ロゴ・画面・教材    │
│ 4～8                      │
├───────────────────────────┤
│ ③ Use                    │
│ 録画・LMS・翻訳・改変     │
│ 9～12                     │
├───────────────────────────┤
│ ④ Governance             │
│ 秘密・帰属・ブランド・終了│
│ 13～16                    │
└───────────────────────────┘
```

これは教育ごとにチェックしやすい構造です。

---

# 8. 口頭確認の場合に特に気を付けること

口頭で、

> 「使っていいですよ」

と言われた場合が一番危険です。

少なくとも次を確認します。

### 「誰が」許可したのか

担当営業が、

> 「使っていいです」

と言っても、その人に知財利用を許諾する権限があるとは限りません。

### 「何を」使ってよいのか

例えば、

> 「資料を使ってよい」

では曖昧です。

```text
PDF全体？
図だけ？
画面だけ？
改変可？
コピー可？
LMS掲載可？
録画可？
```

を確認します。

### 「誰に」使ってよいのか

```text
自社社員限定
顧客への研修可
一般公開可
YouTube公開可
```

では全く違います。

### 「いつまで」使えるのか

提携期間中だけなのか、終了後も教材を使えるのか。

---

# 9. 口頭確認後は「確認メール」で固定する

例えば実務では、次のような確認を残す方法があります。

> 本日の打合せにおける確認事項として、当社が貴社製品Xについて実施する研修において、以下の利用を認めていただいたと理解しています。
>
> 1. 製品名の使用
> 2. 指定されたロゴの使用
> 3. 指定されたスクリーンショットの使用
> 4. 受講者へのPDF配布
>
> 対象は当社顧客向け研修、日本国内、2027年3月31日までと理解しています。認識に相違があればご連絡ください。

このように、

> **口頭許諾 → 利用範囲を文書で確認**

にします。

ただし、**「返信がなければ当然に正式許諾された」と決めつけることは危険**です。契約や相手企業の権限規程により、書面や所定の承認が必要な場合があります。

---

# 10. 特にMoodleを使う場合

今進めておられるMoodleのようなLMSでは、知財問題が一段増えます。

なぜなら、

```text
講師PC
 ↓
一時的な投影
```

だけではなく、

```text
教材
 ↓
Moodle
 ↓
受講者がダウンロード
 ↓
後日閲覧
 ↓
バックアップ
 ↓
退職後もアカウントが残る可能性
```

となるからです。

したがって、教材ごとに少なくとも、

| 項目      | 設定例        |
| ------- | ---------- |
| 権利者     | ○○社        |
| 利用許諾    | 提携契約第○条    |
| 利用目的    | 技術教育のみ     |
| 対象者     | 契約顧客のみ     |
| ダウンロード  | 可／不可       |
| LMS掲載期限 | 2027-03-31 |
| 録画      | 不可         |
| 再配布     | 不可         |
| 改変      | 要事前承諾      |
| 提携終了時   | 削除         |

という**教材メタデータ**を付けるとよいです。

これは、経済産業省が示す秘密情報管理の考え方とも整合的です。秘密情報については、情報の性質に応じて管理方法を明確にすることが重要になります。([経済産業省][2])

---

# 11. 私なら「教育用第三者知財利用台帳」を作ります

1教材について、次のような表を作ります。

| ID     | 教材    | 権利者 | 権利種別   | 許諾根拠        | 利用範囲   | 期限         | 担当 |
| ------ | ----- | --- | ------ | ----------- | ------ | ---------- | -- |
| IP-001 | 製品X入門 | X社  | 著作権    | 契約          | 顧客研修   | 2027/3/31  | A  |
| IP-002 | Xロゴ   | X社  | 商標     | Brand Guide | スライドのみ | 継続         | B  |
| IP-003 | X画面   | X社  | 著作権等   | メール承諾       | LMS不可  | 2026/12/31 | A  |
| IP-004 | API資料 | X社  | 著作権・契約 | SDK規約       | 社内限定   | 契約期間       | C  |

これがあると、

> 「このスライド、来年度も使えますか？」

という質問に答えられます。

---

## 結論

他社商品・サービスの教育では、私は次の原則を勧めます。

> **① 法律上利用できるか**
> **② 契約上利用できるか**
> **③ 権利者のブランド・利用規約上利用できるか**
> **④ 教育対象者・媒体・地域・期間の範囲内か**
> **⑤ 録画・Moodle掲載など二次利用まで許可されているか**

という**5段階チェック**です。

特に業務提携している場合でも、

> **「提携している」＝「相手の知財を教育目的で自由に利用できる」**

ではありません。WIPOもIP教育を、著作権・商標・特許など複数の独立した権利領域として扱っています。([WIPO][3])

必要であれば次に、この16項目をそのまま使えるように、**「他社商品・サービス教育用 知財確認チェックシート」**として、Moodle教材・PowerPoint・動画・実機デモ・GitHub・OSSの欄まで含めた実務用テンプレートにできます。

[1]: https://www.bunka.go.jp/seisaku/chosakuken/seidokaisetsu/index.html?utm_source=chatgpt.com "著作権を学ぶ（教材・講習会） | 文化庁"
[2]: https://www.meti.go.jp/policy/economy/chizai/chiteki/trade-secret.html?utm_source=chatgpt.com "営業秘密～営業秘密を守り活用する～ （METI/経済産業省）"
[3]: https://www.wipo.int/en/web/wipo-academy/?utm_source=chatgpt.com "WIPO Academy"

# Q2 ISO, IEC, ITUの国際規格団体では、リエゾン関係を結び、全文を引用したり、一部の引用の仕方を定義していることがあります。しかし、AUTOSARのようにリエゾン関係を結ばない場合でも、WTO/TBT協定に違反しないことを主張するために国際規格との違いを記述する必要があります。AUTOSARが国際規格を引用または違いの説明を書くにはどのような方法がお勧めでしょうか。
A2

はい。ここはかなり重要な論点です。結論からいうと、**AUTOSARのような業界団体がISO/IEC/ITUと正式なリエゾンを結んでいない場合でも、国際規格との関係を「参照関係」と「差異分析」によって透明化しておく**のがよいと思います。

ただし、最初に一つ重要な整理があります。

> **WTO/TBT協定が直接AUTOSARに「ISO/IEC規格を引用せよ」と要求しているわけではありません。**

TBT協定の中心的な義務は、WTO加盟国の**technical regulations**について、関連する国際規格が存在する場合には、それを基礎として用いることです（第2.4条）。また、国際規格に適合したtechnical regulationには、原則として「不必要な貿易障害を作らない」という反証可能な推定があります（第2.5条）。([世界貿易機関][1])

したがってAUTOSARについては、

**「TBTに適合している」**

と直接主張するより、

**「AUTOSAR仕様は、関連する国際規格を調査し、適用可能な部分は参照・採用し、異なる部分については技術的理由を明示している」**

という**透明性・非差別性・国際整合性の証拠を残す**ことが重要だと思います。

---

# 1. AUTOSARには、実は既に「参照」の仕組みがある

これは非常に興味深いところです。

AUTOSARのFAQでは、AUTOSARは関連する標準に適合することを目指し、ISO、ASAM、GENIVIなどの標準化団体と連絡を取り、既存の解決策については、

> integrated, referenced or adopted

する、と説明しています。([AUTOSAR][2])

また、実際のAUTOSAR仕様には、

**6.2 Related standards and norms**

のような章があり、ISO、IEC、IEEE、IETF、ASAM等を列挙しています。例えばEthernet関連仕様では、ISO 13400、IEEE 802.1AS、ISO 14229、RFC 791、RFC 793等が参照されています。([AUTOSAR][3])

つまり、AUTOSARが正式リエゾンを持たないことと、

> **国際規格を参照できない**

ことは全く別です。

---

# 2. 私なら「5段階の関係」を定義します

AUTOSARの外部規格との関係を、単なるReferencesだけではなく、次の5段階に分類します。

| Level | 関係                      | AUTOSARでの扱い          |
| ----- | ----------------------- | -------------------- |
| 0     | 無関係                     | 対象外                  |
| 1     | Informative reference   | 参考として紹介              |
| 2     | Normative reference     | 準拠・利用を要求             |
| 3     | Adopted / aligned       | 国際規格を取り込んでAUTOSAR仕様化 |
| 4     | Modified / extended     | 国際規格を基礎として変更・拡張      |
| 5     | Alternative / different | 国際規格とは異なる方式を採用       |

これを仕様書に明示します。

例えば、

```text
External Standard Relationship

ISO 14229-1:2020

AUTOSAR status:
  [X] Informative
  [X] Partially adopted
  [ ] Normative
  [ ] Modified
  [ ] Alternative

Applied clauses:
  ISO 14229-1: Clause 5, 6, 7

Not applied:
  ISO 14229-1: Clause 8

Reason:
  AUTOSAR communication architecture requires
  a different service abstraction.
```

という形式です。

---

# 3. 特に重要なのが「差異表」です

私はこれをAUTOSARに標準的に導入することを提案します。

名称は例えば、

> **International Standard Alignment and Deviation Table**

とします。

日本語なら、

> **国際規格整合・差異表**

です。

例えば、

| ISO/IEC  | Clause | ISO/IEC要求 | AUTOSAR | 関係  | 理由                     |
| -------- | ------ | --------- | ------- | --- | ---------------------- |
| ISO XXXX | 5.1    | A         | A       | 同一  | —                      |
| ISO XXXX | 5.2    | B         | B'      | 変更  | AUTOSAR architecture   |
| ISO XXXX | 5.3    | C         | —       | 非採用 | Scope外                 |
| ISO XXXX | 5.4    | D         | D+      | 拡張  | Automotive requirement |

とします。

これが非常に強い資料になります。

---

# 4. 「違いを書いておく」ことにはWTO/TBT上の意味がある

TBT第2.4条では、国際規格を「as a basis」として使うことが要求されています。

しかしWTOの判例上、

> 「国際規格と完全に同一でなければならない」

という意味ではありません。

EC–Sardines等の解釈では、「as a basis」は国際規格を**principal constituent / fundamental principle**として用いることを意味し、必ずしも完全一致を要求するものではないと整理されています。([世界貿易機関][4])

したがって、

```text
International Standard
       │
       ├── adopted
       │
       ├── modified
       │
       ├── extended
       │
       └── not appropriate
              ↓
          technical reason
```

という記録を残すことが重要になります。

---

# 5. 「違う理由」を4種類に分類すると強い

単に、

> AUTOSAR is different from ISO XXXX.

だけでは弱いです。

私は理由を最低でも次の4分類にします。

### A. Scope difference

対象範囲が違う。

```text
ISO：一般産業
AUTOSAR：車載組込み
```

### B. Technical difference

技術的要求が違う。

例えば、

```text
ISO方式
      ↓
AUTOSAR architecture
      ↓
additional interface requirement
```

### C. Safety / Security difference

自動車の安全・セキュリティ要求から異なる。

AUTOSAR ClassicはハードリアルタイムやSafety Constraintsを対象とし、Adaptiveは高性能ECUやfail-operational用途を対象としているため、この種の差異説明は特に重要です。([AUTOSAR][5])

### D. Compatibility / Legacy

既存車両・既存ECUとの互換性。

これは自動車業界では非常に重要です。

---

# 6. 「国際規格を使わない理由」も記録する

ここがTBTとの関係では特に重要です。

WTO TBT 2.4には、国際規格が存在しても、それが legitimate objective を達成するために ineffective / inappropriate なら例外が認められています。([世界貿易機関][1])

したがってAUTOSARの仕様作成時に、

```text
International Standard Review

Relevant ISO/IEC standard:
    ISO XXXX

Applicable?
    Yes / No / Partially

If No or Partially:

Reason:
    [ ] Scope mismatch
    [ ] Technical incompatibility
    [ ] Safety requirement
    [ ] Security requirement
    [ ] Performance requirement
    [ ] Legacy compatibility
    [ ] Automotive-specific requirement
    [ ] Other
```

という欄を設けるのが非常に良いと思います。

---

# 7. さらに一歩進めて「International Standard Matrix」を作る

AUTOSAR全体について、

| 分野          | ISO | IEC | ITU | IEEE | IETF | ASAM | AUTOSAR |
| ----------- | --- | --- | --- | ---- | ---- | ---- | ------- |
| OS          | ○   |     |     |      |      |      | ○       |
| Network     | ○   | ○   |     | ○    | ○    | ○    | ○       |
| Diagnostics | ○   |     |     |      |      | ○    | ○       |
| Safety      | ○   | ○   |     |      |      |      | ○       |
| Security    | ○   | ○   |     |      | IETF |      | ○       |
| Modeling    |     |     |     |      |      |      | ○       |

という**External Standards Matrix**を作ります。

そして各セルについて、

```text
A = Adopted
R = Referenced
M = Modified
E = Extended
D = Different
N = Not applicable
```

とします。

これはAUTOSARのような巨大な仕様群ではかなり有効だと思います。

---

# 8. 「全文引用」は極力避け、「識別可能な参照」にする

ここは知財上も重要です。

ISO自身も、ISO/IEC規格は著作権で保護されており、無断で全文・一部をコピー、配布することはできないと明記しています。([ISO][6])

したがってAUTOSARが、

> ISO 26262-6:2018, Clause 7

と**参照する**ことと、

> ISO 26262-6 Clause 7の全文をAUTOSAR仕様に転載する

ことは全く違います。

私は原則として、

### 推奨

```text
ISO 26262-6:2018, Clause 7
```

または

```text
ISO 26262-6:2018, 7.4
```

＋

```text
AUTOSAR interpretation:
...
```

とします。

---

# 9. 用語についても同じ方式が使える

例えばISOの用語定義を使う場合、

```text
Term: Safety Goal

Source:
ISO 26262-1:2018, 3.139
```

として、

> AUTOSAR uses the term consistently with ISO 26262-1.

とする。

ISO自身も外部文書の用語定義について、外部文書を参照する方法と、必要な場合に出典を明示して定義を再掲する方法を区別しています。また、外部資料を再利用する場合には著作権上の確認が必要としています。([ISO][7])

---

# 10. ただし「ISOとのリエゾン」と「国際規格への参照」は別問題

ここは研究論文を書く場合にも重要です。

```text
AUTOSAR
   │
   ├── Liaison ───── ISO
   │
   └── Reference ─── ISO 26262
```

この二つは違います。

**Liaison**

→ 組織間の正式な協力・情報交換・標準開発プロセス上の関係。

**Reference**

→ 文書の技術的内容について別の規格を参照する関係。

AUTOSAR自身もISO等と「regular contact」を持ち、既存解決策をintegrated/referenced/adoptedするという説明をしています。([AUTOSAR][2])

したがって、

> 「リエゾンがないからISOを参照できない」

という考え方は採らない方がよいです。

---

# 11. WTO/TBTを意識するなら「三つの文書」を残す

AUTOSARの標準化プロセスを改善するなら、私は次の3種類を提案します。

### ① External Standards Register

```text
ISO 26262
ISO 21434
ISO 14229
ISO 13400
IEC 61508
IEEE 802.1
IETF RFC...
ASAM...
```

を一覧化。

### ② Alignment Table

```text
International Standard
       ↓
AUTOSAR Requirement
       ↓
Identical / Modified / Extended
```

を記録。

### ③ Deviation Justification

異なる場合、

```text
Difference
   ↓
Technical reason
   ↓
Safety/security/performance reason
   ↓
Trade impact consideration
```

を記録します。

この3点セットです。

---

# 12. さらに「6原則」を満たすことをチェックする

ISO/IEC Directives自身も、WTO TBTにおける国際規格の特別な位置づけを明記しています。

WTO TBTの国際標準化原則を意識して、

1. Transparency
2. Openness
3. Impartiality and consensus
4. Effectiveness and relevance
5. Coherence
6. Development dimension

という観点からAUTOSARの標準化プロセスを自己評価する方法も考えられます。

特に、

> **「なぜISO/IECと違うのか」**

を公開仕様に残すことは、TransparencyとCoherenceの観点から非常に意味があります。

---

# 13. 私ならAUTOSAR仕様書に次の章を追加します

例えば、

```text
Clause 2  Normative References

Clause 3  Terms and Definitions

Clause 4  Requirements

...

Annex X
International Standards Alignment

X.1 Scope

X.2 Referenced International Standards

X.3 Alignment Classification

X.4 Deviations from International Standards

X.5 Technical Justification

X.6 Safety and Security Considerations

X.7 Compatibility Considerations
```

とします。

特に**Annex X**がポイントです。

---

# 14. 具体例

例えば、

```text
ISO 14229
       │
       │ Diagnostic services
       ↓
AUTOSAR Diagnostic Communication Manager
       │
       ├── adopted
       ├── extended
       └── abstracted
```

なら、

| ISO 14229             | AUTOSAR     | 状態            | 説明                           |
| --------------------- | ----------- | ------------- | ---------------------------- |
| Diagnostic Service    | DCM service | Adopted       | 基本サービスを採用                    |
| Session management    | DCM         | Extended      | AUTOSAR architectureに適合      |
| Transport             | PduR/CanTp  | Split         | AUTOSAR layered architecture |
| ECU-specific behavior | —           | Not specified | OEM/ECU依存                    |

と書く。

これなら、

> 「AUTOSARはISO 14229を無視して独自規格を作った」

ではなく、

> **「ISO 14229を基礎として、AUTOSARのアーキテクチャ上必要な部分を分割・拡張した」**

という説明ができます。

---

# 15. ただし「WTO/TBT違反をしない」という表現には注意

ここはかなり重要です。

AUTOSAR自身が民間の業界団体として仕様を作っている場合、**TBT協定上の義務主体であるWTO加盟国のtechnical regulationと同じ法的評価をそのまま受けるわけではありません**。

TBT Annex 1ではtechnical regulationはmandatoryなproduct requirements等として定義されています。一方、standardは基本的にvoluntaryな文書として定義されています。([世界貿易機関][1])

したがって、

> 「AUTOSARがISOを引用しなかったからTBT違反」

という論理には直ちにはなりません。

むしろ問題になるのは、

```text
AUTOSAR specification
       ↓
OEM / Government regulation
       ↓
Mandatory requirement
       ↓
International trade
```

のように、**AUTOSAR仕様が事実上または法的にmandatory technical regulationの基礎になった場合**です。

ここではじめてTBT 2.4との関係が非常に重要になります。

---

# 16. したがって、私なら「TBT Compliance」ではなくこう表現します

AUTOSAR文書では、

> **International Standards Alignment**

という表現を使います。

例えば、

> **AUTOSAR has reviewed relevant international standards and, where appropriate, uses them as a basis for the development of its specifications. Where an AUTOSAR specification differs from a relevant international standard, the applicable scope, technical differences and rationale are identified in this document.**

という基本方針です。

そして差異表を、

> **Deviation from International Standards**

として公開する。

これなら「WTO/TBTに適合している」という法的断定を避けながら、**TBTが重視する国際規格との整合性・透明性を実証する資料**になります。

---

## 最も重要なポイント

私は、AUTOSARのような業界標準には、ISO/IEC型の**「引用ルール」そのものを移植するより、「国際規格との関係を機械的に追跡できる仕組み」を作る**ことをお勧めします。

最終的には、

```text
                 International Standards
                    ISO / IEC / ITU
                          │
              ┌───────────┴───────────┐
              ↓                       ↓
        Normative Reference      Informative Reference
              │
              ↓
        AUTOSAR Requirement
              │
       ┌──────┼──────┬──────┐
       ↓      ↓      ↓      ↓
    Adopted Modified Extended Different
                         │
                         ↓
               Deviation Justification
                         │
                         ↓
             Safety / Security / Technical
             / Compatibility / Scope
```

という**「International Standard Traceability」**を作るのが、最も説得力のある方法だと思います。

そしてAUTOSAR自身のR24-11 Glossaryを見ると、ISO/IEC、IEEE、ASAM等を実際にReferencesとして列挙する仕組みは既に存在します。([AUTOSAR][8])

この考え方は、以前お話しされていた**「AUTOSARとISO/IECの関係を整理する標準化提案」**にもかなり発展させやすいテーマです。特に、**「AUTOSAR International Standards Alignment & Deviation Annex」**を提案仕様として作ると、標準化プロセス、知財、WTO/TBT、Safety/Securityを一つの研究テーマにまとめられます。

[1]: https://www.wto.org/english/tratop_e/tbt_e/tbtagr.htm?utm_source=chatgpt.com "WTO | Agreement on Technical Barriers to Trade"
[2]: https://www.autosar.org/faq?utm_source=chatgpt.com "AUTOSAR FAQs | Frequently Asked Questions"
[3]: https://www.autosar.org/fileadmin/standards/R20-11/CP/AUTOSAR_SRS_Ethernet.pdf?utm_source=chatgpt.com "Requirements on Ethernet Support in AUTOSAR"
[4]: https://www.wto.org/english/res_e/publications_e/ai17_e/tbt_art2_jur.pdf?utm_source=chatgpt.com "Microsoft Word - tbt_art2_jur.docx"
[5]: https://www.autosar.org/standards?utm_source=chatgpt.com "Standards of AUTOSAR"
[6]: https://www.iso.org/copyright.html?utm_source=chatgpt.com "ISO - Copyright"
[7]: https://www.iso.org/ISO-house-style.html?utm_source=chatgpt.com "ISO - ISO House Style"
[8]: https://www.autosar.org/fileadmin/standards/R24-11/FO/AUTOSAR_FO_TR_Glossary.pdf?utm_source=chatgpt.com "Glossary"

# Q3 AUTOSARのReferenceでは、すでに廃止されている国際規格や、タイトルが変わった国際規格が、LatexでReferenceを生成しているためか数十以上誤記が存在しています。自動車分野のISOの委員の半分以上の企業がAUTOSARに加入しています。ISO自体もさまざまな誤記が残存しています。ISO OSEK OSでは明らかな誤植などが修正されずに訂正が発行されていません。また、AUTOSARの拡張部分をISOに反映させようとしていません。両者の健全な技術発展を実現するのに何か名案はありませんか。
A3

はい。むしろ、そこに**AUTOSARとISOの双方を健全化するための、かなり面白い標準化テーマ**があると思います。

ご指摘の問題を単純に「AUTOSARのReferenceの誤記を直す」と捉えるより、

> **「自動車ソフトウェア標準間の相互保守（cross-standard maintenance）を制度化する」**

と捉えるのが名案だと思います。

AUTOSAR自身も、ISO等の標準化団体とregular contactを持ち、既存の解決策について *integrated, referenced or adopted* する方針を明記しています。また、重複がある場合にはcompatibilityとresponsibilityの明確化を行うとしています。([AUTOSAR][1])
ところが、**「参照した後に相手規格が改訂・廃止された」「タイトルが変わった」「AUTOSAR側で拡張した」場合の相互保守プロセス**は、もっと明示的に制度化できる余地があります。

## 1. 私なら「Automotive Standards Synchronization Initiative」を作ります

仮称ですが、

> **ASSI — Automotive Standards Synchronization Initiative**
> 自動車標準相互整合・保守イニシアティブ

です。

対象を、

* ISO
* IEC
* ITU-T
* AUTOSAR
* ASAM
* COVESA
* SAE
* JASPAR
* その他自動車業界団体

まで広げます。

目的は「どこが正しいかを決める」ことではありません。

**標準Aと標準Bが互いに参照しているなら、その関係を機械的に追跡し、変更を相互に通知する仕組みを作る**ことです。

---

# 2. 一番重要なのは「Referenceを単なる文字列にしない」こと

現在の問題は、例えばLaTeXのReferenceが、

```text
ISO 12345:2018
Title of xxx
```

という**文字列**になっていることだと思います。

これを、

```text
StandardReference {
    organization = ISO
    number       = 12345
    edition      = 2018
    title        = ...
    status       = published
    referencedBy = AUTOSAR_xxx
}
```

という**構造化データ**にします。

すると、

```text
AUTOSAR Reference
       │
       ↓
ISO identifier
       │
       ↓
ISO database
       │
       ├── current edition
       ├── withdrawn
       ├── revised
       ├── corrigendum
       └── title changed
```

を自動チェックできます。

これはかなり効果があります。

---

# 3. 「Reference Linter」を作る

そしてAUTOSAR Release生成時に、

> **Standard Reference Linter**

を走らせます。

例えば、

```text
$ autosar-reference-lint R26-11
```

として、

```text
ERROR:
ISO 15765-2:2004
Status: WITHDRAWN
Replaced by: ISO 15765-2:2024

WARNING:
ISO 13400-2
Title differs from current ISO title

WARNING:
ISO XXXXX:2018
AUTOSAR citation does not match official identifier

ERROR:
IEC XXXXX
Reference edition does not exist
```

のようにします。

これなら**LaTeXを修正する前にデータを修正する**ことになります。

---

# 4. さらに重要なのが「Referenceのライフサイクル」

Referenceには少なくとも、

```text
NEW
  ↓
CURRENT
  ↓
REVISED
  ↓
SUPERSEDED
  ↓
WITHDRAWN
```

という状態を持たせます。

ただし、ここで注意が必要です。

**AUTOSARが参照しているISO規格が新しくなったからといって、AUTOSAR Referenceを自動的に新しい版へ変更してはいけません。**

例えば、

```text
AUTOSAR R24-11
     │
     └── ISO XXXX:2018
```

についてISO XXXX:2026が出た場合、

```text
AUTOSAR R24-11
     │
     └── ISO XXXX:2018
```

は歴史的に正しい可能性があります。

したがって、

> **Historical Reference**

と

> **Current Reference**

を区別する必要があります。

これは非常に重要です。

---

# 5. 「Reference Snapshot」を残す

私はさらに、

> **Reference Snapshot**

をAUTOSAR Releaseごとに保存します。

例えば、

```text
AUTOSAR R24-11
  Reference Snapshot
      ISO XXXX:2018
      ISO YYYY:2019
      IEC ZZZZ:2020
```

を固定。

そして現在のISOデータベースと比較して、

```text
Historical correctness = OK
Current validity       = superseded
```

と表示します。

こうすれば、

> 「古い規格を参照している＝誤り」

とはなりません。

**「そのリリース時点では正しかった」**

ことを保存できます。

---

# 6. そしてご指摘の本丸「AUTOSAR → ISO」を制度化する

ここが私は一番面白いと思います。

現在、

```text
ISO
 ↓
AUTOSAR
```

という流れはかなりあります。

しかし、

```text
AUTOSAR
 ↓
ISO
```

という**技術的フィードバックループ**をもっと強くする。

例えば、

```text
ISO 17356 / OSEK
        ↓
AUTOSAR
        ↓
Automotive requirements
        ↓
AUTOSAR extension
        ↓
ISO feedback package
        ↓
ISO working group
        ↓
ISO revision
```

です。

つまり、

> **AUTOSARをISO規格の「利用者」に留めず、ISO規格を進化させる「実装・実証フィールド」にする**

という考え方です。

---

# 7. 「AUTOSAR Extension Report」をISOへ渡す

AUTOSAR側でISOとの違いが発生したら、その差分を蓄積します。

例えば、

| ISO      | AUTOSAR    | 差異          | 理由         | 実績   |
| -------- | ---------- | ----------- | ---------- | ---- |
| ISO OSEK | AUTOSAR OS | Extension A | Safety     | 実車多数 |
| ISO XXXX | AUTOSAR    | Extension B | Security   | 実装済  |
| ISO YYYY | AUTOSAR    | Extension C | Multi-core | 実装済  |

そして一定期間ごとに、

> **AUTOSAR Extension Report to ISO**

を作る。

これは単なる「意見書」ではなく、

```text
ISO requirement
    ↓
AUTOSAR implementation
    ↓
problem identified
    ↓
extension introduced
    ↓
field experience
    ↓
proposed ISO change
```

という**Evidence-based standardization**にします。

---

# 8. ISO側にも「AUTOSAR Liaison」ではなく「Technical Feedback Channel」を設ける

ここはリエゾン制度にこだわらない方がよいと思います。

例えば、

> **Automotive Software Standards Feedback Channel**

を設ける。

ISO TC/SCの正式なリエゾン関係とは別に、

* AUTOSAR
* ASAM
* SAE
* OEM
* Tier 1
* ECU/半導体企業

から、

> 「ISO規格のこの記述は実装上こう解釈されている」

という技術フィードバックを受け取る。

そしてISO委員会が、

```text
Accepted
Rejected
Needs further study
Already addressed
Out of scope
```

と回答する。

**回答しないこと自体も記録する**のが重要です。

---

# 9. OSEK OSの問題には「Technical Errata Register」が効く

ご指摘の、

> ISO OSEK OSで明らかな誤植があるのにCorrigendumが発行されない

という問題には、私は**Technical Errata Register**を導入するのが良いと思います。

例えば、

| ID      | 規格       | Clause | 問題                 | 種類        | 影響     | 状態           |
| ------- | -------- | ------ | ------------------ | --------- | ------ | ------------ |
| ERR-001 | ISO XXXX | 5.2    | typo               | Editorial | Low    | Confirmed    |
| ERR-002 | ISO XXXX | 6.4    | contradictory      | Technical | High   | Under review |
| ERR-003 | ISO XXXX | 7.1    | ambiguous          | Technical | High   | Accepted     |
| ERR-004 | ISO XXXX | 8.2    | obsolete reference | Editorial | Medium | Corrected    |

とする。

ISOの現行Directivesでは、誤りや曖昧さが誤った・安全でない適用につながる場合、Technical Corrigendum等による訂正の仕組みがあります。一方、単なる「古くなった情報」はCorrectionの対象ではなく、revision等で扱うという区別も明記されています。

したがって、

> **誤植・誤記・技術的誤り・陳腐化**

を分離して管理することが重要です。

---

# 10. 「誤植」と「仕様変更」を混ぜない

これも重要です。

例えば、

### Class A — Editorial Error

```text
Typo
Wrong title
Wrong reference number
Page number error
LaTeX生成ミス
```

### Class B — Technical Errata

```text
Contradiction
Wrong formula
Wrong interface definition
Ambiguous requirement
```

### Class C — Obsolescence

```text
Referenced standard withdrawn
Technology obsolete
Old terminology
```

### Class D — Technical Evolution

```text
AUTOSAR extension
New automotive requirement
New safety requirement
New security requirement
```

に分類する。

そうすると、

```text
A → Corrigendum
B → Corrigendum / Amendment
C → Revision
D → New Work Item / Revision
```

という流れが作れます。

---

# 11. 「ISOとAUTOSARのどちらが正しいか」を議論しない

これも大事だと思います。

例えば、

> AUTOSARがISOより進んでいる

とか、

> ISOが正式なのでAUTOSARが従うべき

という構図にすると、組織間対立になります。

代わりに、

> **State of the Art Synchronization**

という考え方にします。

```text
       ISO
        ↕
   synchronization
        ↕
     AUTOSAR
        ↕
      ASAM
        ↕
 Automotive Industry
```

つまり、

> **「どちらが上か」ではなく、「技術知識をどの標準に、いつ、どのように反映するか」**

を問題にします。

---

# 12. WTO/TBTとの関係でも、この方式はかなり強い

前の質問ともつながります。

WTO/TBT協定では、技術規則について関連する国際規格を基礎として使うこと、国際規格と異なる場合には一定の条件でその理由を説明することが重要です。さらにAnnex 3のCode of Good Practiceでは、非政府の標準化団体も対象となり得て、国際規格を基礎として使うことや貿易障壁を作らないことなどが定められています。([世界貿易機関][2])

また、TBT Committeeが示す国際標準化の6原則は、

1. Transparency
2. Openness
3. Impartiality and consensus
4. Effectiveness and relevance
5. Coherence
6. Development dimension

です。([ISO][3])

今回の提案は、この中でも特に、

> **Transparency + Coherence + Effectiveness and relevance**

を強化します。

---

# 13. 実は「ISO ↔ AUTOSAR Digital Thread」にできます

ここまで進めると、単なる標準化手続ではなく、**デジタル・スレッド**になります。

```text
ISO 17356
    │
    │ reference
    ↓
AUTOSAR OS Requirement
    │
    ↓
AUTOSAR Specification
    │
    ↓
Implementation
    │
    ↓
Test
    │
    ↓
Field Experience
    │
    ↓
AUTOSAR Change Request
    │
    ↓
ISO Feedback
    │
    ↓
ISO Revision
```

これを各RequirementにIDを持たせて追跡します。

例えば、

```text
ISO-17356-OS-REQ-xxx
        ↓
AUTOSAR-OS-REQ-yyy
        ↓
AUTOSAR-OS-SPEC-zzz
        ↓
TEST-zzz
```

です。

これは、ユーザーが以前から取り組まれている**UML → Requirement → Software → Test → Safety**という流れとも非常に相性がいいです。

---

# 14. さらにGenerative AIを使うと面白い

ここは今の時代ならぜひ入れたいところです。

例えばAIに、

```text
ISO references
AUTOSAR references
ISO current catalogue
AUTOSAR current release
```

を与えて、

```text
Reference Check
    ↓
Title mismatch
Edition mismatch
Withdrawn
Superseded
Potential typo
Potential semantic difference
```

を自動検出する。

ただしAIには**修正権限を与えない**。

```text
AI
 ↓
Candidate finding
 ↓
Human expert
 ↓
Confirmed
 ↓
AUTOSAR change request
 ↓
ISO committee
```

とします。

これは、以前話していた**Human / AI / ComputerのSoftware Process分離**そのものです。

---

# 15. 私なら最終的に「二つのGit」を作ります

かなり大胆ですが、これが一番面白いと思います。

### Git A：AUTOSAR Specification

```text
AUTOSAR repository
```

### Git B：International Standards Knowledge Graph

```text
standard-id
edition
title
status
replacement
references
clauses
AUTOSAR mappings
errata
deviations
```

そしてCIで、

```text
AUTOSAR Build
      ↓
Reference Linter
      ↓
Standards Knowledge Graph
      ↓
ERROR / WARNING
```

とします。

---

# 16. そして「Standards Change Request」を共通化する

例えば、

```text
SCR-2026-001

Source:
ISO 12345:2018

AUTOSAR:
R26-11 / XXX

Issue:
Referenced ISO title is obsolete.

Type:
Reference Error

Action:
Update reference metadata.

Impact:
No technical impact.
```

あるいは、

```text
SCR-2026-002

Source:
ISO OSEK OS

Issue:
Ambiguous requirement

AUTOSAR:
AUTOSAR OS has implemented an unambiguous interpretation.

Evidence:
10+ years implementation experience.

Proposal:
Clarify ISO text.

Type:
Technical Erratum / Revision Candidate
```

とする。

この**SCR（Standards Change Request）をISO側にも渡せる形式**にしてしまう。

---

# 17. これなら「AUTOSARがISOを直す」という構図にならない

ここがポイントです。

提案の主語を、

> AUTOSAR should correct ISO.

ではなく、

> **Automotive software standardization should establish a bidirectional maintenance mechanism between international and industry standards.**

とします。

これならISO側にも受け入れやすい。

ISOには既に、規格のmaintenance、correction、amendment、revision、maintenance agencyという仕組みがあります。

AUTOSARにも継続的に仕様を改善するReleaseの考え方があります。実際、AUTOSARはR20-11等について新機能と改善を含む同期されたReleaseとして説明しています。([AUTOSAR][4])

つまり、

> **両者の既存プロセスを壊さず、「境界部分」だけを同期する**

のです。

---

# 18. 私なら研究・標準化提案のタイトルをこうします

かなり良いテーマになると思います。

### 第一候補

> **自動車ソフトウェア標準における国際規格と業界規格の相互保守方式**

英語なら、

> **A Bidirectional Maintenance Framework between International and Industry Standards for Automotive Software**

### もう少し技術寄り

> **Automotive Standards Digital Thread: Traceability between ISO and AUTOSAR**

### AIまで含めるなら

> **AI-Assisted Cross-Standard Consistency Management for Automotive Software Standards**

---

## 私が特に「名案」だと思う部分

最終的には、**ISOとAUTOSARのどちらかを他方に従わせるのではなく、「標準間の差分そのものを第一級の管理対象にする」**ことです。

```text
                 ┌──────────────┐
                 │ ISO / IEC    │
                 └──────┬───────┘
                        ↕
              Standard Synchronization
                        ↕
                 ┌──────┴───────┐
                 │   AUTOSAR    │
                 └──────┬───────┘
                        ↕
                 ASAM / SAE / etc.
                        ↕
                 Automotive Industry
```

そして各関係を、

**Reference → Version → Difference → Reason → Implementation → Evidence → Feedback → Revision**

として追跡する。

これなら、今回ご指摘の

* AUTOSARのReference誤記
* 廃止規格の参照
* タイトル変更
* LaTeX生成上の問題
* ISO側の誤植
* Corrigendum未発行
* AUTOSAR拡張がISOへ戻らない
* ISOとAUTOSARの技術的乖離
* WTO/TBT上の国際規格との整合性

を**一つの仕組みで扱えます**。

しかもWTO/TBTのAnnex 3が求める方向性とも、「国際規格を基礎にする」「透明性を確保する」「国際標準化に参加する」という点で親和性があります。([世界貿易機関][2])

特に、**「AUTOSAR Reference Linter + International Standards Knowledge Graph + ISO Feedback Package」**の3点セットは、実装可能性が高く、単なる理念ではなく**PoCを作れる標準化提案**になると思います。

もし実際に提案書にするなら、次は **「AUTOSAR R24-11/R25-11のReferenceを実例として10～20件抽出し、①誤記、②廃止、③タイトル変更、④版違い、⑤AUTOSAR独自拡張、の5種類に分類した表」**を作ると、かなり説得力が出ます。そこからISOへの**Change Request様式まで含む8～10ページ程度の標準化提案書**に発展させられます。

[1]: https://www.autosar.org/faq/?utm_source=chatgpt.com "AUTOSAR FAQs | Frequently Asked Questions"
[2]: https://www.wto.org/english/tratop_e/tbt_e/tbtagr.htm?utm_source=chatgpt.com "WTO | Agreement on Technical Barriers to Trade"
[3]: https://www.iso.org/files/live/sites/isoorg/files/publications/en/ISO_Public-Policy-Toolkit.pdf?utm_source=chatgpt.com "9.3 How are International Standards developed?"
[4]: https://www.autosar.org/news-events/detail/autosar-release-r20-11-published?utm_source=chatgpt.com "News & Events AUTOSAR"

# Q4 「AUTOSAR R24-11/R25-11のReferenceを実例として10～20件抽出し、①誤記、②廃止、③タイトル変更、④版違い、⑤AUTOSAR独自拡張、の5種類に分類した表」を作 ってください。
A4

はい。かなり面白い実例が取れます。
今回は **AUTOSAR公式のR24-11/R25-11文書に実際に記載されているReference** と、ISO/IEC/IEEEの公式データベースを突き合わせて、**「Referenceそのものの問題」と「AUTOSARによる拡張」を分ける**形にしました。

なお、ここでいう「誤記」は、単なる「古い」ではなく、**規格番号・組織名・タイトルなどの記載が実際の標準と一致しないもの**に限定しています。

### AUTOSAR R24-11 / R25-11 Referenceのサンプル調査

| No. | AUTOSAR Release | AUTOSAR文書                     | Reference記載                                                                                                                   | 分類               | 現在確認できる状態・問題                                                                                                       | コメント                                                                           |
| --: | --------------- | ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
|   1 | R24-11          | FO/TR Glossary                | **ISO/IEC 9646-1:1994**                                                                                                       | ②廃止・③タイトル/表記     | 現在もPublished、1994 edition。ただし旧1991版はWithdrawn。                                                                     | **問題とは断定しにくい**。Referenceとしては古いが現行版を指している。                                      |
|   2 | R24-11          | FO/TR Glossary                | **ISO 17356-3: Road vehicles – Open interface for embedded automotive applications – Part 3: OSEK/VDX Operating System (OS)** | ⑤AUTOSAR独自拡張との関係 | ISO 17356-3:2005は2026年にも確認され、現行版。                                                                                  | OSEK/VDXをAUTOSAR OSの基礎として利用。([ISO][1])                                         |
|   3 | R24-11          | FO/TR Glossary                | **IEEE 1471-2000**                                                                                                            | ②廃止・④版違い         | IEEE自身が **Superseded**、42010-2011に置換。さらに42010-2011も42010-2022に置換。                                                  | 典型的な「Reference lifecycle未追従」。([IEEE Standards Association][2])                 |
|   4 | R24-11          | FO/TR Glossary                | **ISO/IEC 26262 Part 1 – Road vehicles – Functional safety: Vocabulary**                                                      | ①誤記・③タイトル        | 正式な規格番号は **ISO 26262-1:2018**。正式タイトルは *Road vehicles — Functional safety — Part 1: Vocabulary*。                    | **ISO/IEC 26262**ではなくISO 26262。番号・タイトル表記の修正候補。([ISO][3])                       |
|   5 | R24-11          | FO/TR Glossary                | **IEEE 1517-1999**                                                                                                            | ②廃止・④版違い         | IEEE自身が **Superseded**、1517-2010へ置換。                                                                               | 明確な旧版Reference。([IEEE Standards Association][4])                               |
|   6 | R24-11          | FO/TR Glossary                | **ISO/IEC 61511 Part 1 – Information technology – Software life cycle process**                                               | **①誤記**          | 61511はISO/IECではなく **IEC 61511**。しかも内容はInformation Technologyではなく、Process Industry向けSafety Instrumented Systems。    | 今回の中では**最も明確な誤記候補**。IEC 61511-1の正式名称とは全く異なる。([IEC Webstore][5])                |
|   7 | R24-11          | FO/TR Glossary                | **ISO 7498 – Information processing systems – Open Systems Interconnection – Basic Reference Model**                          | ②廃止・④版違い         | ISO 7498:1984はWithdrawn。現在は **ISO/IEC 7498-1:1994**。                                                               | Referenceに旧規格番号が残っている例。([ISO][6])                                              |
|   8 | R24-11          | CP/SWS StandardTypes          | **ISO 17356-3**                                                                                                               | ④版違いではない         | ISO側は2005 editionで現行。                                                                                              | むしろ「古いが正しいReference」の重要な対照例。                                                   |
|   9 | R24-11          | CP/SWS StandardTypes          | **ISO/IEC 9899:1990**                                                                                                         | **②廃止・④版違い**     | ISO公式で1999年にWithdrawn。現在はISO/IEC 9899:2024。                                                                        | **かなり強いReference maintenance候補**。([ISO][7])                                    |
|  10 | R24-11          | CP/SWS MFX Library            | **ISO/IEC 9899:1990 Programming Language – C**                                                                                | ②廃止・④版違い         | C90を参照しているが、1990版はWithdrawn。                                                                                       | R24-11にも同じ旧Referenceが残る。([AUTOSAR][8])                                         |
|  11 | R24-11          | CP/SWS EFX Library            | **ISO/IEC 9899:1990 Programming Language – C**                                                                                | ②廃止・④版違い         | 同上。                                                                                                                | 同じReferenceが複数文書に複製されることで、maintenance負荷が増える典型例。([AUTOSAR][9])                  |
|  12 | R25-11          | CP/SWS BFX Library            | **ISO/IEC 9899:1990 Programming Language – C**                                                                                | ②廃止・④版違い         | R25-11でもC90 Referenceが残る。                                                                                          | **R24-11→R25-11で継続している**点が重要。([AUTOSAR][10])                                   |
|  13 | R25-11          | CP/SWS MFL Library            | **ISO/IEC 9899:1990 Programming Language – C**                                                                                | ②廃止・④版違い         | R25-11でもC90を参照。                                                                                                    | 2024版Cが存在する現在、Reference lifecycle管理のPoCに非常に向く。([AUTOSAR][11])                  |
|  14 | R25-11          | CP/SWS DiagnosticLogAndTrace  | **ISO 7498 / ISO/IEC 7498-1:1994**                                                                                            | ③タイトル/表記         | AUTOSAR側は本文中で「ISO 7498」と記載しつつ、ReferenceではISO/IEC 7498-1:1994。ISO公式の正式名称は *Basic Reference Model: The Basic Model*。 | 「略記」と「正式Reference」の混在を検出する対象。([AUTOSAR][12])                                   |
|  15 | R25-11          | CP/RS COM                     | **ISO 17356-4:2005**                                                                                                          | ⑤AUTOSAR独自拡張     | AUTOSAR COMはOSEK COMをfunctional basisとし、OSEKにない機能を追加、異なる仕様をAUTOSAR側で優先。                                            | **非常に良い「ISO→AUTOSAR extension」実例**。([AUTOSAR][13])                             |
|  16 | R24-11/R25-11   | CP/SWS OS                     | **ISO 17356-3:2005 OSEK/VDX OS**                                                                                              | ⑤AUTOSAR独自拡張     | AUTOSAR OSはOSEK/VDXを基礎とし、Multi-Core、IOC等を追加。                                                                       | **ISO OSEK → AUTOSAR OS → Multi-Core OS**という発展関係を明示できる。([AUTOSAR][14])         |
|  17 | R24-11          | FO/RS StandardizationTemplate | AUTOSAR Extension Mechanisms                                                                                                  | ⑤AUTOSAR独自拡張     | AUTOSAR自身がExtension Mechanismsを明示的に定義し、Data Exchange Pointでの拡張利用を記述する仕組みを持つ。                                       | 「AUTOSARが国際規格をそのまま採用する」のではなく、**拡張を管理する仕組みそのもの**。([AUTOSAR][15])                |
|  18 | R25-11          | CP/RS COM                     | **ISO 17356-4をbasisにする**                                                                                                      | ⑤AUTOSAR独自拡張     | OSEK COMの全機能をそのまま採用するのではなく、AUTOSAR COMで異なる仕様・追加機能を定義。                                                              | WTO/TBTでいう「international standardをbasisとして使うが、同一ではない」の研究例にも使える。([AUTOSAR][13]) |

### 特に重要な5例

研究用としては、私は次の5つを「代表例」にします。

| 分類                | 代表例                                                                           | 何が面白いか                                      |
| ----------------- | ----------------------------------------------------------------------------- | ------------------------------------------- |
| **① 誤記**          | `ISO/IEC 61511 Part 1 – Information technology – Software life cycle process` | **規格番号、組織、タイトル、分野が食い違っている**。単なる古さではない       |
| **② 廃止**          | `IEEE 1471-2000`                                                              | IEEE自身がSupersededと明記                        |
| **③ タイトル変更/表記**   | `ISO 7498` → `ISO/IEC 7498-1:1994`                                            | 規格番号体系そのものが変わっている                           |
| **④ 版違い**         | `ISO/IEC 9899:1990`                                                           | R24-11/R25-11に残る一方、ISOでは2024 editionまで進んでいる |
| **⑤ AUTOSAR独自拡張** | `ISO 17356-4:2005 → AUTOSAR COM`                                              | ISO OSEK COMをbasisとして、AUTOSARが追加・変更している     |

ここで特に重要なのは、**「古いReference＝誤り」としないこと**です。

例えば `ISO 17356-3:2005` は20年以上前の規格ですが、ISO公式では2026年5月に確認され、現在もPublished/Currentです。したがって、これは「古いから誤り」ではありません。([ISO][1])

一方、`ISO/IEC 9899:1990` は明確にWithdrawnで、ISO/IEC 9899:2024が存在します。こちらは **「Reference lifecycleの更新候補」** と評価できます。([ISO][7])

---

## ここから見えてくる、かなり重要な構造

この表を作ってみると、前回お話しした **「AUTOSAR Reference Linter」** の設計がかなり具体化できます。

単純に

```text
Reference文字列
        ↓
最新規格を検索
        ↓
古かったらERROR
```

ではダメです。

むしろ、

```text
                    ┌── Current
                    │
AUTOSAR Reference ──┼── Superseded
                    │
                    ├── Withdrawn
                    │
                    ├── Title changed
                    │
                    ├── Number changed
                    │
                    ├── Edition changed
                    │
                    └── AUTOSAR extension
```

と分類すべきです。

特に **ISO 17356-4 → AUTOSAR COM** は、Reference Linterだけでは「不一致」と判定してはいけません。AUTOSAR自身が、

> ISO 17356-4:2005 is the functional basis

と明示したうえで、**ISOにない機能を追加し、ISOと異なる場合にはAUTOSAR仕様を優先する**という設計になっています。([AUTOSAR][13])

これはまさに、以前話していた

**「国際規格を参照する」≠「国際規格と完全一致する」**

を実証する実例です。

---

## さらに面白いのは R24-11 → R25-11 の比較

今回のサンプルでは、

```text
R24-11
  ISO/IEC 9899:1990
        ↓
R25-11
  ISO/IEC 9899:1990
```

というReferenceが実際に残っています。

つまり、

**ISO側のLifecycle**

```text
1990
 ↓
1999
 ↓
2011
 ↓
2018
 ↓
2024
```

に対して、

**AUTOSAR Reference**

```text
1990
 ↓
1990
 ↓
1990
 ...
```

となっている箇所があります。ISO/IEC 9899:1990はISO公式で1999年にWithdrawnされています。([ISO][7])

これは、まさに前回提案した

> **Reference Snapshot + Standards Lifecycle + Reference Linter**

のPoCに非常に適したケースです。

そしてもう一つ重要なのが、

```text
ISO/OSEK
     ↓
AUTOSAR
     ↓
AUTOSAR extension
     ↓
実装・量産
     ↓
フィードバック
     ↓
ISO revision
```

という**技術知識の逆流**です。

AUTOSAR OSについても、AUTOSAR自身が「OSEK/VDX OSを基礎」としながら、Multi-Core OSやIOCなどを拡張していることを明記しています。([AUTOSAR][14])

したがって、今回の18件を単なる「誤記一覧」とするより、

> **AUTOSAR R24-11/R25-11 International Standards Reference Lifecycle Case Study**

としてまとめる方が、研究としてかなり強いと思います。

なお、今回の18件は**全Referenceを機械的に網羅した監査結果ではなく、AUTOSAR公式文書から抽出した代表的なケーススタディ**です。特に①「誤記」は、誤植と断定できるものを厳しく絞っています。

[1]: https://www.iso.org/standard/40079.html?utm_source=chatgpt.com "ISO 17356-3:2005 - Road vehicles — Open interface for embedded automotive applications — Part 3: OSEK/VDX Operating System (OS)"
[2]: https://standards.ieee.org/ieee/1471/2187/?utm_source=chatgpt.com "IEEE SA - IEEE 1471-2000"
[3]: https://www.iso.org/standard/68383.html?utm_source=chatgpt.com "ISO 26262-1:2018 - Road vehicles — Functional safety — Part 1: Vocabulary"
[4]: https://standards.ieee.org/ieee/1517/2259/?utm_source=chatgpt.com "IEEE SA - IEEE 1517-1999"
[5]: https://webstore.iec.ch/en/iec_catalog/product/preview/?id=L3B1Yi9wZGYvcHJldmlldy9pbmZvX2llYzYxNTExLTF7ZWQyLjB9Yi5wZGY%3D&utm_source=chatgpt.com "IEC 61511-1:2016 © IEC 2016 — 9 —"
[6]: https://www.iso.org/standard/14252.html?browse=ics&utm_source=chatgpt.com "ISO 7498:1984 - Information processing systems — Open Systems Interconnection — Basic Reference Model"
[7]: https://www.iso.org/standard/17782.html?utm_source=chatgpt.com "ISO/IEC 9899:1990 - Programming languages — C"
[8]: https://www.autosar.org/fileadmin/standards/R24-11/CP/AUTOSAR_CP_SWS_MFXLibrary.pdf?utm_source=chatgpt.com "Specification of Fixed Point Math Routines"
[9]: https://www.autosar.org/fileadmin/standards/R24-11/CP/AUTOSAR_CP_SWS_EFXLibrary.pdf?utm_source=chatgpt.com "Specification of Extended Fixed Point Routines"
[10]: https://www.autosar.org/fileadmin/standards/R25-11/CP/AUTOSAR_CP_SWS_BFXLibrary.pdf?utm_source=chatgpt.com "Specification of Bit Handling Library"
[11]: https://www.autosar.org/fileadmin/standards/R25-11/CP/AUTOSAR_CP_SWS_MFLLibrary.pdf?utm_source=chatgpt.com "Specification of Floating Point Math Library"
[12]: https://www.autosar.org/fileadmin/standards/R25-11/CP/AUTOSAR_CP_SWS_DiagnosticLogAndTrace.pdf?utm_source=chatgpt.com "Specification of Diagnostic Log and Trace"
[13]: https://www.autosar.org/fileadmin/standards/R25-11/CP/AUTOSAR_CP_SWS_COM.pdf?utm_source=chatgpt.com "Specification of Communication"
[14]: https://www.autosar.org/fileadmin/standards/R24-11/CP/AUTOSAR_CP_SWS_OS.pdf?utm_source=chatgpt.com "Specification of Operating System"
[15]: https://www.autosar.org/fileadmin/standards/R24-11/FO/AUTOSAR_FO_RS_StandardizationTemplate.pdf?utm_source=chatgpt.com "Requirements on Standardization Template"


