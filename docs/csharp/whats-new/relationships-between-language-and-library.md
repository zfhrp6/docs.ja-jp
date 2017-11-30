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
# <a name="relationships-between-language-features-and-library-types"></a><span data-ttu-id="817ca-105">言語機能とライブラリの型間のリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="817ca-105">Relationships between language features and library types</span></span>

<span data-ttu-id="817ca-106">C# 言語の定義には、それらの型の特定の種類と特定のアクセス可能なメンバーの設定を標準ライブラリが必要です。</span><span class="sxs-lookup"><span data-stu-id="817ca-106">The C# language definition requires a standard library to have certain types and certain accessible members on those types.</span></span> <span data-ttu-id="817ca-107">コンパイラは、多くのさまざまな言語機能のこれらの必要な型およびメンバーを使用するコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="817ca-107">The compiler generates code that uses these required types and members for many different language features.</span></span> <span data-ttu-id="817ca-108">必要に応じて、ここでその型またはメンバーがまだ展開されていません環境を作成する場合、言語の新しいバージョンのために必要な型が含まれている NuGet パッケージがあります。</span><span class="sxs-lookup"><span data-stu-id="817ca-108">When necessary, there are NuGet packages that contain types needed for newer versions of the language when writing code for environments where those types or members have not been deployed yet.</span></span>

<span data-ttu-id="817ca-109">この標準ライブラリの機能に対する依存関係は、最初のバージョンから、c# 言語の一部をされました。</span><span class="sxs-lookup"><span data-stu-id="817ca-109">This dependency on standard library functionality has been part of the C# language since its first version.</span></span> <span data-ttu-id="817ca-110">そのバージョンでは、例が含まれます。</span><span class="sxs-lookup"><span data-stu-id="817ca-110">In that version, examples included:</span></span>

* <span data-ttu-id="817ca-111"><xref:System.Exception>-すべてのコンパイラによって生成された例外のために使用します。</span><span class="sxs-lookup"><span data-stu-id="817ca-111"><xref:System.Exception> - used for all compiler generated exceptions.</span></span>
* <span data-ttu-id="817ca-112"><xref:System.String>-c#`string`型は、シノニムの<xref:System.String>します。</span><span class="sxs-lookup"><span data-stu-id="817ca-112"><xref:System.String> - the C# `string` type is a synonym for <xref:System.String>.</span></span>
* <span data-ttu-id="817ca-113"><xref:System.Int32>シノニム`int`です。</span><span class="sxs-lookup"><span data-stu-id="817ca-113"><xref:System.Int32> - synonym of `int`.</span></span>

<span data-ttu-id="817ca-114">その最初のバージョンが単純な: コンパイラおよび標準ライブラリは、まとめて配布され、それぞれのバージョンを 1 つだけが発生しました。</span><span class="sxs-lookup"><span data-stu-id="817ca-114">That first version was simple: the compiler and the standard library shipped together, and there was only one version of each.</span></span>

<span data-ttu-id="817ca-115">以降のバージョンの c# は、依存関係に、新しい型またはメンバーを追加した場合があります。</span><span class="sxs-lookup"><span data-stu-id="817ca-115">Subsequent versions of C# have occasionally added new types or members to the dependencies.</span></span> <span data-ttu-id="817ca-116">例: <xref:System.Runtime.CompilerServices.INotifyCompletion>、<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>と<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="817ca-116">Examples include: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> and <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>.</span></span> <span data-ttu-id="817ca-117">C# 7.0 の依存関係を追加することでこれが引き続き<xref:System.ValueTuple>を実装する、[組](../tuples.md)言語機能。</span><span class="sxs-lookup"><span data-stu-id="817ca-117">C# 7.0 continues this by adding a dependency on <xref:System.ValueTuple> to implement the [tuples](../tuples.md) language feature.</span></span>

<span data-ttu-id="817ca-118">言語設計チームが、型および準拠している標準ライブラリで必要なメンバーの表層領域を最小限に抑えるには機能します。</span><span class="sxs-lookup"><span data-stu-id="817ca-118">The language design team works to minimize the surface area of the types and members required in a compliant standard library.</span></span> <span data-ttu-id="817ca-119">その目標は、場所、ライブラリの新機能は言語にシームレスに組み込むクリーン デザインに対して分散されます。</span><span class="sxs-lookup"><span data-stu-id="817ca-119">That goal is balanced against a clean design where new library features are incorporated seamlessly into the language.</span></span> <span data-ttu-id="817ca-120">新しい型を必要とする c# の将来のバージョンの新機能と標準ライブラリ内のメンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="817ca-120">There will be new features in future versions of C# that require new types and members in a standard library.</span></span> <span data-ttu-id="817ca-121">これらの依存関係、作業を管理する方法を理解しておく必要であります。</span><span class="sxs-lookup"><span data-stu-id="817ca-121">It's important to understand how to manage those dependencies in your work.</span></span>

## <a name="managing-your-dependencies"></a><span data-ttu-id="817ca-122">依存関係を管理します。</span><span class="sxs-lookup"><span data-stu-id="817ca-122">Managing your dependencies</span></span>

<span data-ttu-id="817ca-123">C# コンパイラ ツールは、サポートされているプラットフォームの .NET ライブラリのリリース サイクルからは切り離されてようになりました。</span><span class="sxs-lookup"><span data-stu-id="817ca-123">C# compiler tools are now decoupled from the release cycle of the .NET libraries on supported platforms.</span></span> <span data-ttu-id="817ca-124">実際には、別のリリース サイクルのある別の .NET ライブラリ: Windows 上の .NET Framework は、Windows Update と relesed、.NET Core は個別のスケジュール、および各ターゲット プラットフォーム用の Xamarin ツール付属のライブラリの更新プログラムのバージョンの Xamarin では付属しています。</span><span class="sxs-lookup"><span data-stu-id="817ca-124">In fact, different .NET libraries have different release cycles: the .NET Framework on Windows is relesed as a Windows Update, .NET Core ships on a separate schedule, and the Xamarin versions of library updates ship with the Xamarin tools for each target platform.</span></span>

<span data-ttu-id="817ca-125">ほとんどの時間は、これらの変更が気付きません。</span><span class="sxs-lookup"><span data-stu-id="817ca-125">The majority of time, you won't notice these changes.</span></span> <span data-ttu-id="817ca-126">ただし、そのプラットフォームで機能を必要とする言語のまだ .NET ライブラリ内の新しいバージョンを処理するときに、それらの新しい型を提供する NuGet パッケージを参照します。</span><span class="sxs-lookup"><span data-stu-id="817ca-126">However, when you are working with a newer version of the language that requires features not yet in the .NET libraries on that platform, you'll reference the NuGet packages to provide those new types.</span></span>
<span data-ttu-id="817ca-127">プラットフォーム、アプリがサポートする、新しいフレームワークのインストールで更新では、余分な参照を削除できます。</span><span class="sxs-lookup"><span data-stu-id="817ca-127">As the platforms your app supports are updated with new framework installations, you can remove the extra reference.</span></span>

<span data-ttu-id="817ca-128">この分離は、対応するために、フレームワークがない可能性がありますマシンを対象としている場合でも、新しい言語機能を使用することができますを意味します。</span><span class="sxs-lookup"><span data-stu-id="817ca-128">This separation means you can use new language features even when you are targeting machines that may not have the corresponding framework.</span></span>
