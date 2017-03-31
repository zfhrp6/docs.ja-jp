---
title: "文字列補間 | C#"
description: "C# 6 の文字列補間の動作について"
keywords: ".NET、.NET Core、C#、文字列"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 41afad1c1148319eb8d7d1c3066424eea431649d
ms.lasthandoff: 03/13/2017

---

# <a name="string-interpolation-in-c"></a>C における文字列補間# #

文字列補間は、文字列内のプレースホルダーを文字列変数の値によって置き換える方法です。 C# 6 より前は、これは `System.String.Format` を使用して行われました。 それでも動作しますが、番号付きのプレースホルダーを使用するため読みにくく冗長になります。

他のプログラミング言語ではすでに、文字列補間の機能を組み込んでいました。 たとえば PHP では次のようになります。

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

C# 6 でついに、この形式の文字列補間ができるようになりました。 文字列の前に `$` を使用して、それらの値の変数または式に置き換えると示すことができます。

## <a name="prerequisites"></a>必須コンポーネント
お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。 インストールの指示については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。
このアプリケーションは、Windows、Ubuntu Linux、macOS または Docker コンテナーで実行できます。 お好みのコード エディターをインストールしてください。 次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。 しかし、他の使い慣れたツールを使用しても構いません。

## <a name="create-the-application"></a>アプリケーションを作成する

すべてのツールをインストールしたら、新しい .NET Core アプリケーションを作成します。 コマンド ライン ジェネレーターを使用するには、`interpolated` などプロジェクトのディレクトリを作成し、好みのシェルで次のコマンドを実行します。

```
dotnet new console
```

このコマンドで、プロジェクト ファイル *interpolated.csproj* およびソース コード ファイル *Program.cs* とともに、必要最低限の .NET Core プロジェクトが作成されます。 `dotnet restore` を実行して、このプロジェクトのコンパイルに必要な依存関係を復元する必要があります。

プログラムを実行するには `dotnet run` を使用します。 コンソールに "Hello, World" という出力が表示されます。

## <a name="intro-to-string-interpolation"></a>文字列補間の概要

`System.String.Format` を使用して、文字列で、その文字列に続くパラメーターで置き換えられる "プレースホルダー" を指定します。 たとえば、次のようになります。

[!code-csharp[String.Format の例](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

これにより "My name is Matt Groves" と出力されます。

C# 6 では `String.Format` を使用する代わりに `$` 記号とともに付加して文字列で直接変数を使用することにより、補間文字列を定義します。 たとえば、次のようになります。

[!code-csharp[補間の例](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

使用するのは変数のみとは限りません。 角かっこ内で任意の式を使用することができます。 たとえば、次のようになります。

[!code-csharp[補間の式の例](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

この出力は以下のようになります。

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a>文字列補間の動作

背後では、この文字列補間の構文はコンパイラによって String.Format に変換されます。 そのため、[前に String.Format で実行したのと同様のこと](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx)ができます。

たとえば、パディングと数値の書式設定を追加できます。

[!code-csharp[補間の書式設定の例](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

上記はこのような出力となります。

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

変数名が見つからない場合、コンパイル時エラーが生成されます。

たとえば、次のようになります。

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

これをコンパイルすると、エラーが発生します。
 
* `Cannot use local variable 'adj' before it is declared` - 変数 `adj` が補間された文字列の*後までに*宣言されなかった。
* `The name 'otheranimal' does not exist in the current context` - `otheranimal` と呼ばれる変数が宣言すらされていない。

## <a name="localization-and-internationalization"></a>ローカリゼーションと国際化

補間された文字列は `IFormattable` と `FormattableString` をサポートしており、国際化するのに役立ちます。

既定では、補間された文字列は現在のカルチャを使用します。 別のカルチャを使用するには、`IFormattable` としてキャストします。

たとえば、次のようになります。

[!code-csharp[補間の国際化の例](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a>まとめ 

このチュートリアルでは、C# 6 の文字列補間機能の使用方法について説明しました。 これは基本的に、シンプルな `String.Format` ステートメントを書く簡潔な方法で、より高度な使い方をするには注意が必要です。

