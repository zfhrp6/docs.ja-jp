---
title: "言語機能とライブラリの型間のリレーションシップ |Microsoft ドキュメント"
description: "言語機能は、多くの場合、ライブラリの型の実装に依存します。 そのリレーションシップを理解します。"
keywords: "C# 言語のデザイン、標準ライブラリ"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 93fd26a72743fcf45df3904cb8d0c787d8a228a8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="relationships-between-language-features-and-library-types"></a>言語機能とライブラリの型間のリレーションシップ

C# 言語の定義には、それらの型の特定の種類と特定のアクセス可能なメンバーの設定を標準ライブラリが必要です。 コンパイラは、多くのさまざまな言語機能のこれらの必要な型およびメンバーを使用するコードを生成します。 必要に応じて、ここでその型またはメンバーがまだ展開されていません環境を作成する場合、言語の新しいバージョンのために必要な型が含まれている NuGet パッケージがあります。

この標準ライブラリの機能に対する依存関係は、最初のバージョンから、c# 言語の一部をされました。 そのバージョンでは、例が含まれます。

* <xref:System.Exception>-すべてのコンパイラによって生成された例外のために使用します。
* <xref:System.String>-c#`string`型は、シノニムの<xref:System.String>します。
* <xref:System.Int32>シノニム`int`です。

その最初のバージョンが単純な: コンパイラおよび標準ライブラリは、まとめて配布され、それぞれのバージョンを 1 つだけが発生しました。

以降のバージョンの c# は、依存関係に、新しい型またはメンバーを追加した場合があります。 例: <xref:System.Runtime.CompilerServices.INotifyCompletion>、<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>と<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>です。 C# 7.0 の依存関係を追加することでこれが引き続き<xref:System.ValueTuple>を実装する、[組](../tuples.md)言語機能。

言語設計チームが、型および準拠している標準ライブラリで必要なメンバーの表層領域を最小限に抑えるには機能します。 その目標は、場所、ライブラリの新機能は言語にシームレスに組み込むクリーン デザインに対して分散されます。 新しい型を必要とする c# の将来のバージョンの新機能と標準ライブラリ内のメンバーがあります。 これらの依存関係、作業を管理する方法を理解しておく必要であります。

## <a name="managing-your-dependencies"></a>依存関係を管理します。

C# コンパイラ ツールは、サポートされているプラットフォームの .NET ライブラリのリリース サイクルからは切り離されてようになりました。 実際には、別のリリース サイクルのある別の .NET ライブラリ: Windows 上の .NET Framework は、Windows Update と relesed、.NET Core は個別のスケジュール、および各ターゲット プラットフォーム用の Xamarin ツール付属のライブラリの更新プログラムのバージョンの Xamarin では付属しています。

ほとんどの時間は、これらの変更が気付きません。 ただし、そのプラットフォームで機能を必要とする言語のまだ .NET ライブラリ内の新しいバージョンを処理するときに、それらの新しい型を提供する NuGet パッケージを参照します。
プラットフォーム、アプリがサポートする、新しいフレームワークのインストールで更新では、余分な参照を削除できます。

この分離は、対応するために、フレームワークがない可能性がありますマシンを対象としている場合でも、新しい言語機能を使用することができますを意味します。
