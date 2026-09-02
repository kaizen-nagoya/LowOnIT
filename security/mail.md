# Q1 高齢者が持つ技術スキルを判定できるエンジニアがいない場合に、スキル判定、業務分担、賞与用評価ができないという課題があるとお聞きしています。スキル判定、業務分担、賞与用評価の課題と解決方法を８つづつ示し、参考となる資料、論文をWikipedia以外のURLで合計２４個示してくだし。
A1 by CHatGPT

はい。これはかなり面白いテーマです。しかも、単なる「PPAPは危険」という話にせず、**「暗号文と復号鍵・パスワードを同一経路に流さない」という古典的な鍵管理・チャネル分離の原則が、なぜ製造業の業務慣行では形骸化したのか**という研究テーマにすると、かなり筋が通ります。

まず重要な点を一つ修正します。

> **「暗号化ファイルとパスワードを別メールにする」こと自体が、必ずしも安全とは限りません。**

同じメールシステムを使って

* メール1：暗号化ZIP
* メール2：復号パスワード

と送っても、攻撃者がメールアカウント、メールサーバ、メールゲートウェイを取得すれば**両方を入手できます**。

したがって本来の原則は、

> **暗号化データと、それを復号する秘密情報について、攻撃者から見た独立性を確保する**

です。

現在のNIST SP 800-63B Rev.4でも、Out-of-Band認証について「primary channel」と「secondary channel」を分離し、さらに**電子メールをOOB認証チャネルとして使用してはならない**と明記しています。([NIST Pages][1])
OWASPも、暗号化データと鍵を可能な限り別の場所に置く「Separation of Keys and Data」を明示しています。([OWASP Cheat Sheet Series][2])

以下、この原則を研究するための文献を **古典16＋最近16** に分けます。

---

# Ⅰ．古い基礎文献・論文・標準 16種類

年代順に近い形で並べます。

| No. | 文献                                                                                                   |         年 | このテーマとの関係                          |
| --: | ---------------------------------------------------------------------------------------------------- | --------: | ---------------------------------- |
|   1 | Shannon, **Communication Theory of Secrecy Systems**                                                 |      1949 | 暗号通信の数学的基礎。秘密鍵と暗号文を分離して考える出発点      |
|   2 | Feistel, **Cryptographic Coding for Data-Bank Privacy**                                              |      1973 | コンピュータデータの暗号化・鍵管理という実用的問題          |
|   3 | Diffie & Hellman, **New Directions in Cryptography**                                                 |      1976 | 公開鍵暗号と鍵配送問題を根本から転換                 |
|   4 | Merkle, **Secure Communications Over Insecure Channels**                                             |      1978 | 安全でない通信路上で秘密を確立する問題。チャネル分離研究の重要な基礎 |
|   5 | Needham & Schroeder, **Using Encryption for Authentication in Large Networks**                       |      1978 | 認証と鍵配送をネットワークプロトコルとして体系化           |
|   6 | Denning & Sacco, **Timestamps in Key Distribution Protocols**                                        |      1981 | 鍵配送、再送攻撃、時刻情報                      |
|   7 | Lampson, **Accountability and Freedom**                                                              | 1973/1982 | 認証・アクセス制御・責任追跡という組織的セキュリティ         |
|   8 | Morris & Thompson, **Password Security: A Case History**                                             |      1979 | パスワードを秘密情報としてどう管理するかを扱う古典          |
|   9 | Rivest, Shamir & Adleman, **A Method for Obtaining Digital Signatures and Public-Key Cryptosystems** |      1978 | RSA。鍵配送問題を公開鍵方式で解決                 |
|  10 | Kahn, **The Codebreakers**                                                                           |      1967 | 暗号通信と通信路・鍵管理の歴史的理解                 |
|  11 | Diffie, **The First Ten Years of Public-Key Cryptography**                                           |      1988 | 公開鍵暗号と鍵配送問題の発展史                    |
|  12 | Bellovin & Merritt, **Encrypted Key Exchange**                                                       |      1992 | パスワードを使った安全な鍵交換。今回のテーマに特に近い        |
|  13 | Bellovin & Merritt, **Augmented Encrypted Key Exchange**                                             |      1993 | パスワード認証と暗号鍵交換を分離して扱う発想             |
|  14 | Zimmermann, **The Official PGP User's Guide**                                                        |      1995 | PGPによる実用的な暗号通信                     |
|  15 | RFC 2015, **MIME Security with Pretty Good Privacy (PGP)**                                           |      1996 | PGPをメールに組み込む標準化。暗号化メールの基礎          |
|  16 | RFC 3156, **MIME Security with OpenPGP**                                                             |      2001 | OpenPGPによるメール暗号化を標準化               |

特に **3、4、5、8、12、13、15、16** は今回の研究では重要です。

RFC 2015は1996年の標準で、PGPの暗号化・署名をMIMEメールに組み込んでいます。([RFCエディタ][3])
RFC 3156では、暗号化されたデータをメールのMIME構造として扱っています。([RFCエディタ][4])

つまり、**「暗号化ファイルをメールで送る」という技術そのものは30年近く前から標準化されていた**わけです。

---

# Ⅱ．今回の問題に特に近い古典

16個の中でも、私は次の4本を「核心文献」と考えます。

### ① Diffie & Hellman 1976

**New Directions in Cryptography**

ここで本質的に問題になったのが、

> 「暗号化するための鍵を、どう安全に相手に渡すのか？」

という問題です。

つまり、

**暗号化アルゴリズムの問題 ≠ 鍵配送の問題**

です。

製造業のPPAP問題も実はここに戻ります。

---

### ② Needham–Schroeder 1978

**Using Encryption for Authentication in Large Networks**

ここでは、

```text
通信
  │
  ├── データ
  │
  └── 認証・鍵
```

をプロトコルとして扱います。

「データを暗号化したから安全」ではなく、

> **誰に鍵を渡すのか**
>
> **いつ鍵を渡すのか**
>
> **誰が相手を認証したのか**

まで考える必要があることを示した古典です。

---

### ③ Bellovin & Merritt 1992

**Encrypted Key Exchange**

今回の「パスワードを別経路にする」という問題にかなり近いです。

パスワードを単純に通信するのではなく、**パスワードを使って暗号学的に鍵交換する**という方向に進みます。

これは、

> 「パスワードをメールで送る」

から

> 「そもそもパスワードを通信経路に直接流さなくてもよい」

への発想転換です。

---

### ④ RFC 3156 / OpenPGP

PGP/OpenPGPは、

```text
平文
 ↓
セッション鍵で暗号化
 ↓
公開鍵でセッション鍵を保護
 ↓
暗号文
```

という構造を取ります。

つまり、**「暗号化ファイル＋パスワード」という人間依存の運用そのものを、公開鍵暗号によって置き換える**ことができます。

---

# Ⅲ．最近の規格・論文・特許 16種類

ここは「2020年代」を中心にします。

| No. | 文献・規格・特許                                                 |     年 | 意義                     |
| --: | -------------------------------------------------------- | ----: | ---------------------- |
|   1 | NIST SP 800-63B Rev.4                                    |  2025 | OOB認証でチャネル分離を明確化       |
|   2 | NIST SP 800-57 Part 1 Rev.5                              |  2020 | 暗号鍵管理                  |
|   3 | NIST SP 800-57 Part 1 Rev.6 Draft                        |  2025 | 鍵管理、KEM等を更新            |
|   4 | NIST SP 800-133 Rev.2                                    |  2020 | 暗号鍵生成                  |
|   5 | NIST SP 800-108 Rev.1                                    |  2024 | KDFによる鍵導出              |
|   6 | NIST FIPS 203 / ML-KEM                                   |  2024 | ポスト量子鍵カプセル化            |
|   7 | RFC 8551 / S/MIME 4.0                                    |  2019 | メール暗号化・署名              |
|   8 | RFC 9580 / OpenPGP                                       |  2024 | 最新OpenPGP標準            |
|   9 | RFC 9787 / Guidance on End-to-End Email Security         |  2025 | E2Eメールセキュリティの最新指針      |
|  10 | OWASP Cryptographic Storage Cheat Sheet                  |    最新 | データと鍵の分離               |
|  11 | OWASP Key Management Cheat Sheet                         |    最新 | 鍵生成・配送・保管              |
|  12 | JP6885150B2, File sharing system                         |  2021 | 認証サーバと暗号化ファイルを分離       |
|  13 | JP7661576B2, File management system                      | 2025頃 | 認証後に暗号化添付を取得           |
|  14 | JP7014994B2, Email monitoring device                     | 2022頃 | 暗号化添付＋別経路パスワードを扱う      |
|  15 | US20170099268A1, Encrypted message communication         |  2017 | パスワードをメールとは独立した通信経路で伝達 |
|  16 | WO2023230271A1, Techniques for anonymizing user activity |  2023 | 暗号化添付とパスワードを別経路で伝える実装例 |

---

# Ⅳ．最近の資料で特に重要なもの

## 1. NIST SP 800-63B Rev.4

これは今回の研究では**最重要クラス**です。

NISTは、

> primary channel

と

> secondary channel

を明確に分けています。

そして、OOB認証について、

```text
Primary Channel
      │
      │ 認証要求
      ▼
   Verifier
      ▲
      │
Secondary Channel
```

という考え方を採用します。

さらに重要なのが、

> **Email SHALL NOT be used for out-of-band authentication**

という明確な規定です。理由として、メールはパスワードだけでアクセスされる可能性、途中・メールサーバでの傍受、DNS spoofingによるリルーティングなどが挙げられています。([NIST Pages][1])

これは、まさに今回の問題を現代的な認証設計として表現したものです。

---

# Ⅴ．OWASPの「Separation of Keys and Data」

これも非常に重要です。

OWASPは、

> **暗号鍵は可能な限り暗号化データとは別の場所に保存する**

と明示しています。さらに、

```text
Data
 │
 └── DEK ── encrypted data

KEK
 │
 └── DEKを暗号化
```

というEnvelope Encryptionの考え方を説明しています。KEKとDEKも分離することが推奨されています。([OWASP Cheat Sheet Series][2])

したがって、

```text
暗号化ZIP
+
パスワードを同じメール
```

は、

**「暗号化した」という一点だけを見れば安全だが、鍵管理としては弱い**

ということになります。

---

# Ⅵ．さらに面白いのが「最近の特許」

今回の研究では、実は**特許が非常に面白い資料**になります。

例えばJP6885150B2のファイル共有システムでは、

```text
利用者
 │
 ├── 暗号化ファイル
 │
 └── 認証サーバ
        │
        └── 権限確認
```

という構造を採用しています。

暗号化ファイルには認証サーバの情報や、認証サーバの公開鍵で暗号化された共通鍵などを含める構成です。([Google Patents][5])

つまり、

> **「パスワードを別メールで送る」**

という人間の運用を、

> **「認証サーバにアクセスして権限を確認する」**

というシステムに置き換えています。

これは製造業の現場改革には非常に重要な考え方です。

---

# Ⅶ．実は「PPAPをやめる」だけでは不十分

ここが今回の研究で一番面白いところだと思います。

従来：

```text
        メール
          │
   ┌──────┴──────┐
   ↓             ↓
暗号化ZIP       パスワード
```

これを、

```text
        メール
          │
          ↓
      暗号化ZIP

        電話
          │
          ↓
      パスワード
```

にしても、まだ**人間の運用に依存**しています。

さらに電話番号がメールに書いてあれば、

```text
メール
 │
 ├─ 暗号化ZIP
 └─ 電話番号

電話
 │
 └─ パスワード
```

となり、攻撃者が両方を取得できる可能性があります。

より良い設計は、

```text
             ┌─────────────┐
             │ 認証サーバ   │
             └──────┬──────┘
                    │
              認証・認可
                    │
       ┌────────────┴────────────┐
       ↓                         ↓
  暗号化データ                 鍵
       │                         │
       └─────────┬───────────────┘
                 ↓
             利用者
```

です。

つまり、

> **「別メール」から「別チャネル」へ、さらに「鍵管理システム」へ**

進化させる必要があります。

---

# Ⅷ．この問題を研究テーマにするなら

私は次のようなタイトルがかなり良いと思います。

> **「暗号化ファイルと復号鍵の分離原則に関する研究
> ― PPAP型運用からゼロトラスト型ファイル共有への移行 ―」**

あるいは、製造業に焦点を絞るなら、

> **「製造業における暗号化ファイル送信慣行のセキュリティ分析
> ― 40年以上前の暗号鍵配送原則と現代の業務慣行の乖離 ―」**

です。

そして研究の中心を、

```text
1949
 Shannon
   ↓
1976
 Diffie-Hellman
   ↓
1978
 Needham-Schroeder
   ↓
1992
 Encrypted Key Exchange
   ↓
1996/2001
 PGP / OpenPGP
   ↓
2010年代
 PPAP型業務慣行
   ↓
2020年代
 Zero Trust
 Key Management
 OOB Authentication
   ↓
2025
 NIST SP 800-63B Rev.4
```

という**「技術は進歩しているのに、企業の業務プロセスが古典的な鍵管理原則に追いついていない」**という歴史的比較にすると、非常に面白い研究になります。

特にNISTの現行規格は、単に「暗号化せよ」ではなく、**primary channel / secondary channel / authentication / channel binding**まで踏み込んでいます。([NIST Pages][1])

また、NISTの2025年版鍵管理文書では、従来の鍵管理に加えてKEMなども取り込む方向に進んでいます。([NISTパブリケーション][6])

**したがって、今回のテーマは「PPAP批判」よりも、「暗号技術における鍵とデータの分離という古典原則が、なぜ企業のSoftware Process／業務プロセスに実装されなかったのか」という研究にした方が、ずっと深くなります。**

なお、最近の特許にも、暗号化添付とパスワードを同じメールで扱う方式そのものが明記されている例があります。([Google Patents][7]) これは、**「技術者は危険性を認識していたが、ユーザビリティ・運用コストとのトレードオフで旧来方式が残った」**ことを調べるうえで、非常に興味深い一次資料になります。

[1]: https://pages.nist.gov/800-63-4/sp800-63b.html?utm_source=chatgpt.com "NIST Special Publication 800-63B"
[2]: https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html?utm_source=chatgpt.com "Cryptographic Storage - OWASP Cheat Sheet Series"
[3]: https://www.rfc-editor.org/info/rfc2015/?utm_source=chatgpt.com "RFC 2015: MIME Security with Pretty Good Privacy (PGP) | RFC Editor"
[4]: https://www.rfc-editor.org/info/rfc3156/?utm_source=chatgpt.com "RFC 3156: MIME Security with OpenPGP | RFC Editor"
[5]: https://patents.google.com/patent/JP6885150B2/en?utm_source=chatgpt.com "JP6885150B2 - File sharing system, file sharing device, file sharing method, and file sharing program - Google Patents"
[6]: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r6.ipd.pdf?utm_source=chatgpt.com "NIST SP 800-57pt1r6 initial public draft, Recommendation for Key Management: Part 1 — General"
[7]: https://patents.google.com/patent/US20240386109A1/en?utm_source=chatgpt.com "US20240386109A1 - Analysis of Malware - Google Patents"

# Q2 インタネットが始まったころ、IDを短い名前を使っていた人たちがいました。1995年にWindows９５が発売され、すべてのPCがデフォルトでインタネット接続可能になり、メールアドレスを姓名のfull spellingを使うことを提唱してきました。オンラインで人によびかけたりするときに、アルファベットで発音がすぐわかり、姓名で読んだ方が同姓の方がいても混同しないようにできるし、メールアドレスを決める際も、同姓同名の人以外は一意に決めることができ無駄な作業がないといわれています。30年経っても、いまだにメールアドレスに姓名のfull spellingを使っていない組織があるとのことです。なぜかと、その組織にどう働きかけたらいいでしょうか。
A2 

はい。私はこの問題を、単に「メールアドレスを姓名にしましょう」という命名規則の話ではなく、**「人間がコンピュータ上で相手を識別するためのインターフェース設計」**として扱うのがよいと思います。

そして、面白いことに、1995年のRFC 1781にはすでに、**「人にとって分かりやすく、かつ曖昧なく対象を特定できる名前」**という考え方がかなり明確に書かれています。RFC 1781は1995年3月、まさにWindows 95発売前です。([rfc-editor.org](https://www.rfc-editor.org/rfc/rfc1781.html?utm_source=chatgpt.com)) 

ただし、結論から言うと、**「姓名のfull spellingをメールアドレスにする」ことを絶対原則にするのは、現在では少し修正した方が強い**です。

---

## 1. まず、30年間変わらなかった理由

組織が短いIDや意味不明なIDを使い続ける理由は、技術的な理由よりも**組織設計上の理由**が大きいです。

代表的には次の8つがあります。

| 理由               | 組織側の考え方                      |
| ---------------- | ---------------------------- |
| ① 過去システムとの互換性    | 30年前のID体系を変えると大量のシステム変更が必要   |
| ② IDを「人名」と考えていない | メールアドレスを「システム内部ID」と考える       |
| ③ 重複問題           | `taro.yamada` と同姓同名が出たらどうするか |
| ④ 改姓問題           | 結婚・離婚などで姓が変わったらどうするか         |
| ⑤ 退職・異動          | 人が変わってもIDを再利用したい             |
| ⑥ セキュリティ         | 本名を公開するのは情報漏洩だという考え          |
| ⑦ プライバシー         | メールアドレスそのものを個人情報として扱う        |
| ⑧ 組織内政治          | 「今困っていないので変えない」              |

特に重要なのは②です。

組織のIT部門はしばしば、

> **ユーザーID = コンピュータが人を識別するための番号**

と考えます。

一方、利用者は、

> **メールアドレス = 人間が相手を呼び、覚え、伝えるための住所**

と考えます。

この**設計思想の違い**が、30年間残った大きな理由だと思います。

---

# 2. 実は1995年のRFCにも「曖昧性」の問題が書かれている

ここは非常に面白いです。

1995年3月の **RFC 1781 "Using the OSI Directory to Achieve User Friendly Naming"** は、

> User Friendly Name

という概念を扱っています。

そして、ユーザーが伝える名前について、

> **効率的かつ曖昧なく一つの対象に解決できる名前を選ぶべき**

という考え方を示しています。([rfc-editor.org](https://www.rfc-editor.org/rfc/rfc1781.html?utm_source=web.run)) 

つまり、

```text
短い
  ↓
覚えやすい
  ↓
しかし誰なのか分からない
```

より、

```text
人間が理解できる
      ＋
一意に識別できる
      ＋
組織内で解決できる
```

という設計が重要だということです。

これは、質問されている問題と非常に近いです。

---

# 3. ただし「full spelling = 常に正しい」ではありません

ここは現在の研究として重要です。

例えば、

```text
taro.yamada@example.com
```

は、

* 誰か分かる
* 発音しやすい
* 電話で伝えやすい
* 名刺に書きやすい
* 同姓同名の処理もしやすい

という利点があります。

一方で、

```text
John.Smith@example.com
```

のような方式は、同姓同名問題が非常に早く発生します。

また、

```text
Taro.Yamada123@example.com
```

などになると、結局「123は何？」という問題が発生します。

さらに、

```text
田中一郎
```

のローマ字表記を

```text
ichiro.tanaka
```

にするのか、

```text
tanaka.ichiro
```

にするのか、

```text
tanaka.ichiro@example.jp
```

にするのか、

日本人の名前をどうローマ字化するのかという問題もあります。

---

# 4. そして現在は「姓名をメールアドレスに入れない」という考え方も強くなっています

ここが1995年との大きな違いです。

NISTの現在のDigital Identity Guidelinesでは、**デジタルIDと現実世界の人物を必ずしも同一視しない**考え方が明確になっています。

NIST SP 800-63-4は2025年に公開され、デジタルアイデンティティについて、オンラインサービスの文脈では一意なデジタルIDを持つ一方、現実世界の人物が誰なのかを必ず公開する必要はない、としています。([nist.gov](https://www.nist.gov/publications/nist-sp-800-63-4-digital-identity-guidelines?utm_source=turn0search5)) 

さらに、Federationでは、

> username、email address、employee numberなどの平文PIIを識別子に含めない

という考え方があります。([pages.nist.gov](https://pages.nist.gov/800-63-4/sp800-63c.html?utm_source=turn0search10)) 

つまり現在のベストプラクティスは、

**「人間に分かりやすい名前」**

と

**「システム内部で一意なID」**

を**分離する方向**です。

---

# 5. 私なら「姓名full spelling」を次のように再定義します

ここが組織に働きかけるときのポイントです。

「メールアドレスを姓名にしろ」

ではなく、

> **人間向け識別子とコンピュータ向け識別子を分離し、人間向け識別子は可能な限り自然言語による正式名称を使う**

と提案します。

例えば、

```text
                    Person
                       │
          ┌────────────┴────────────┐
          │                         │
     Human Identifier         Machine Identifier
          │                         │
          ↓                         ↓
  Taro Yamada                 8f3a91c2...
  taro.yamada@example.jp
```

という構造です。

---

# 6. これなら「姓名メールアドレス」の長所を残せます

例えば社員情報を、

| 項目            | 値                        |
| ------------- | ------------------------ |
| 氏名            | Yamada Taro              |
| 表示名           | 山田 太郎                    |
| Email         | `taro.yamada@example.jp` |
| Employee ID   | `A037521`                |
| Internal UUID | `8f3a...`                |

とします。

すると、

### 人間

```text
山田太郎さんにメールしてください
```

### メール

```text
taro.yamada@example.jp
```

### 人事システム

```text
A037521
```

### IAM / SSO

```text
UUID
```

と使い分けられます。

これなら、

**「メールアドレスを変更したら全部のシステムが壊れる」**

という従来のIT部門の反対理由もなくなります。

---

# 7. もう一つ重要なのは「メールアドレス」と「ID」を分けること

これはかなり強い提案になります。

例えば、

```text
Employee ID
    ↓
A037521
    │
    ├── Email
    │      ↓
    │  taro.yamada@example.jp
    │
    ├── Microsoft 365
    │
    ├── GitHub
    │
    ├── Moodle
    │
    └── ERP
```

とします。

つまり、

> **社員番号が本当のIdentityで、メールアドレスは人間向けのAlias**

とするわけです。

そうすると改姓しても、

```text
taro.yamada@example.jp
       ↓
taro.sato@example.jp
```

という変更が可能です。

内部IDは、

```text
A037521
```

のままです。

---

# 8. 「同姓同名」は実は問題ではありません

ここも組織に説明するときに重要です。

例えば、

```text
Taro Yamada
Taro Yamada
```

が2人いたとしても、

```text
taro.yamada@example.jp
taro.yamada2@example.jp
```

のようにする必要は必ずしもありません。

むしろ、

```text
taro.yamada.sales@example.jp
taro.yamada.engineering@example.jp
```

など、**組織上の文脈を付加する方法**があります。

ただし、部署異動でアドレスが変わる問題があるので、長期的には

```text
taro.yamada@example.jp
```

を固定し、

```text
表示名：山田 太郎（技術部）
```

などを使う方がよいでしょう。

---

# 9. そして「名前を公開することはセキュリティ上危険」という反論

これは半分正しく、半分間違っています。

NISTもusernameが個人を特定できる情報を含む場合にはPIIになり得ると説明しています。([pages.nist.gov](https://pages.nist.gov/800-63-FAQ/?pubDate=20250428&utm_source=turn0search0)) 

したがって、

```text
taro.yamada@example.com
```

をインターネット上に無制限に公開することと、

```text
taro.yamada@example.com
```

を**社内メールアドレスとして使うこと**

は分けるべきです。

---

# 10. さらに1997年のRFC 2142も重要です

RFC 2142は、

```text
postmaster@
hostmaster@
abuse@
security@
sales@
support@
```

など、**人ではなく組織の役割に対応したメールアドレス**を標準化しています。([rfc-editor.org](https://www.rfc-editor.org/info/rfc2142/?utm_source=turn0search8)) 

したがって私は、組織のメール体系を、

```text
【Person】

taro.yamada@example.com


【Role】

support@example.com
security@example.com
sales@example.com


【System】

build@example.com
noreply@example.com
```

の3種類に分けることを勧めます。

これなら「全部姓名にしろ」という極端な提案にもなりません。

---

# 11. 組織への働きかけ方

ここは「正しいから変えてください」では、おそらく負けます。

30年続いている仕組みには、必ず**変えない理由**があります。

そこで、

### ❌ 悪い提案

> 「30年前から間違っています。姓名のメールアドレスに変更してください。」

ではなく、

### ⭕ 良い提案

> **「人間向け識別子とシステム内部識別子を分離して、メール・SSO・人事・業務システムの識別体系を整理しませんか。」**

とします。

---

# 12. さらに「コスト削減」を数字で示す

例えば、

```text
短縮ID
  ↓
「このIDは誰？」
  ↓
名簿検索
  ↓
社員番号確認
  ↓
部署確認
  ↓
メール送信
```

という作業が発生します。

一方、

```text
taro.yamada@example.jp
```

なら、

```text
誰？
↓
山田太郎
```

となります。

つまり、

> **メールアドレスは単なる通信先ではなく、Human-Computer Interfaceである**

と定義できます。

これはかなり強い論点です。

---

# 13. 私なら組織にこの4段階で提案します

### Phase 1：現状調査

```text
社員数
メールアドレス形式
同姓同名
短縮ID
改姓
異動
退職
外部連絡
```

を調査。

### Phase 2：Human-readable identifier

新規採用者から、

```text
given.family@example.jp
```

を原則にする。

### Phase 3：既存社員

既存の

```text
k0351@example.jp
abc123@example.jp
```

はすぐ変更せず、

```text
abc123@example.jp
       ↓
taro.yamada@example.jp
```

を**aliasとして追加**。

### Phase 4：内部IDとの分離

最終的に、

```text
                 Identity
                    │
       ┌────────────┼────────────┐
       ↓            ↓            ↓
 Employee ID      Email       Display Name
       │            │            │
   A037521   taro.yamada@   山田 太郎
             example.jp
```

にします。

---

# 14. 研究テーマとしても面白いです

今回の話は、先ほどのPPAPの話と実はつながっています。

PPAPも、

> **40年前から知られているセキュリティ原則と、現在の企業の業務プロセスとの乖離**

でした。

今回も、

> **1990年代から存在するHuman-readable namingの思想と、2026年の企業IAM・メール運用との乖離**

です。

さらに面白いのは、**両者とも「技術的には解決済みなのに、組織プロセスが変わらない」**という共通点です。

```text
          技術
           │
           ↓
    ┌─────────────┐
    │  理想的設計  │
    └──────┬──────┘
           │
           ↓
       組織プロセス
           │
           ↓
      古い慣行が残る
           │
           ↓
      人間の無駄な作業
           │
           ↓
      セキュリティ低下
```

これは、以前お話しした**Software Processにおける Human / AI / Computer の責任境界**ともつながります。

特に現在のNIST SP 800-63-4は、デジタルIDについて「本人を表す属性」と「オンラインサービス上の識別子」を分けて考えています。([nist.gov](https://www.nist.gov/publications/nist-sp-800-63-4-digital-identity-guidelines?utm_source=turn0search5)) 

ですから、私は最終的には、

> **「姓名をメールアドレスにするべきか」**

より、

> **「人間にとって可読・発音可能・記憶可能な識別子と、機械にとって一意・永続的・プライバシー保護可能な識別子を、どのように設計・分離すべきか」**

という問題設定をお勧めします。

この形なら、**RFC 1781（1995）→ RFC 2377（1998）→ 国際化メール RFC 6530 → NIST Digital Identity Guidelines（2025）**という30年の技術史をつなげられます。RFC 2377も、ディレクトリの人物名についてメールボックス識別子を使う設計を具体的に論じています。([rfc-editor.org](https://www.rfc-editor.org/rfc/rfc2377.html?utm_source=turn0search13)) 

そして、**「30年前の提案がなぜ組織に定着しなかったのか」**を、技術・経済・セキュリティ・プライバシー・組織慣性・UXの6側面から分析すると、かなり面白い研究になると思います。
