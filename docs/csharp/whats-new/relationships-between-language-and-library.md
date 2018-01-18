---
title: "言語機能とライブラリ型間のリレーションシップ | Microsoft Docs"
description: "言語機能は多くの場合、実装のためにライブラリ型に依存します。 そのリレーションシップを理解します。"
keywords: "C# 言語の設計、標準ライブラリ"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: b7de4fdb4356e8822dba6aaaf67d615980ff09cd
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="relationships-between-language-features-and-library-types"></a><span data-ttu-id="88899-105">言語機能とライブラリ型間のリレーションシップ</span><span class="sxs-lookup"><span data-stu-id="88899-105">Relationships between language features and library types</span></span>

<span data-ttu-id="88899-106">C# 言語の定義には、標準ライブラリに特定の型とその型にアクセス可能な特定のメンバーがある必要があります。</span><span class="sxs-lookup"><span data-stu-id="88899-106">The C# language definition requires a standard library to have certain types and certain accessible members on those types.</span></span> <span data-ttu-id="88899-107">コンパイラは、多くの異なる言語機能に必要なこれらの型とメンバーを使用するコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="88899-107">The compiler generates code that uses these required types and members for many different language features.</span></span> <span data-ttu-id="88899-108">これらの型やメンバーがまだ展開されていない環境のためのコードを記述する場合に、必要な場合には、その言語の新しいバージョンに必要な型が含まれている NuGet パッケージがあります。</span><span class="sxs-lookup"><span data-stu-id="88899-108">When necessary, there are NuGet packages that contain types needed for newer versions of the language when writing code for environments where those types or members have not been deployed yet.</span></span>

<span data-ttu-id="88899-109">この標準ライブラリ機能に対する依存関係は、C# 言語の最初のバージョンからその一部となっています。</span><span class="sxs-lookup"><span data-stu-id="88899-109">This dependency on standard library functionality has been part of the C# language since its first version.</span></span> <span data-ttu-id="88899-110">そのバージョンでは、次の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="88899-110">In that version, examples included:</span></span>

* <span data-ttu-id="88899-111"><xref:System.Exception>: 例外を生成したすべてのコンパイラに使用されます。</span><span class="sxs-lookup"><span data-stu-id="88899-111"><xref:System.Exception> - used for all compiler generated exceptions.</span></span>
* <span data-ttu-id="88899-112"><xref:System.String>: C# `string` 型は <xref:System.String> のシノニムです。</span><span class="sxs-lookup"><span data-stu-id="88899-112"><xref:System.String> - the C# `string` type is a synonym for <xref:System.String>.</span></span>
* <span data-ttu-id="88899-113"><xref:System.Int32>: `int` のシノニム。</span><span class="sxs-lookup"><span data-stu-id="88899-113"><xref:System.Int32> - synonym of `int`.</span></span>

<span data-ttu-id="88899-114">その最初のバージョンは単純でした。コンパイラと標準ライブラリは共に出荷され、それぞれ 1 つのバージョンしかありませんでした。</span><span class="sxs-lookup"><span data-stu-id="88899-114">That first version was simple: the compiler and the standard library shipped together, and there was only one version of each.</span></span>

<span data-ttu-id="88899-115">C# の以降のバージョンでは、随時、依存関係に新しい型またはメンバーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="88899-115">Subsequent versions of C# have occasionally added new types or members to the dependencies.</span></span> <span data-ttu-id="88899-116">例として、<xref:System.Runtime.CompilerServices.INotifyCompletion>、<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>、<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute> があります。</span><span class="sxs-lookup"><span data-stu-id="88899-116">Examples include: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> and <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>.</span></span> <span data-ttu-id="88899-117">C# 7.0 では、<xref:System.ValueTuple> で依存関係を追加して[タプル](../tuples.md)言語機能を実装することで、これを続けています。</span><span class="sxs-lookup"><span data-stu-id="88899-117">C# 7.0 continues this by adding a dependency on <xref:System.ValueTuple> to implement the [tuples](../tuples.md) language feature.</span></span>

<span data-ttu-id="88899-118">言語設計チームは、準拠している標準ライブラリで必要な型およびメンバーのアクセス領域を最小限に抑えることに取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="88899-118">The language design team works to minimize the surface area of the types and members required in a compliant standard library.</span></span> <span data-ttu-id="88899-119">その目標は、新しいライブラリ機能が言語にシームレスに組み込まれているクリーン設計と両立させることです。</span><span class="sxs-lookup"><span data-stu-id="88899-119">That goal is balanced against a clean design where new library features are incorporated seamlessly into the language.</span></span> <span data-ttu-id="88899-120">将来、標準ライブラリ内の新しい型とメンバーを必要とする C# の新バージョンが登場するでしょう。</span><span class="sxs-lookup"><span data-stu-id="88899-120">There will be new features in future versions of C# that require new types and members in a standard library.</span></span> <span data-ttu-id="88899-121">自分の作業でこれらの依存関係を管理する方法を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="88899-121">It's important to understand how to manage those dependencies in your work.</span></span>

## <a name="managing-your-dependencies"></a><span data-ttu-id="88899-122">依存関係の管理</span><span class="sxs-lookup"><span data-stu-id="88899-122">Managing your dependencies</span></span>

<span data-ttu-id="88899-123">C# コンパイラ ツールは現在、サポートされているプラットフォームの .NET ライブラリのリリース サイクルと切り離されています。</span><span class="sxs-lookup"><span data-stu-id="88899-123">C# compiler tools are now decoupled from the release cycle of the .NET libraries on supported platforms.</span></span> <span data-ttu-id="88899-124">実際、.NET ライブラリごとに異なるリリース サイクルがあります。Windows の .NET Framework は、Windows Update としてリリースされ、.NET Core は個別のスケジュールで出荷されます。また、ライブラリの更新の Xamarin バージョンは、各ターゲット プラットフォーム用の Xamarin ツールとともに出荷されます。</span><span class="sxs-lookup"><span data-stu-id="88899-124">In fact, different .NET libraries have different release cycles: the .NET Framework on Windows is released as a Windows Update, .NET Core ships on a separate schedule, and the Xamarin versions of library updates ship with the Xamarin tools for each target platform.</span></span>

<span data-ttu-id="88899-125">ほとんどの場合、これらの変更に気付くことはありません。</span><span class="sxs-lookup"><span data-stu-id="88899-125">The majority of time, you won't notice these changes.</span></span> <span data-ttu-id="88899-126">ただし、そのプラットフォーム上の .NET ライブラリ内にまだない機能を必要とする言語の新しいバージョンを使用している場合は、それらの新しい型を提供する NuGet パッケージを参照することになります。</span><span class="sxs-lookup"><span data-stu-id="88899-126">However, when you are working with a newer version of the language that requires features not yet in the .NET libraries on that platform, you'll reference the NuGet packages to provide those new types.</span></span>
<span data-ttu-id="88899-127">お使いのアプリがサポートしているプラットフォームが新しいフレームワークのインストールで更新されるときに、余分な参照を削除できます。</span><span class="sxs-lookup"><span data-stu-id="88899-127">As the platforms your app supports are updated with new framework installations, you can remove the extra reference.</span></span>

<span data-ttu-id="88899-128">この分離は、対応するフレームワークがない可能性があるマシンを対象とする場合でも、新しい言語機能を使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="88899-128">This separation means you can use new language features even when you are targeting machines that may not have the corresponding framework.</span></span>
