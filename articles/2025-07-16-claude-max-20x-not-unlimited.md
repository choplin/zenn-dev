---
title: "Claude Max 20xは「使い放題」プランではない"
emoji: "🚦"
type: "tech"
topics: ["claude", "ai", "llm", "anthropic"]
published: true
published_at: "2025-07-16"
---

ここ数日、Claude Max 20xプランを使っていて、以前より頻繁に利用制限にかかるようになったと感じます。「20xだから実質使い放題」と考えており、実際に6月はその感覚に近かったのですが、そうではなかったようです。

[ccusage](https://github.com/ryoppippi/ccusage)（Claude使用量を確認するツール）で実際の使用状況を確認してみると、6月と7月で明らかな違いが見られました。

**2025年6月16日時点の使用状況：**
![6月の使用状況](/images/2025-07-16-claude-max-20x-not-unlimited/ccusage-2025-06-16.png)

**2025年7月15日時点の使用状況：**
![7月の使用状況](/images/2025-07-16-claude-max-20x-not-unlimited/ccusage-2025-07-15.png)

どちらも毎セッション（セッションについては後述）制限に達するまで使用していたのですが、6月の$694に対して、7月は$464しか利用できていません。トークン量をみても明らかに減少しています。

公式ドキュメントをよく読んでみると、Claude Maxは決して「使い放題」プランではないことがわかります。Anthropicの公式ヘルプセンターの情報をもとに、Claude Max 20xの実際の制限について見ていきます。

## 「20x」が意味するもの

まず、Claude Maxプランには2つのティアがあります：

- **Max 5x Pro**（月額$100）：Proプランの5倍の使用量
- **Max 20x Pro**（月額$200）：Proプランの20倍の使用量

この「20x」について、[Anthropicの公式ヘルプセンター](https://support.anthropic.com/en/articles/11014257-about-claude-s-max-plan-usage)では以下のように説明されています：

> If your conversations are relatively short, with the Max plan at 5x more usage, you can expect to send at least 225 messages every 5 hours, and with the Max plan at 20x more usage, at least 900 messages every 5 hours

会話が比較的短い場合、Max 5xプランでは5時間ごとに最低225メッセージ、Max 20xプランでは最低900メッセージを送信できると記載されています。さらに続けて次のような説明があります：

> often more depending on message length, conversation length, and Claude's current capacity. We will provide a warning when you have a limited number of messages remaining.

つまり、メッセージの長さや会話の長さ、そしてClaudeの現在のキャパシティによって、実際に送信できるメッセージ数は変動します。重要なのは、「現在のキャパシティ」という要因が含まれている点です。同じ使い方をしても、月によって利用可能な量が変わる可能性があります。

## 5時間ごとのリセットの仕組み

Claude Maxの利用制限は「セッション」という単位で管理されています：

- メッセージ制限は**5時間ごとにリセット**される
- この5時間の区切りを「セッション」と呼ぶ
- セッションは最初のメッセージ送信時から開始される

例えば、午前9時に最初のメッセージを送信すると、午後2時までが1セッションとなり、その間に900メッセージ程度が送信できます。

## 月間50セッションの制限

さらに注意が必要なのが、月間のセッション数に関する制限です：

> Please note that if you exceed 50 sessions per month, we may limit your access to Claude.

月間50セッションを超えると、アクセスが制限される可能性があります。"may"という表現からも分かるように、Anthropicはこの制限を柔軟に運用する方針のようです。公式では次のように説明されています：

> The 50 sessions guideline is not a strict cut-off – rather, it's a flexible benchmark that allows us to limit excessive usage case-by-case and only when necessary, to ensure fair access for all Max subscribers.

定額プランとして提供する上で、料金と実際の使用量のバランスを取るため、50セッションという基準を設定しているようです。これは厳密な制限ではなく「目安」として運用され、全体的な使用状況に応じてAnthropic側で調整される仕組みになっています。

50セッションを月30日で割ると、1日あたり約1.6セッションになります。平日のみ使用する場合でも1日2〜3セッション程度で上限に達するため、アクティブユーザーにとっては注意が必要な数字です。

## 効率的な利用へのtips

公式ドキュメントでは、使用量を最大化するために以下のポイントが有効であるとされています。

1. **新しいトピックごとに新しい会話を開始**する
2. **関連する質問はまとめて**送信する
3. **使用量の警告に注意**を払う
4. **5時間のリセット時間を意識**して作業を計画する
5. **添付ファイルのサイズに気を配る**

また[Usage Limit Best Practices](https://support.anthropic.com/en/articles/9797557-usage-limit-best-practices)も参考になります。

## まとめ

Claude Max 20xは確かに大幅に拡張された使用量を提供しますが、「使い放題」ではありません。月額$200という価格設定も、この制限を前提としたものだと理解できます。

アクティブに使用するユーザーにとっても十分な容量が提供されていますが、「無制限に使える」という期待を持つと、思わぬところで制限に直面することがあります。毎日数時間程度の利用であれば十分な容量ですが、終日Claude Codeで作業を行う場合は制限を意識した使い方が必要になるでしょう。

とはいえ、これだけの性能を持つAIを月額$200の定額で利用できるのは破格であり、Anthropicには感謝しかありません。公式ドキュメントの内容を正しく理解した上で、効率的に活用していきましょう。
