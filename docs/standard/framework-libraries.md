---
title: "フレームワーク ライブラリ"
description: "フレームワーク ライブラリ"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
translationtype: Human Translation
ms.sourcegitcommit: 093b852fe1ed2307ebce914381fe47388b435c95
ms.openlocfilehash: 7283ed099cefa4b0e137869724f8e87dda0d451a

---

# <a name="framework-libraries"></a>フレームワーク ライブラリ

.NET には、基底クラス ライブラリ (コア セット) またはフレームワーク クラス ライブラリ (完全なセット) と呼ばれるクラス ライブラリの包括的な標準セットがあります。 これらのライブラリは、多くの汎用およびアプリ固有の型、アルゴリズムおよびユーティリティの機能の実装を提供します。 商用ライブラリとコミュニティ ライブラリはどちらもフレームワーク クラス ライブラリの上に構築され、コンピューティング タスクの広範なセット用に使いやすい市販ライブラリを提供します。

これらのライブラリのサブセットには、各 .NET 実装が提供されます。 基底クラス ライブラリ (BCL) API には、任意の .NET 実装が想定されています。これは、開発者がそれらを必要としていることと、よく使われるライブラリでそれらを実行する必要があるという 2 つの理由からです。 ASP.NET などの BCL 上のアプリ固有のライブラリは、すべての .NET 実装で使用できません。

## <a name="base-class-libraries"></a>基底クラス ライブラリ

BCL は最も基本的な型およびユーティリティの機能を提供し、他のすべての .NET クラス ライブラリの基本となります。 これらは、任意のワークロードに偏ることなく、非常に汎用的な実装を提供することを目的としています。 アプリは、高スループットよりも低待機時間、低い CPU 使用率よりも低いメモリ使用率のように、特定のポリシーを選ぶ場合があるため、パフォーマンスは常に重要な考慮事項です。 これらのライブラリは、一般に、高パフォーマンスになることを意図しており、これらさまざまなパフォーマンス上の問題に応じて、妥協案を採用します。 ほとんどのアプリでは、この方法は成功しています。

## <a name="primitive-types"></a>プリミティブ型

.NET には、すべてのプログラムで (さまざまな程度で) 使用されるプリミティブ型のセットが含まれています。 これらの型には、数値、文字列、バイト、および任意のオブジェクトなどのデータが含まれています。 C# 言語には、これらの型のキーワードが含まれています。 これらの型のサンプル セットを、一致する C# キーワードとともに以下に示します。

*   [System.Object](https://msdn.microsoft.com/library/system.object.aspx) ([object](https://msdn.microsoft.com/library/9kkx3h3c.aspx)): CLR 型システムの基底クラス。 型階層のルートです。
*   [System.Int16](https://msdn.microsoft.com/library/system.int16.aspx) ([short](https://msdn.microsoft.com/library/ybs77ex4.aspx)): 16 ビットの符号付き整数型。 符号なしの [UInt16](https://msdn.microsoft.com/library/system.uint16.aspx) も存在します。
*   [System.Int32](https://msdn.microsoft.com/library/system.int32.aspx) ([int](https://msdn.microsoft.com/library/5kzh1b5w.aspx)): 32 ビットの符号付き整数型。 符号なしの [UInt32](https://msdn.microsoft.com/library/x0sksh43.aspx) も存在します。
*   [System.Single](https://msdn.microsoft.com/library/system.single.aspx) ([float](https://msdn.microsoft.com/library/b1e65aza.aspx)): 32 ビット浮動小数点型。
*   [System.Decimal](https://msdn.microsoft.com/library/system.decimal.aspx) ([decimal](https://msdn.microsoft.com/library/364x0z75.aspx)): 128 ビットの 10 進数型。
*   [System.Byte](https://msdn.microsoft.com/library/system.byte.aspx) ([byte](https://msdn.microsoft.com/library/5bdb6693.aspx)): メモリのバイトを表す符号なし 8 ビット整数。
*   [System.Boolean](https://msdn.microsoft.com/library/system.boolean.aspx) ([bool](https://msdn.microsoft.com/library/c8f5xwh7.aspx)): 'true' または 'false' を表すブール型。
*   [System.Char](https://msdn.microsoft.com/library/system.char.aspx) ([char](https://msdn.microsoft.com/library/x9h8tsay.aspx)): Unicode 文字を表す 16 ビットの数値型。
*   [System.String](https://msdn.microsoft.com/library/system.string.aspx) ([string](https://msdn.microsoft.com/library/362314fe.aspx)): 一連の文字を表します。 `char[]` とは異なりますが、`string` で各 `char` にインデックスを付けることができます。

## <a name="data-structures"></a>データ構造

.NET には、ほとんどの .NET アプリの主力となるデータ構造体のセットが含まれています。 これらはほとんどがコレクションですが、その他の型も含まれています。

*   [Array](https://msdn.microsoft.com/library/system.array.aspx): インデックスを使用してアクセスできる、厳密に型指定されたオブジェクトの配列を表します。 その構造ごとの固定サイズがあります。
*   [List](https://msdn.microsoft.com/library/6sh2ey19.aspx): インデックスを使用してアクセスできる、厳密に型指定されたオブジェクトのリストを表します。 必要に応じてサイズを自動調整します。
*   [Dictionary](https://msdn.microsoft.com/library/xfhwa508.aspx): -キーによってインデックスが作成される値のコレクションを表します。 値は、キーを使用してアクセスできます。 必要に応じてサイズを自動調整します。
*   [Uri](https://msdn.microsoft.com/library/system.uri.aspx): オブジェクト表現を可能にし、URI (Uniform Resource Identifier) の一部へ簡単にアクセスできるようにします。
*   [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx): 通常、日付や時刻として表現される瞬間を表します。

## <a name="utility-apis"></a>ユーティリティ API

.NET には多くの重要なタスクの機能を提供するユーティリティ API のセットが含まれています。

*   [HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient.aspx): URI で識別されるリソースに HTTP 要求を送信し、そのリソースから HTTP 応答を受信するための基底クラスを提供する API です。
*   [XDocument](https://msdn.microsoft.com/library/system.xml.linq.xdocument.aspx): LINQ を使用して XML ドキュメントのロードと照会をするための API です。
*   [StreamReader](https://msdn.microsoft.com/library/system.io.streamreader.aspx): ファイル ([StreamWriter](https://msdn.microsoft.com/library/system.io.stringwriter.aspx)) を読み取るための API です。ファイルの書き込みに使用できます。

## <a name="appmodel-apis"></a>アプリ モデル API

.NET で使用できる多くのアプリ モデルが、複数の企業から提供されています。

*   [ASP.NET](http://asp.net): Web サイトとサービスを構築するための Web フレームワークを提供します。 Windows、Linux、macOS でサポートされます (ASP.NET のバージョンによって異なります)。



<!--HONumber=Nov16_HO1-->


