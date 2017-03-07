---
title: ".NET アセンブリ ファイルの形式"
description: ".NET アセンブリ ファイルの形式"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ec5619e164be44205060d790ba1dc66e261faf92
ms.lasthandoff: 03/02/2017

---

# <a name="net-assembly-file-format"></a>.NET アセンブリ ファイルの形式

.NET プラットフォームでは、.NET プログラムの完全な記述と格納に使用するバイナリ ファイル形式として、"アセンブリ" が定義されています。 アセンブリは、プログラム自体と同様に従属ライブラリにも使用されます。 .NET プログラムは、適切な .NET ランタイム以外の成果物を必要とせずに、1 つ以上のアセンブリとして実行できます。 ネイティブの依存関係 (オペレーティング システム API を含む) は別の考慮事項であり、.NET アセンブリの形式には存在しません。ただし、この形式を使用して記述されることがあります (たとえば WinRT)。

> 各 CLI コンポーネントには、そのコンポーネントに固有の宣言、実装、参照のためのメタデータが含まれます。 そのため、コンポーネント固有のメタデータはコンポーネント メタデータと呼ばれ、結果として得られるコンポーネントは自己記述と呼ばれます (ECMA 335 I.9.1 のコンポーネントおよびアセンブリの仕様)。

この形式は ECMA 335 として仕様が完全に指定され、標準化されています。 すべての .NET コンパイラとランタイムが、この形式を使用します。 ドキュメント化された、更新が頻繁でないバイナリ形式の存在は、相互運用性の面で大きなメリットであり、ほぼ間違いなく必要条件になっています。 この形式が最後に実質的な方法で更新されたのは 2005 年 (.NET 2.0) で、ジェネリックやプロセッサ アーキテクチャに対応するための変更が行われました。

この形式は CPU や OS に依存しません。 多くのチップや CPU を対象にした .NET ランタイムの一部として使用されています。 この形式自体は Windows で開発された経緯がありますが、任意のオペレーティング システムに実装できます。 OS の相互運用性にかかわる、この形式の最も重要なオプションと言えるのは、ほとんどの値をリトル エンディアン形式で格納することです。 コンピューターのポインター サイズ (32 ビット、64 ビットなど) に対する特定の関係はありません。

.NET アセンブリ形式は、特定のプログラムまたはライブラリの構造をとてもわかりやすく記述することもできます。 アセンブリの内部コンポーネント、具体的にはアセンブリ参照や定義済みの型とそれらの内部構造を記述します。 ツールまたは API で表示のためにこの情報の読み取り、処理を行ったり、プログラムによる決定を行うことができます。

## <a name="format"></a>形式

.NET バイナリ形式は、Windows [PE ファイル](http://en.wikipedia.org/wiki/Portable_Executable)形式に基づいています。 実際には、.NET クラス ライブラリは Windows PE に準拠し、Windows ダイナミック リンク ライブラリ (DLL) またはアプリケーション実行可能ファイル (EXE) のように見えます。 これは Windows 上でとても便利な特性であり、ネイティブな実行可能バイナリのように偽装して、実行可能バイナリと同じように扱うことができます (OS ロード、PE ツールなど)。

![アセンブリ ヘッダー](./media/assembly-format/assembly-headers.png)

ECMA 335 II.25.1 のランタイム ファイル形式の構造に基づくアセンブリ ヘッダー。

## <a name="processing-the-assemblies"></a>アセンブリの処理

アセンブリを処理するツールや API を記述することができます。 アセンブリ情報を使用して、実行時のプログラムによる決定、アセンブリの書き換え、エディターでの API IntelliSense の提供、ドキュメントの生成ができます。 [System.Reflection](https://msdn.microsoft.com/library/system.reflection.aspx) と [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) は、この目的によく使われるツールの好例です。

