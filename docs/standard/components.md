---
title: ".NET アーキテクチャ コンポーネント"
description: ".NET Standard Library、.NET ランタイム、ツールなど、主要な .NET アーキテクチャ コンポーネントについて説明します。"
keywords: ".NET, .NET Standard Library, .NET Standard, .NET Core, .NET Framework, Xamarin, MSBuild, C#, F#, VB, コンパイラ"
author: cartermp
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 7741df222250f3746abb1e3c359bd9e89e6a732c
ms.openlocfilehash: e93764ff4d3391110c79f73a34512bd073ce0499
ms.lasthandoff: 01/18/2017

---

# <a name="net-architectural-components"></a>.NET アーキテクチャ コンポーネント

.NET は複数の主要コンポーネントで構成されています。  .NET Standard Library という名前の標準ライブラリは、どこでも実行できる大規模な API のセットです。  この標準ライブラリは、3 つの .NET ランタイム、つまり .NET Framework、.NET Core、Mono for Xamarin で実装されています。  また、.NET 言語はどの .NET ランタイムでも実行します。  さらに、すべてのプラットフォームにプロジェクトをビルドするためのツールがあります。  これらのツールは、どのランタイムを選んでも同じです。

次の図は、これまでに説明した .NET の各コンポーネントの概要とそれらの関係を示したものです。

![すべての .NET アーキテクチャ コンポーネント](media/components.png)

以降では、これらの主要コンポーネントのそれぞれについて簡単に説明します。  

## <a name="net-standard-library"></a>.NET Standard Library

.NET Standard Library は、.NET ランタイムによって実装される API のセットです。

さらに厳密に言うと、コードのコンパイル対象である統一されたコントラクトのセットを構成する .NET API の仕様です。  これらのコントラクトには、各 .NET ランタイムの基になる実装があります。  これにより異なる .NET ランタイム間の移植性が可能になり、コードは効率的に "どこでも実行" できるようになります。

.NET Standard Library はビルド ターゲットでもあり、.NET Standard と呼ばれます。  現在は .NET Standard 1.0 ～ 1.6 を対象にできます。  コードが .NET Standard のバージョンを対象にする場合、そのバージョンを実装するすべての .NET ランタイムで動作することが保証されます。

.NET Standard Library および .NET Standard の対象化の詳細については、「[.NET Standard Library](library.md)」をご覧ください。

## <a name="net-runtimes"></a>.NET ランタイム

Microsoft が積極的に開発し保守している主要な .NET ランタイムとしては、.NET Core、.NET Framework、Mono for Xamarin の 3 つがあります。

### <a name="net-core"></a>.NET Core

.NET Core は、サーバーのワークロード用に最適化されたクロスプラットフォーム ランタイムです。  .NET Standard Library を実装しているので、.NET Standard を対象とするすべてのコードが .NET Core 上で実行できます。  ASP.NET Core およびユニバーサル Windows プラットフォーム (UWP) で使用されるランタイムです。  最新の機能を備え、効率的であり、大規模なサーバーとクラウドのワークロードを処理するように設計されています。

.NET Core について詳しくは、「[.NET Core](../core/index.md)」をご覧ください。

### <a name="net-framework"></a>.NET Framework

.NET Framework は従来の .NET ランタイムであり、2002 年から使用されています。  既存の .NET 開発者が常に使用してきたものと同じ .NET Framework です。  .NET Standard Library を実装しているので、.NET Standard を対象とするすべてのコードが .NET Framework 上で実行できます。  Windows フォームと WPF での Windows デスクトップ開発用 API など、追加の Windows 固有 API が含まれます。  .NET Framework は、Windows デスクトップ アプリケーション開発用に最適化されています。

.NET Framework について詳しくは、「[.NET Framework](../framework/index.md)」をご覧ください。

### <a name="mono-for-xamarin"></a>Mono for Xamarin

Mono は、Xamarin アプリで使われるランタイムです。  .NET Standard Library を実装しているので、.NET Standard を対象とするすべてのコードが Xamarin アプリ上で実行できます。  iOS、Android、Xamarin.Forms、Xamarin.Mac 用の追加 API が含まれます。  iOS および Android でのモバイル アプリケーションの開発に最適化されています。

Mono について詳しくは、[Mono のドキュメント](http://www.mono-project.com/docs/)をご覧ください。

## <a name="net-tooling-and-common-infrastructure"></a>.NET のツールと共通インフラストラクチャ

.NET 用のツールは、.NET の各実装に共通でもあります。  次に一例を挙げます。

* .NET 言語とコンパイラ
* JIT やガベージ コレクターなどのランタイム コンポーネント
* .NET プロジェクト システム ("csproj"、"vbproj"、"fsproj" などと呼ばれることもあります)
* プロジェクトのビルドに使われるビルド エンジンである MSBuild
* Microsoft の .NET 用パッケージ マネージャーである NuGet
* .NET プロジェクト開発用のクロスプラットフォーム コマンドライン インターフェイスである .NET CLI
* オープン ソースのビルド オーケストレーション ツール (CAKE、FAKE など)

ここで重要なのは、アプリ開発に .NET のどの "フレーバー" を選択しても共通のツールとインフラストラクチャが多数存在することです。

## <a name="next-steps"></a>次の手順

詳細については、次のトピックを参照してください。

* [.NET 標準ライブラリ](library.md)
* [.NET Core のガイド](../core/index.md)
* [.NET Framework ガイド](../framework/index.md)
* [C# のガイド](../csharp/index.md)
* [F# のガイド](../fsharp/index.md)
* [VB.NET ガイド](../visual-basic/index.md)

