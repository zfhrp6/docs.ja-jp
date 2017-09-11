---
title: ".NET Compiler SDK の使用 - C# ガイド"
description: "自動診断とコードの修正を作成する Roslyn API について説明します"
keywords: .NET, .NET Core, C#, Roslyn,
ms.date: 06/25/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: abed9e00-2ddc-468e-9cca-d033bd6a7e36
redirect_url: /dotnet/csharp/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b227d67fd5431da328e1686fd9afc6a3b9db035e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="-using-the-net-compiler-sdk"></a><span data-ttu-id="2c5c9-104">🔧 .NET Compiler SDK の使用</span><span class="sxs-lookup"><span data-stu-id="2c5c9-104">🔧 Using the .NET Compiler SDK</span></span>

> <span data-ttu-id="2c5c9-105">**注:**</span><span class="sxs-lookup"><span data-stu-id="2c5c9-105">**Note**</span></span>
> 
> <span data-ttu-id="2c5c9-106">このトピックはまだ作成されておりません。</span><span class="sxs-lookup"><span data-stu-id="2c5c9-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="2c5c9-107">適用範囲や方法を具体化するのに役立つ皆様からのご意見をお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="2c5c9-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="2c5c9-108">GitHub で状態の追跡やこの[件](https://github.com/dotnet/docs/issues/972)に関するご意見を投稿することができます。</span><span class="sxs-lookup"><span data-stu-id="2c5c9-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/972) at GitHub.</span></span>
> 
> <span data-ttu-id="2c5c9-109">このトピックの初期ドラフトや概要の確認をご希望の場合は、この件の連絡先情報を含むメモを入力してください。</span><span class="sxs-lookup"><span data-stu-id="2c5c9-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="2c5c9-110">ご意見の投稿方法の詳細については、[GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md) でご確認ください。</span><span class="sxs-lookup"><span data-stu-id="2c5c9-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

<span data-ttu-id="2c5c9-111">これは、セクション全体のメタ トピックです。</span><span class="sxs-lookup"><span data-stu-id="2c5c9-111">This is a meta-topic for an entire section.</span></span> <span data-ttu-id="2c5c9-112">ここで説明する必要がある領域は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2c5c9-112">Areas that need to be covered here include:</span></span> 
* <span data-ttu-id="2c5c9-113">作業の開始</span><span class="sxs-lookup"><span data-stu-id="2c5c9-113">Getting Started</span></span>
* <span data-ttu-id="2c5c9-114">サンプルおよびチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2c5c9-114">Samples and tutorials</span></span>
* <span data-ttu-id="2c5c9-115">概念的な内容</span><span class="sxs-lookup"><span data-stu-id="2c5c9-115">conceptual content</span></span>
* <span data-ttu-id="2c5c9-116">API の全体的なモデル</span><span class="sxs-lookup"><span data-stu-id="2c5c9-116">overall model of the APIs</span></span>
* <span data-ttu-id="2c5c9-117">[roslyn-analyzers](http://github.com/dotnet/roslyn-analyzers) リポジトリのサンプルへのリンク</span><span class="sxs-lookup"><span data-stu-id="2c5c9-117">links to samples on the [roslyn-analyzers](http://github.com/dotnet/roslyn-analyzers) repository</span></span>
* <span data-ttu-id="2c5c9-118">その他のリファレンス コンテンツへのリンク</span><span class="sxs-lookup"><span data-stu-id="2c5c9-118">links to other reference content</span></span>

