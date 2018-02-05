---
title: "非同期の概要"
description: "ブロッキング I/O と複数コアでの同時操作の処理を容易にする鍵となる手法である非同期プログラミングについて説明します。"
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2dddc21dfb124fe97c397a156743981a67e4037
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="async-overview"></a><span data-ttu-id="e8c52-104">非同期の概要</span><span class="sxs-lookup"><span data-stu-id="e8c52-104">Async Overview</span></span>

<span data-ttu-id="e8c52-105">少し前まで、アプリの高速化は、より新しい PC やサーバーを購入することによって単純に実現されていましたが、その傾向は終わりました。</span><span class="sxs-lookup"><span data-stu-id="e8c52-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="e8c52-106">実際には、逆転しました。</span><span class="sxs-lookup"><span data-stu-id="e8c52-106">In fact, it reversed.</span></span> <span data-ttu-id="e8c52-107">1 GHz のシングル コア ARM チップを搭載した携帯電話が登場し、サーバーのワークロードは VM に移行されました。</span><span class="sxs-lookup"><span data-stu-id="e8c52-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="e8c52-108">ユーザーは引き続き応答速度の速い UI を望み、ビジネス オーナーは業務の拡大に合わせて拡張できるサーバーを必要としています。</span><span class="sxs-lookup"><span data-stu-id="e8c52-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="e8c52-109">モバイルおよびクラウドへの移行が進み、インターネット接続ユーザーが 30 億人を超えた結果、新しいソフトウェア パターンが生まれました。</span><span class="sxs-lookup"><span data-stu-id="e8c52-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="e8c52-110">クライアント アプリケーションには、アプリ ストアの高い評価と共に、常時オンで常時接続であること、そのうえでユーザーの操作 (タッチなど) に対する応答性を常に維持することが期待されます。</span><span class="sxs-lookup"><span data-stu-id="e8c52-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="e8c52-111">サービスは、適切にスケールアップおよびスケールダウンしてトラフィックの急増に対処することが期待されます。</span><span class="sxs-lookup"><span data-stu-id="e8c52-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="e8c52-112">非同期プログラミングは、ブロッキング I/O と複数コアでの同時操作の処理を容易にする鍵となる手法です。</span><span class="sxs-lookup"><span data-stu-id="e8c52-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="e8c52-113">.NET では、C#、VB、F# で簡単に使用できる言語レベルの非同期プログラミング モデルにより、アプリやサービスの応答性と弾力性を実現する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="e8c52-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="e8c52-114">非同期コードを記述する理由</span><span class="sxs-lookup"><span data-stu-id="e8c52-114">Why Write Async Code?</span></span>

<span data-ttu-id="e8c52-115">最新アプリでは、ファイルおよびネットワーク I/O を広範囲に使用します。</span><span class="sxs-lookup"><span data-stu-id="e8c52-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="e8c52-116">従来の I/O API は既定によりブロックし、困難なパターンを学習して使用しない限り、結果的にユーザー エクスペリエンスとハードウェア使用率が不適切になっていました。</span><span class="sxs-lookup"><span data-stu-id="e8c52-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="e8c52-117">このモデルを逆転させたのがタスクベースの非同期 API と言語レベルの非同期プログラミング モデルであり、非同期実行が既定になりました。これに関して新たに学習する必要がある概念はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="e8c52-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="e8c52-118">非同期コードの特性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e8c52-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="e8c52-119">スレッドを生成することによって、I/O 要求が戻るのを待つ間により多くのサーバー要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="e8c52-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="e8c52-120">I/O 要求の待機中に UI 操作に対してスレッドを生成し、実行時間の長い作業を他の CPU コアに移行することによって、UI の応答性を高めます。</span><span class="sxs-lookup"><span data-stu-id="e8c52-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="e8c52-121">新しい .NET API の多くは非同期です。</span><span class="sxs-lookup"><span data-stu-id="e8c52-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="e8c52-122">.NET で非同期コードを記述するのはとても簡単です。</span><span class="sxs-lookup"><span data-stu-id="e8c52-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="e8c52-123">次の内容</span><span class="sxs-lookup"><span data-stu-id="e8c52-123">What's next?</span></span>

<span data-ttu-id="e8c52-124">非同期の概念とプログラミングの詳細については、「[非同期の詳細](async-in-depth.md)」と「[Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md)」(タスクベースの非同期プログラミング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c52-124">For a deep dive into async concepts and programming, see [Async in depth](async-in-depth.md) and [Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>
