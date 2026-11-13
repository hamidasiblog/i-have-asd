# i-have-asd

**自閉スペクトラムの読み手のための、見通しのきく出力。次に何が来るかが見え、切り替えはいつも同じ知らせ方で起きます。**

[English](../../README.md)

> **医療の助言ではありません。** これは AI コーディングアシスタントの「返し方」を整えるスキルです。診断・治療・療法・医療機器のいずれでもなく、臨床で試したものでもありません。自閉スペクトラムの人は一人ひとり違い、ここに書いたことは特定の誰かを説明するものではありません。使うのに診断は要りません。

## 何をするか

オンにすると、AI は返事の形をその場で変えるのをやめ、4つの決まった型と、文字どおりの言葉を使います。

| 型 | AI がすること |
| --- | --- |
| 1. 返事の決まった枠 | どの返事も同じ4つの部分を同じ順で：`Now`（今）／`This reply`（この返事の中身）／本文／`Next`（次）。 |
| 2. 先に見通し | 何かが起きる前に、目的・手順の数・変わることと変わらないことを書く。量は具体的な単位で。 |
| 3. 変更の決まった知らせ | 計画が変わるとき：`Change`／`Reason`／`Was`／`Now`／`Unchanged`。前と後を並べて見せる。黙って変えない。 |
| 4. 切り替えの決まった型 | 話題を移るとき：`Closing: … — 状態`、そのあと `Switching to: …`。途中で出た別件は飛びつかず「置いておく」。 |

加えて：

- **言葉**：文字どおり、具体的に。比喩・慣用句・皮肉を使わない。1つのものには1つの名前。決まりは理由と一緒に書く。
- **質問**：1つの返事に1つ。選択肢を2つか3つ出し、おすすめに印を付ける。急がないときは「今決めなくてよい」と書く。
- **見通しはきくが、固くはない**：読み手はどの型も変えられる。変えた型が、そのあとの決まった型になる。

全文は [skills/i-have-asd/SKILL.md](../../skills/i-have-asd/SKILL.md) の1枚です。決まりはここにしかありません。

## オンとオフ

設定はありません。オンかオフだけです。

- `/i-have-asd` でそのセッションをオンにする。
- `stop asd mode`（または `normal mode`）でオフにする。
- いつもオンにする：空の印のファイル `~/.claude/.i-have-asd-always` を作る。消せば元に戻る。

導入は [INSTALL.md](../../INSTALL.md)。

## 出どころ

決まりは「AI がどう書くか」についての設計上の選択です。下の資料を参考にしていますが、臨床の推奨をそのまま持ってきたものではなく、どの資料も AI アシスタントを調べたものではありません。

書いたとき（2026-11-13）に実際に開いて読めたページだけを並べています。

### NICE ガイドライン CG142

Autism spectrum disorder in adults: diagnosis and management（2012年6月27日公開、2021年6月14日最終更新）
https://www.nice.org.uk/guidance/cg142/chapter/Recommendations

| 推奨 | 書いてあること | 使った所 |
| --- | --- | --- |
| 1.3.2 | ケアについて話し合うとき、"importance of predictability, clarity, structure and routine for autistic people" と "increased propensity for elevated anxiety about decision-making" を考慮に入れる。 | 型1〜4、質問 |
| 1.6.3 | 適応として "a more concrete and structured approach with a greater use of written and visual information"、"making rules explicit and explaining their context"、"using plain English and avoiding excessive use of metaphor, ambiguity and hypothetical situations"、"offering regular breaks"。 | 言葉、休み |
| 1.8.14 | 職員は "be consistent and predictable, but with some flexibility to allow change and choice"。 | 「見通しはきくが、固くはない」 |
| 1.2.2 | 評価を検討するきっかけとなる特徴の1つに "stereotypic (rigid and repetitive) behaviours, resistance to change or restricted interests"。 | 型3・4 |

これらの推奨は保健・福祉の職員に向けて書かれたものです。1.6.3 は併存する精神疾患への認知・行動的介入の適応について、1.8.14 は入所ケアについての推奨です。このスキルが借りているのは伝え方の工夫だけで、介入ではありません。

### 国立障害者リハビリテーションセンター 発達障害情報・支援センター

- 各障害の定義：https://www.rehab.go.jp/ddis/understand/definition
- 支援方法の学習：https://www.rehab.go.jp/ddis/howto/study/support
- 支援原則の学習：https://www.rehab.go.jp/ddis/howto/study/principle
- 自閉スペクトラム症（発達障害情報のポータルサイト。センターの定義のページからリンクされている）：https://hattatsu.go.jp/supporter/healthcare_health/about-asd-2/

ページに書いてあること：

- 手順を番号を振って手順書に整理すること、カレンダーや予定表で先の見通しをもてるようにすることが、有効な場合が多いとされている。いつもと違う変更は、同じ紙の上で修正する、別の紙に新しく示す、といった形で視覚的に示すとわかりやすい。→ 型2・3
- 広汎性発達障害の特性をもつ人の多くは、聴覚的な情報より視覚的な情報のほうが理解しやすいといわれている。→ 書いた構造で示す
- 抽象的な指示、暗黙の了解、比喩的な表現、皮肉、冗談などの理解が困難な場合がある。できるだけ具体的な表現で伝える。ルールをきちんと説明する。→ 言葉
- 自己決定では、いくつか選択肢を設定してその中から選ぶことから始め、選択肢ごとのメリットとリスクを明示する。→ 質問
- ポータルのページには、（幼児期の記述として）初めてのことや予定の変更を好まないことがあること、成人後に仕事が臨機応変にこなせない悩みをもつことがあることが書かれている。→ 型2〜4

センターのページは、主に子どもへの支援と発達障害全般について書かれています。同じ考えを大人向けの文字の出力に当てはめたのは、このスキルの設計上の選択です。

## あえてしないこと

- 読み手を評価・診断・説明しない。
- 読み手の伝え方を変えさせようとしない。
- 診断・薬・療法について助言しない。聞かれたら断るように AI に指示している。
- 読み手が言い出さないかぎり、自閉スペクトラムに触れない。

## 手本

[ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd)（Ayoub Ghriss、MIT）を手本にしています。リポジトリの構成、`SessionStart` フック、Pi/OMP のエクステンション、OpenCode のプラグイン、各ランタイムのマニフェストはそこから持ってきて直したもので、元の著作権表示は [LICENSE](../../LICENSE) と各ファイルに残しています。`SKILL.md` の決まりは新しく書いたものです。

このリポジトリは元の作者とは関係がなく、作者が確かめたものでもありません。

## ライセンス

[MIT](../../LICENSE)
