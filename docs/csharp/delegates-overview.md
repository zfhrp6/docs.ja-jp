---
title: "デリゲートの概要"
description: "この概要トピックでは、基本的な概念を紹介し、デリゲートの言語上の設計目標について説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dd4c68fb4f960d0c2d5cbdc9e699650070cacaf1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="introduction-to-delegates"></a><span data-ttu-id="a04d2-104">デリゲートの概要</span><span class="sxs-lookup"><span data-stu-id="a04d2-104">Introduction to Delegates</span></span>

[<span data-ttu-id="a04d2-105">前へ</span><span class="sxs-lookup"><span data-stu-id="a04d2-105">Previous</span></span>](delegates-events.md)

<span data-ttu-id="a04d2-106">デリゲートは、.NET における "*遅延バインディング*" のメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="a04d2-106">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="a04d2-107">遅延バインディングとは、皆さんが作成するアルゴリズムについて、その一部を実装するメソッドを呼び出し元からも少なくとも 1 つ与えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a04d2-107">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="a04d2-108">たとえば天文学アプリケーションで、一連の星を並べ替えることを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="a04d2-108">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="a04d2-109">星の並べ替え基準には、地球からの距離や星の等級、知覚的な明るさを選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="a04d2-109">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="a04d2-110">いずれの場合も、Sort() メソッドが行うことは基本的に同じです。つまり何らかの比較に基づいて一連の項目を整列します。</span><span class="sxs-lookup"><span data-stu-id="a04d2-110">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="a04d2-111">しかし、2 つの星を比較するコードは、並べ替えの基準によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a04d2-111">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="a04d2-112">ソフトウェアには、この種の手法が半世紀にわたって使用されてきました。</span><span class="sxs-lookup"><span data-stu-id="a04d2-112">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="a04d2-113">C# 言語のデリゲートの概念は、きわめて優れた言語機能と、その概念を中心にしたタイプ セーフ機能を実現します。</span><span class="sxs-lookup"><span data-stu-id="a04d2-113">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="a04d2-114">本シリーズの中で後述しているように、このようなアルゴリズム向けに記述された C# コードはタイプ セーフであり、引数や戻り値の型については、言語とコンパイラの機能を利用して型の一致が保証されます。</span><span class="sxs-lookup"><span data-stu-id="a04d2-114">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="a04d2-115">デリゲートの言語上の設計目標</span><span class="sxs-lookup"><span data-stu-id="a04d2-115">Language Design Goals for Delegates</span></span>

<span data-ttu-id="a04d2-116">最終的にデリゲートとなる機能を実現するにあたって、言語の設計者たちはさまざまな目標を設定しました。</span><span class="sxs-lookup"><span data-stu-id="a04d2-116">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="a04d2-117">設計チームが目指したのは、あらゆる遅延バインディング アルゴリズムに適用できる共通の言語概念です。</span><span class="sxs-lookup"><span data-stu-id="a04d2-117">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="a04d2-118">つまり、開発者が 1 つの概念を身に付ければ、ソフトウェアに関するさまざまな課題にその知識を応用できるような言語の実現を目標に掲げたのです。</span><span class="sxs-lookup"><span data-stu-id="a04d2-118">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="a04d2-119">次に設計チームが目指したのは、シングルキャストとマルチキャストの両方のメソッド呼び出しをサポートすることでした。</span><span class="sxs-lookup"><span data-stu-id="a04d2-119">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="a04d2-120">複数のメソッドが数珠つなぎの状態になったデリゲートを "マルチキャスト デリゲート" といいます。</span><span class="sxs-lookup"><span data-stu-id="a04d2-120">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="a04d2-121">実際の例については、[本シリーズの中で後述](delegate-class.md)しています。</span><span class="sxs-lookup"><span data-stu-id="a04d2-121">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="a04d2-122">設計チームは、C# のあらゆるコード要素に関して開発者たちが当然と考えるレベルのタイプ セーフティをデリゲートにおいても実現したいと考えていたのです。</span><span class="sxs-lookup"><span data-stu-id="a04d2-122">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="a04d2-123">また、設計チームは、デリゲートを初めとする遅延バインディング アルゴリズムの利便性が大いに発揮される具体的なパターンは、イベント パターンであると認識していました。</span><span class="sxs-lookup"><span data-stu-id="a04d2-123">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="a04d2-124">.NET のイベントの基本的なパターンをデリゲートのコードで確実に実現したいと考えていたのです。</span><span class="sxs-lookup"><span data-stu-id="a04d2-124">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="a04d2-125">そうした目標に向けたすべての作業の成果として C# と .NET にサポートされたのが、デリゲートとイベントです。</span><span class="sxs-lookup"><span data-stu-id="a04d2-125">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="a04d2-126">以降このセクションの記事では、言語の機能やライブラリのサポート、デリゲートを扱う際に用いられる一般的な用語について取り上げています。</span><span class="sxs-lookup"><span data-stu-id="a04d2-126">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="a04d2-127">`delegate` キーワードとそれによって生成されるコード、</span><span class="sxs-lookup"><span data-stu-id="a04d2-127">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="a04d2-128">`System.Delegate` クラスの機能とその使い方、</span><span class="sxs-lookup"><span data-stu-id="a04d2-128">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="a04d2-129">タイプ セーフなデリゲートの作成方法、デリゲート経由で呼び出すことのできるメソッドの作成方法のほか、</span><span class="sxs-lookup"><span data-stu-id="a04d2-129">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="a04d2-130">ラムダ式を使ったデリゲートやイベントの扱い方、</span><span class="sxs-lookup"><span data-stu-id="a04d2-130">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="a04d2-131">LINQ の構成要素としてデリゲートがどこで使われているか、</span><span class="sxs-lookup"><span data-stu-id="a04d2-131">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="a04d2-132">.NET のイベント パターンの基礎としてデリゲートがどのように使われ、両者がどのように違うのかについても説明します。</span><span class="sxs-lookup"><span data-stu-id="a04d2-132">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="a04d2-133">すべての記事を読み終えると、.NET のプログラミングやフレームワーク API を利用するうえでの不可欠な要素として、デリゲートがどのように活かされているのかがおわかりいただけると思います。</span><span class="sxs-lookup"><span data-stu-id="a04d2-133">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="a04d2-134">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="a04d2-134">Let's get started.</span></span>

[<span data-ttu-id="a04d2-135">次へ</span><span class="sxs-lookup"><span data-stu-id="a04d2-135">Next</span></span>](delegate-class.md)

