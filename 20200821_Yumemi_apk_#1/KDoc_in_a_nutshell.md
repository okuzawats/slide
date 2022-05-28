---
marp: true
theme: uncover
size: 16:9
paginate: true
headingDivider: 2
header: KDoc in a nutshell
footer: © 2020 okuzawats
---

# KDoc in a nutshell
okuzawats
YUMEMI.apk #1
2020/08/21
converted to markdown format 2022/05/28

<!--
_class: lead
_paginate: false
_header: ""
-->

## 自己紹介

- okuzawats
  - Twitter: okuzawats
  - GitHub: okuzawats
- Androidアプリエンジニア @ フラー株式会社
  - 柏の葉キャンパス／新潟
  - We are hiring!🙌

![bg right:50%](img/okuzawats.png)

## KDoc is 何？

## KDoc is 何？

- ドキュメンテーションコメントを書くやつ✍️
  - JavadocのKotlin版
- Markdown対応🚀
- Dokkaによるドキュメントの自動生成🤖
  - 自分はやったことないです

##

```kotlin
/**
 * バージョン番号を表すクラス
 *
 * [fromRawString]を使って、x.y.z形式の文字列からインスタンスを生成します。
 * [toString]すると[majorVersion].[minorVersion].[patchVersion]形式で文字列にしてくれます。
 * [Comparable]を実装しているので、[Version]同士の比較が可能です。
 * この時、[majorVersion]、[minorVersion]、[patchVersion]の順に比較を行います。
 *
 * @property majorVersion メジャーバージョン
 * @property minorVersion マイナーバージョン
 * @property patchVersion パッチバージョン
 */
class Version private constructor(
    private val majorVersion: Int,
    private val minorVersion: Int,
    private val patchVersion: Int
): Comparable<Version> {
```

##

書き方
👇
https://kotlinlang.org/docs/reference/kotlin-doc.html

## KDocを何で書くのか

- 学習コストの低減📉
  - 自然言語で書けるので学習コストがあまりかからない
  - 新しくプロジェクトに入ってくる人
  - 一ヶ月後の自分
- 設計品質の向上📈
  - 考慮漏れに気付くことができる
  - 設計の問題をあぶり出すことができる

## KDocに何を書くのか

- 仕様📄
- コードをどうやって使うのか✍️
- なんでそうなっているのか🧐
  - 👉コードを使う人がそのコードをどのように使うのかわかるように書く
  - 👉ドキュメンテーションコメントに従った実装を行う

## KDocに何を書かないのか

- 処理内容の翻訳👻
  - 読めばわかることをわざわざ書く必要はない
  - 邪魔になる
- Privateなメソッドに対するドキュメンテーションコメント🤫
  - 外部に公開する物についてのみ書けば良い
  - Privateなメソッドは普通のコメントで良い

##

まとめ
👇
ドキュメンテーションコメントを書こう

## 参考文献

- Kotlin. (N.D.). Documenting Kotlin Code. Retrieved from https://kotlinlang.org/docs/reference/kotlin-doc.html
- 佐藤竜一. (2009). エンジニアのためのJavadoc再入門講座. 翔泳社.
