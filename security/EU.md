# Q1 セキュリティに関するEUの法体系、指令などの全体像と、国際条約、国際規格との関係をお示しください。
A1 by chatgpt

はい。ここは、先ほどの **AUTOSAR・ISO/IEC・UNECE/WP.29の関係**ともかなり深くつながります。

結論からいうと、EUのセキュリティ法体系は単一の「サイバーセキュリティ法」があるのではなく、

> **EU条約・EU法 → 分野別のEU規則/指令 → 欧州標準・認証 → 国際規格 → 国際条約・国際ルール**

という多層構造になっています。

特に自動車については、一般的なEUサイバー法だけでなく、**UNECE UN R155/R156とISO/SAE 21434等が重なる**ため、かなり複雑です。

---

# 1. 全体像

まず大きく分けると、次の5層で考えると分かりやすいです。

```text
                 国際社会
┌────────────────────────────────────┐
│ 国際条約・国際法                    │
│ ・UN Convention against Cybercrime  │
│ ・Budapest Convention               │
│ ・UN Charter / Human Rights         │
└──────────────────┬─────────────────┘
                   │
                   ▼
┌────────────────────────────────────┐
│ 国際規格・国際的ルール              │
│ ISO/IEC 27001                       │
│ ISO/IEC 27002                       │
│ ISO/SAE 21434                       │
│ ISO 24089                           │
│ UN Regulation R155/R156             │
└──────────────────┬─────────────────┘
                   │
                   ▼
             ┌─────────────┐
             │     EU      │
             │   法体系    │
             └──────┬──────┘
                    │
       ┌────────────┼─────────────┐
       ▼            ▼             ▼
   横断的法制    分野別法制     データ・人権
       │            │             │
   NIS2          DORA          GDPR
   CRA           RED           eIDAS
   Cybersecurity CER           AI Act
   Act
       │
       ▼
┌────────────────────────────────────┐
│ EU加盟国の国内法・監督・罰則        │
└────────────────────────────────────┘
```

重要なのは、

**国際規格は通常「法律」ではない**

という点です。

ISO/IEC 27001を取得したからEU法を全部満たした、という意味にはなりません。

逆にEU法がISO規格を参照した場合には、**法的要求を具体化する技術的手段として規格が非常に重要になる**、という関係です。

---

# 2. EUのサイバーセキュリティ法の中心

現在のEU法制では、特に次の法律が中心です。

| 法令                                                  | 略称                    | 主な対象              | 性格                |
| --------------------------------------------------- | --------------------- | ----------------- | ----------------- |
| Directive (EU) 2022/2555                            | **NIS2**              | 重要・重要度の高い事業者      | 組織・ネットワークのサイバーリスク |
| Regulation (EU) 2024/2847                           | **CRA**               | デジタル要素を持つ製品       | 製品セキュリティ          |
| Regulation (EU) 2019/881                            | **Cybersecurity Act** | ENISA・認証          | EUサイバー認証          |
| Directive (EU) 2022/2557                            | **CER**               | Critical Entities | 重要事業者のレジリエンス      |
| Regulation (EU) 2022/2554                           | **DORA**              | 金融                | 金融ICTリスク          |
| Regulation (EU) 2016/679                            | **GDPR**              | 個人データ             | プライバシー＋情報セキュリティ   |
| Regulation (EU) 2024/1689                           | **AI Act**            | AIシステム            | AIリスク・安全・セキュリティ   |
| Directive 2014/53/EU + Delegated Regulation 2022/30 | **RED Cybersecurity** | 無線機器              | 製品サイバーセキュリティ      |

---

# 3. NIS2――「組織」を守る法律

[NIS2 Directive – EUR-Lex](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng?utm_source=chatgpt.com)

NIS2は、

**Directive (EU) 2022/2555**

です。

目的はEU全体で高い共通レベルのサイバーセキュリティを確保することです。従来のNIS Directiveを置き換えました。([EUR-Lex][1])

対象は例えば、

* エネルギー
* 輸送
* 銀行
* 金融市場
* 医療
* デジタルインフラ
* ICTサービス
* 公共行政
* 製造業の一部

などです。

つまりNIS2は、

> **「会社・組織としてサイバー攻撃にどう備えるか」**

が中心です。

例えば、

```text
リスク分析
   ↓
セキュリティ対策
   ↓
Incident Detection
   ↓
Incident Reporting
   ↓
Recovery
   ↓
Management Responsibility
```

という管理体系になります。

---

# 4. CRA――「製品」を守る法律

これは今回の話では特に重要です。

[Cyber Resilience Act – EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng?utm_source=chatgpt.com)

**Cyber Resilience Act (CRA)** は Regulation (EU) 2024/2847です。

NIS2が主として「組織」を対象とするのに対して、CRAは、

> **Products with Digital Elements**

を対象とします。

つまり、

* ソフトウェア
* IoT機器
* ネットワーク機器
* OS
* 組込みソフトウェア
* デジタル機能を持つ製品

などです。

CRAは設計・開発・製造だけではなく、**脆弱性対応を製品のライフサイクル全体で要求**しています。([EUR-Lex][2])

したがって、

```text
              NIS2
                │
         ┌──────▼──────┐
         │ Organization │
         └──────────────┘

              CRA
                │
         ┌──────▼──────┐
         │    Product   │
         └──────────────┘
```

という整理が非常に有用です。

---

# 5. Cybersecurity Act――ENISAと認証

[EU Cybersecurity Act – EUR-Lex](https://eur-lex.europa.eu/eli/reg/2019/881/oj/eng?utm_source=chatgpt.com)

Regulation (EU) 2019/881は、

* ENISAの権限・組織
* EU cybersecurity certification framework

を定めています。([EUR-Lex][3])

ここで重要なのは、

**「規格」と「認証」をつなぐ仕組み**

だということです。

```text
ISO/IEC規格
      │
      ▼
技術的要求事項
      │
      ▼
EU harmonised standards
      │
      ▼
Conformity Assessment
      │
      ▼
Certification
```

という流れを作ることができます。

---

# 6. CER――Cybersecurityだけではなく「レジリエンス」

[Critical Entities Resilience Directive – EUR-Lex](https://eur-lex.europa.eu/eli/dir/2022/2557/oj/eng?utm_source=chatgpt.com)

**CER Directive (EU) 2022/2557** は重要事業体のレジリエンスを扱います。([EUR-Lex][4])

ここでは、

> Cybersecurity

だけではありません。

例えば、

* 自然災害
* テロ
* 物理攻撃
* 停電
* サイバー攻撃
* その他の重大インシデント

を含めて、

```text
Prevent
  ↓
Protect
  ↓
Respond
  ↓
Resist
  ↓
Mitigate
  ↓
Recover
```

という考え方になります。

NIS2との連携も明示されています。([EUR-Lex][5])

したがって、

**NIS2 = Cyber resilience**

**CER = Overall resilience**

と整理すると理解しやすいです。

---

# 7. DORA――金融だけの特別法

金融については、

**Digital Operational Resilience Act (DORA)**

があります。

これは金融機関に対して、

* ICT risk management
* incident reporting
* resilience testing
* third-party ICT risk
* ICT service providers

などを要求する体系です。

したがって、

```text
一般企業       → NIS2
デジタル製品   → CRA
金融          → DORA
重要インフラ   → CER
```

という分野別の重なりがあります。

---

# 8. GDPR――個人情報とSecurity

GDPRは「サイバーセキュリティ法」そのものではありません。

しかしSecurityと非常に密接です。

特にArticle 32の、

> Security of processing

が重要です。

つまり、

```text
個人データ
   ↓
Privacy
   +
Security
```

という構造です。

例えば、

* confidentiality
* integrity
* availability
* resilience
* restoration
* testing

などが問題になります。

したがって、

**Cybersecurity ≠ Privacy**

ですが、

**Cybersecurity ∩ Privacy**

という大きな重なりがあります。

---

# 9. RED――IoT・無線機器

自動車やIoTではこれも重要です。

Radio Equipment Directive (RED) 2014/53/EUに対して、Commission Delegated Regulation (EU) 2022/30が追加され、一定のインターネット接続無線機器などについて、

* network protection
* personal data/privacy protection
* fraud protection

に関する要求を具体化しています。([EUR-Lex][6])

したがって、

```text
IoT
 │
 ├── CRA
 │
 └── RED
```

のように複数の法令が同じ製品に関係することがあります。

---

# 10. AI ActもSecurityと接続する

AI Actも直接の「Cybersecurity Act」ではありませんが、

* high-risk AI
* robustness
* cybersecurity
* safety
* risk management

などを扱います。

そのため、

```text
AI Act
   │
   ├── Safety
   ├── Security
   ├── Privacy
   └── Fundamental Rights
```

という構造になります。

特に自動運転などでは、

**AI Act + Machinery/Product Safety + CRA + UN R155/R156 + ISO 26262 + ISO/SAE 21434**

という複数レイヤーが重なる可能性があります。

---

# 11. EU法と国際条約はどうつながるか

ここが非常に重要です。

EU法と国際条約は同じ階層ではありません。

```text
             国際法
               │
     ┌─────────┴─────────┐
     ▼                   ▼
国際条約               国際規格
     │                   │
     ▼                   ▼
加盟国の国際法上       技術的基準
の義務
     │                   │
     └─────────┬─────────┘
               ▼
              EU法
               │
               ▼
           EU加盟国法
```

ただし、EU自身が条約の当事者になれる場合や、EU法が国際的義務を履行する場合があります。

---

# 12. サイバー犯罪の国際条約

現在非常に重要なのが、

## Budapest Convention

[Budapest Convention – Council of Europe](https://www.coe.int/en/web/cybercrime/convention-on-cybercrime?utm_source=chatgpt.com)

です。

正式には、

**Convention on Cybercrime (ETS No.185)**

です。

これは、

* 不正アクセス
* コンピュータ関連犯罪
* 電子的証拠
* 捜査
* 国際協力

などを扱います。

2026年現在82 Partiesがあり、国際的なサイバー犯罪協力の中心的条約です。([Portal][7])

特に重要なのは、

> **Cybersecurity engineeringの規格ではなく、Cybercrime + Law Enforcementの条約**

だということです。

---

# 13. さらにUN Convention against Cybercrime

そして新しい大きな動きがあります。

国連の

**United Nations Convention against Cybercrime**

です。

2024年12月24日に採択されました。

ただし、**2026年9月現在まだ発効していません**。

国連条約局によれば、

* Signatories: 81
* Parties: 3
* Not yet in force

です。発効には40件の批准等が必要です。([国際連合条約集][8])

したがって、

```text
Budapest Convention
       │
       │ 現在すでに発効
       ▼
Cybercrime international cooperation

UN Convention against Cybercrime
       │
       │ 2024 adopted
       │ 2026 not yet in force
       ▼
将来のglobal framework
```

という状況です。

---

# 14. Cybersecurityについての国際法はさらに別

ここで「サイバー犯罪」と「国家間サイバー攻撃」を分ける必要があります。

例えば、

* 国家によるサイバー攻撃
* Critical infrastructure attack
* Cyber warfare
* espionage
* sovereignty
* use of force

などです。

これについては、

**国連憲章その他の既存国際法がサイバー空間にも適用される**

という考え方が国際的議論の基本になっています。

UNのOEWGでも、

* international law
* norms of responsible state behaviour
* confidence-building measures
* capacity building

などが議論されています。([UN Web TV][9])

したがって、ここにはまだ、

> 「世界共通のサイバーセキュリティISO規格」

とは全く異なる、**国家間の国際法・外交・安全保障の領域**があります。

---

# 15. 国際規格はどこに入るのか

代表的なものを整理すると、

| 分野                             | 国際規格                          |
| ------------------------------ | ----------------------------- |
| 組織Security                     | **ISO/IEC 27001**             |
| Security controls              | ISO/IEC 27002                 |
| Risk                           | ISO/IEC 27005                 |
| Automotive cybersecurity       | **ISO/SAE 21434**             |
| Automotive cybersecurity audit | ISO/PAS 5112 / ISO/DTS 5112   |
| Automotive software update     | **ISO 24089**                 |
| Functional Safety              | ISO 26262                     |
| Security evaluation            | ISO/IEC 15408 Common Criteria |
| Industrial control             | IEC 62443                     |
| Privacy                        | ISO/IEC 27701                 |

例えばISO/IEC 27001:2022はISMSの要求事項を定めています。([ISO][10])

自動車ではISO/SAE 21434がE/Eシステムのライフサイクル全体のCybersecurity Engineeringを扱います。([ISO][11])

---

# 16. そして自動車ではUNECEが非常に重要

ここが先生のAUTOSAR研究との接点です。

自動車では、

**EU法 → UN Regulation → ISO規格 → AUTOSAR**

という複数階層になります。

代表例が、

## UN Regulation No.155

**Cybersecurity and Cyber Security Management System (CSMS)**

と、

## UN Regulation No.156

**Software Update and Software Update Management System (SUMS)**

です。

UNECE公式資料でもR155/R156が自動車CybersecurityとSoftware Updateについての規則として整理されています。([UNECE][12])

概念的には、

```text
                 EU
                  │
          ┌───────▼───────┐
          │ EU Vehicle Law │
          └───────┬───────┘
                  │
                  ▼
              UNECE WP.29
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
     UN R155              UN R156
     Cybersecurity        Software Update
        │                   │
        ▼                   ▼
 ISO/SAE 21434           ISO 24089
        │                   │
        └─────────┬─────────┘
                  ▼
               AUTOSAR
                  │
                  ▼
          ECU / SW / RTE / OS
```

という関係になります。

UNECE R155/R156は「国際条約」と単純に呼ぶより、**1958 Agreementの枠組みで採択されたUN Regulations**として扱うのが正確です。

---

# 17. したがって「法律→規格」の関係は一方向ではない

ここが、先ほどのAUTOSAR Reference問題とつながります。

例えば、

```text
       EU法
         │
         ▼
      UN R155
         │
         ▼
   ISO/SAE 21434
         │
         ▼
      AUTOSAR
         │
         ▼
      実装
         │
         ▼
    Field Experience
         │
         ▼
     AUTOSAR CR
         │
         ▼
    ISO revision
         │
         ▼
      UN R155
```

という**循環型の知識伝達**が本来望ましい。

ところが現実には、

```text
ISO
 ↓
AUTOSAR
```

は非常に強いのに、

```text
AUTOSAR
 ↓
ISO
 ↓
UNECE
 ↓
EU
```

という逆方向のフィードバックが十分に体系化されていない場合があります。

これは、先ほどの

**「AUTOSAR Reference Linter + Standards Digital Thread」**

という提案と非常に相性がいいテーマです。

---

# 18. WTO/TBTとの関係

さらに、前の議論とも接続できます。

EUの技術規制が、

```text
EU Regulation
      ↓
technical requirement
      ↓
harmonised standard
      ↓
ISO/IEC standard
```

という形で国際規格を利用する場合、WTO TBT Agreementとの関係が問題になります。

特にTBT Agreement 2.4では、関連する国際標準が存在する場合、技術規則の基礎としてそれを使用することが原則とされています。

したがって、

```text
International treaty
       │
       ▼
WTO/TBT
       │
       ▼
EU technical regulation
       │
       ▼
European harmonised standard
       │
       ▼
ISO/IEC / IEC
```

という別の「国際経済法」の軸も存在します。

これはサイバーセキュリティだけでなく、

**AUTOSAR → ISO → UNECE → EU → WTO/TBT**

という、先生が先ほど問題提起された「標準間の整合性」の議論に直接つながります。

---

# 19. 一枚にまとめると

私は研究・講義用には、次の図を基本モデルにすることをお勧めします。

```text
                         ┌─────────────────────┐
                         │   International Law │
                         │ UN Charter / Human  │
                         │ Rights / IHL etc.   │
                         └──────────┬──────────┘
                                    │
                ┌───────────────────┼───────────────────┐
                │                   │                   │
                ▼                   ▼                   ▼
        Budapest Convention   UN Cybercrime       WTO / TBT
        Cybercrime            Convention           Trade
                │                   │                   │
                └───────────────────┼───────────────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │        EU           │
                         │     Legislation     │
                         └──────────┬──────────┘
                                    │
          ┌───────────────┬─────────┼──────────┬─────────────┐
          ▼               ▼         ▼          ▼             ▼
        NIS2             CRA     Cybersecurity CER          GDPR
     Organization      Product     Act       Resilience     Privacy
          │               │         │          │             │
          └───────────────┴─────────┼──────────┴─────────────┘
                                    │
                                    ▼
                         European Standards
                           EN / ETSI / CEN
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ International       │
                         │ Standards           │
                         │ ISO/IEC/IEC/SAE     │
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┼────────────────┐
                    ▼               ▼                ▼
                 27001           21434             24089
                    │               │                │
                    └───────────────┼────────────────┘
                                    ▼
                              UNECE WP.29
                              R155 / R156
                                    │
                                    ▼
                               AUTOSAR
                                    │
                                    ▼
                            Vehicle Software
```

---

## 20. この体系で特に重要な区別

最後に、混同しやすいものを整理するとこうなります。

| もの                               | 法的性質            | 主な役割                 |
| -------------------------------- | --------------- | -------------------- |
| **EU Regulation**                | EU域内で直接適用される法   | CRA, GDPR, DORA等     |
| **EU Directive**                 | 加盟国が国内法化        | NIS2, CER等           |
| **UN Regulation**                | 国際的な車両型式認証の枠組み  | R155/R156            |
| **International Treaty**         | 国家間の法的義務        | Budapest Convention等 |
| **ISO/IEC Standard**             | 原則として任意規格       | 技術的要求・方法             |
| **European Harmonised Standard** | EU法の要求への適合立証に重要 | CRA等との接続             |
| **AUTOSAR**                      | 業界標準            | 実装可能な車載SW仕様          |
| **Company specification**        | 契約・社内規定等        | 実際の製品要求              |

そして非常に重要なのが、

> **「規格に書いてある」ことと「法律で義務である」ことは違う**

という点です。

逆に、

> **「法律に書いてある要求」を、ISO/IEC/EN/AUTOSARなどの技術体系に落とす**

ことで、実装可能な要求になります。

---

### 今回の話を先生のAUTOSAR研究につなげるなら

私は次の**「Cybersecurity Standards Digital Thread」**を作ると非常に面白いと思います。

```text
EU Law
  ↓
NIS2 / CRA / GDPR / sectoral law
  ↓
UNECE R155/R156
  ↓
ISO/SAE 21434 / ISO 24089
  ↓
AUTOSAR
  ↓
ARXML / RTE / OS / COM / SecOC / Crypto
  ↓
ECU implementation
  ↓
Test / Audit / CSMS
  ↓
Field incident / vulnerability
  ↓
AUTOSAR Change Request
  ↓
ISO Change
  ↓
UNECE Change
  ↓
EU regulatory update
```

これを作ると、先ほどの **「AUTOSAR Referenceの誤記・廃止・版違い・独自拡張」**の問題を、単なる文献管理ではなく、

**「法 → 国際規格 → 業界標準 → 実装 → 実績 → 国際規格改訂 → 法規制」**

という**標準化のフィードバック制御系**として研究できます。

これは安全工学でいう **Safety Case / Traceability** にかなり近く、さらにCybersecurityでは **Security Case / Compliance Traceability** に発展させられます。ISO/SAE 21434の監査ガイドもCSMS監査とサプライチェーンを意識した構造になっています。([ISO][13])

特に先生が先ほど問題にされた **「AUTOSARの拡張がISOへ戻っていかない」**という問題を、このDigital Threadの「逆方向Traceability」として定式化すると、かなり研究テーマらしくなります。

[1]: https://eur-lex.europa.eu/eli/dir/2022/2555?utm_source=chatgpt.com "EUR-Lex - 02022L2555-20221227 - EN - EUR-Lex"
[2]: https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng?utm_source=chatgpt.com "Regulation - 2024/2847 - EN - EUR-Lex"
[3]: https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A02019R0881-20250204&utm_source=chatgpt.com "EUR-Lex - 02019R0881-20250204 - MT - EUR-Lex"
[4]: https://eur-lex.europa.eu/eli/dir/2022/2557/oj/eng?utm_source=chatgpt.com "Directive - 2022/2557 - EN - CER - EUR-Lex"
[5]: https://eur-lex.europa.eu/eli/dir/2022/2557/oj?utm_source=chatgpt.com "Directive - 2022/2557 - EN - CER - EUR-Lex"
[6]: https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A32022R0030&utm_source=chatgpt.com "Delegated regulation - 2022/30 - EN - EUR-Lex"
[7]: https://www.coe.int/en/web/cybercrime/the-budapest-convention?utm_source=chatgpt.com "About the Convention - Cybercrime"
[8]: https://treaties.un.org/Pages/ViewDetails.aspx?chapter=18&clang=_en&mtdsg_no=XVIII-16&src=TREATY&utm_source=chatgpt.com "UNTC"
[9]: https://webtv.un.org/en/asset/k1w/k1w7hi4w10?utm_source=chatgpt.com "(3rd meeting) Open-ended working group on Information and Communication Technology (ICT) - Tenth Substantive Session (17-21 February 2025) | UN Web TV"
[10]: https://www.iso.org/standard/27001?km_404=all&utm_source=chatgpt.com "ISO/IEC 27001:2022 - Information security management systems"
[11]: https://www.iso.org/standard/70918.html?browse=tc&utm_source=chatgpt.com "ISO/SAE 21434:2021 - Road vehicles — Cybersecurity engineering"
[12]: https://unece.org/transport/road-transport/reference-documents?utm_source=chatgpt.com "Reference documents | UNECE"
[13]: https://www.iso.org/standard/80840.html?utm_source=chatgpt.com "ISO/PAS 5112:2022 - Road vehicles — Guidelines for auditing cybersecurity engineering"
