---
title: "7.1 c# の新機能"
description: "7.1 c# の新機能の概要。"
keywords: "C# 言語のデザイン、7.1、Visual Studio 2017、"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a>7.1 c# の新機能

C# 7.1 は、c# 言語に最初のポイント リリースです。 言語の増加のリリース パターンをマークします。 使用できますの新機能、理想的には各新機能の準備ができたとき。 C# 7.1 は、コンパイラ、言語の指定したバージョンと一致するを構成する機能を追加します。 言語バージョンにアップグレードする意思決定からツールをアップグレードするかどうかを分離することができます。

C# 7.1 を追加、[バージョンの言語の選択](#language-version-selection)、3 つの新しい言語機能および新しいコンパイラの動作の構成要素。

このリリースの新しい言語機能は次のとおりです。

* [`async``Main`メソッド](#async-main)
  - アプリケーションのエントリ ポイントを持つことができます、`async`修飾子です。
* [`default`リテラル式](#default-literal-expressions)
  - 対象の型を推論できる場合は、既定値の式の既定のリテラル式を使用できます。
* [推論されたタプル要素の名前](#inferred-tuple-element-names)
  - タプル要素の名前は、多くの場合の組の初期化から推論することができます。

コンパイラが 2 つのオプションには、最後に、`/refout`と`/refonly`を制御する[参照アセンブリの生成](#reference-assembly-generation)です。

## <a name="language-version-selection"></a>バージョンの言語の選択

C# コンパイラでは、c# 7.1 以降では、Visual Studio 2017 バージョン 15.3、または .NET Core SDK 2.0 をサポートします。 ただし、7.1 機能は、既定でオフにされます。 7.1 機能を有効にするには、プロジェクトの言語バージョンの設定を変更する必要があります。

Visual Studio で、ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし、選択**プロパティ**です。 選択、**ビルド** タブを選択、**詳細**ボタンをクリックします。 ドロップダウンで、次のように選択します。 **c# 最新のマイナー バージョン (最新)**、または特定のバージョン**c# 7.1**イメージ次に示すようにします。 `latest`値は、現在のコンピューターに最新のマイナー バージョンを使用することを意味します。 `C# 7.1`は最新のマイナー バージョンがリリースされた後でも、c# 7.1 を使用することを意味します。

![言語バージョンを設定](./media/csharp-7-1/advanced-build-settings.png)

代わりに、"csproj"ファイルを編集し、追加または次の行を変更することができます。

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Visual Studio IDE を使用して、csproj ファイルを更新する場合は、各ビルド構成に対して別々 のノードが作成されます。 通常値を設定する同じすべてのビルド構成が、各ビルド構成に対して明示的に設定またはこの設定を変更するときに、「すべての構成」を選択する必要があります。 Csproj ファイルで、次が表示されます。

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

有効な設定、`LangVersion`要素は。

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

特殊な文字列`default`と`latest`それぞれ、ビルド コンピューターにインストールされている最新のメジャーおよびマイナーの言語バージョンに解決します。

この設定は、プロジェクトの新しい言語機能を組み込むを選択することから、開発環境で新しいバージョンの SDK とツールのインストールを切り離します。 ビルド コンピューターには、最新の SDK とツールをインストールできます。 各プロジェクトは、言語の特定バージョンのビルドを使用して構成できます。

## <a name="async-main"></a>非同期のメイン

*Async メイン*メソッドでは、使用することができます`await`で、`Main`メソッドです。
以前を記述する必要があります。

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

今すぐに記述できます。

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

宣言するかどうか、プログラムは終了コードを返さない、`Main`を返すメソッド、 <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

詳細を読み取ることができますの詳細について、 [async メイン](../programming-guide/main-and-command-args/index.md)プログラミング ガイドの「します。

## <a name="default-literal-expressions"></a>既定のリテラル式

既定のリテラル式は、既定値の式の拡張版です。
これらの式は、既定値に変数を初期化します。 ここで以前記述できます。

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

これで、初期化の右側にある型を省略できます。

```csharp
Func<string, bool> whereClause = default;
```

C# プログラミング ガイドのトピックでこの機能強化について詳細にについては、[値式の既定](../programming-guide/statements-expressions-operators/default-value-expressions.md)です。

この機能強化にもいくつかの解析規則の変更、 [default キーワード](../language-reference/keywords/default.md)です。

## <a name="inferred-tuple-element-names"></a>推論されたタプル要素の名前

この機能は、c# 7.0 で導入された組の機能の小さい拡張機能です。 何度も組を初期化するときに、代入の右側にあるに使用される変数は、タプル要素の名前と同じ。

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

タプル要素の名前は、c# 7.1 内の組を初期化するために使用される変数から推論することができます。

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

この機能についての詳細については、[組](../tuples.md)トピックです。

## <a name="reference-assembly-generation"></a>参照アセンブリの生成

生成する 2 つのコンパイラ オプションがある*参照専用のアセンブリ*: [/refout](../language-reference/compiler-options/refout-compiler-option.md)と[/refonly](../language-reference/compiler-options/refonly-compiler-option.md)です。
リンク先のトピックでは、これらのオプションと詳細の参照アセンブリを説明します。
