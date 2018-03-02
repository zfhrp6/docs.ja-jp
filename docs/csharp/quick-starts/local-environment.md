---
title: "ローカル環境のチュートリアル - C# ローカル クイックスタート"
description: "このクイックスタートでは、クイックスタートをローカルで実行するための基本について説明します。"
author: billwagner
ms.topic: article
ms.date: 12/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9957f524e04f8ff64d4f640cf085b16cf9a2c0c6
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="local-environment"></a><span data-ttu-id="03b44-103">ローカル環境</span><span class="sxs-lookup"><span data-stu-id="03b44-103">Local environment</span></span>

<span data-ttu-id="03b44-104">クイックスタートをローカルで実行するための最初の手順は、ローカル コンピューター上に開発環境をセットアップすることです。</span><span class="sxs-lookup"><span data-stu-id="03b44-104">The first step to trying a quickstart locally is to setup a development environment on your local machine.</span></span>
<span data-ttu-id="03b44-105">Mac、PC、または Linux 上でローカルの開発環境を設定する手順については、.NET の [10 分でわかる概要](https://www.microsoft.com/net/core)に関するトピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="03b44-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

<span data-ttu-id="03b44-106">または、[.NET Core SDK](http://dot.net/core) と [Visual Studio Code](https://code.visualstudio.com/) をインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="03b44-106">Alternatively, you can install the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="03b44-107">アプリケーション開発の基本フロー</span><span class="sxs-lookup"><span data-stu-id="03b44-107">Basic application development flow</span></span>

<span data-ttu-id="03b44-108">[`dotnet new`](../../core/tools/dotnet-new.md) コマンドを使用してアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="03b44-108">You'll create applications using the [`dotnet new`](../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="03b44-109">このコマンドによってアプリケーションに必要なファイルとアセットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="03b44-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="03b44-110">クイック スタートではすべて `console` タイプのアプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="03b44-110">The quickstarts all use the `console` application type.</span></span>

<span data-ttu-id="03b44-111">その他には、実行可能ファイルをビルドする [`dotnet build`](../../core/tools/dotnet-build.md) コマンド、実行可能ファイルを実行する [`dotnet run`](../../core/tools/dotnet-run.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="03b44-111">The other commands you'll use are [`dotnet build`](../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-quickstart"></a><span data-ttu-id="03b44-112">クイック スタートを選択する</span><span class="sxs-lookup"><span data-stu-id="03b44-112">Pick your quickstart</span></span>

<span data-ttu-id="03b44-113">次のどのクイックスタートからでも始められます。</span><span class="sxs-lookup"><span data-stu-id="03b44-113">You can start with any of the following quickstarts:</span></span>

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[<span data-ttu-id="03b44-114">C# における数値</span><span class="sxs-lookup"><span data-stu-id="03b44-114">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="03b44-115">「[C# における数値](numbers-in-csharp-local.md)」クイック スタートでは、コンピューターが数値を格納する方法と、異なる数値型で計算を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="03b44-115">In the [Numbers in C#](numbers-in-csharp-local.md) quickstart, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="03b44-116">丸め処理の基礎と、C# で算術演算を実行する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="03b44-116">You'll learn the basics of rounding, and how to perform mathematical calculations using C#.</span></span> 

<span data-ttu-id="03b44-117">このクイック スタートでは、「[Hello World](hello-world.yml)」チュートリアルを終了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="03b44-117">This quickstart assumes that you have finished the [Hello world](hello-world.yml) tutorial.</span></span>

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[<span data-ttu-id="03b44-118">分岐とループ</span><span class="sxs-lookup"><span data-stu-id="03b44-118">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="03b44-119">「[分岐とループ](branches-and-loops-local.md)」のクイック スタートでは、変数に格納された値に基づいて、コード実行のさまざまなパスを選択する作業の基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="03b44-119">The [Branches and loops](branches-and-loops-local.md) quickstart teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="03b44-120">プログラムが決定して異なる操作を選択する上で基本となる、制御フローの基礎を学習します。</span><span class="sxs-lookup"><span data-stu-id="03b44-120">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span> 

<span data-ttu-id="03b44-121">この入門レッスンでは、「[Hello World](hello-world.yml)」および「[C# における数値](numbers-in-csharp-local.md)」の各レッスンが終了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="03b44-121">This beginning lesson assumes that you have finished the [Hello World](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collectionarrays-and-collectionsmd"></a>[<span data-ttu-id="03b44-122">リスト コレクション</span><span class="sxs-lookup"><span data-stu-id="03b44-122">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="03b44-123">「[リスト コレクション](arrays-and-collections.md)」レッスンでは、データのシーケンスを格納するリスト コレクション型について説明します。</span><span class="sxs-lookup"><span data-stu-id="03b44-123">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="03b44-124">項目の追加方法や削除方法、項目の検索方法、リストを並べ替える方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="03b44-124">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="03b44-125">さまざまな種類のリストを紹介します。</span><span class="sxs-lookup"><span data-stu-id="03b44-125">You'll explore different kinds of lists.</span></span> 

<span data-ttu-id="03b44-126">この入門クイック スタートでは、上記のクイック スタートが終了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="03b44-126">This beginning quickstart assumes that you have finished the quickstarts listed above.</span></span>

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[<span data-ttu-id="03b44-127">クラスの概要</span><span class="sxs-lookup"><span data-stu-id="03b44-127">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="03b44-128">この最後のクイック スタートは、お使いのマシンで、独自のローカルの開発環境と .NET Core を使用して行うためにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="03b44-128">This final quickstart is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="03b44-129">コンソール アプリケーションを構築し、C# 言語に含まれるオブジェクト指向の基本的な機能について学習します。</span><span class="sxs-lookup"><span data-stu-id="03b44-129">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
