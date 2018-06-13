---
title: 共通のコンテナー デザインの原則
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c67986b1deb504f2b05f2903a263bf1a91f70b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568122"
---
# <a name="common-container-design-principles"></a><span data-ttu-id="f8b24-103">共通のコンテナー デザインの原則</span><span class="sxs-lookup"><span data-stu-id="f8b24-103">Common container design principles</span></span>

<span data-ttu-id="f8b24-104">事前に、開発プロセスを取得するはすコンテナーを使用する方法に関していくつかの基本的な概念です。</span><span class="sxs-lookup"><span data-stu-id="f8b24-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="f8b24-105">コンテナーには、プロセスと等しい</span><span class="sxs-lookup"><span data-stu-id="f8b24-105">Container equals a process</span></span>

<span data-ttu-id="f8b24-106">コンテナー モデルでは、コンテナーは、1 つのプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="f8b24-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="f8b24-107">コンテナーを定義すると、プロセス境界として、スケール、またはバッチ オフ、プロセスに使用されるプリミティブの作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="f8b24-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="f8b24-108">Docker コンテナーを実行すると表示されます、 [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)定義します。</span><span class="sxs-lookup"><span data-stu-id="f8b24-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="f8b24-109">これは、プロセス、およびコンテナーの有効期間を定義します。</span><span class="sxs-lookup"><span data-stu-id="f8b24-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="f8b24-110">プロセスが完了したら、コンテナーのライフ サイクルが終了します。</span><span class="sxs-lookup"><span data-stu-id="f8b24-110">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="f8b24-111">Web サーバー、および Microsoft Azure として実装されていますが、バッチ ジョブなどの有効期間が短いプロセスなどの実行時間の長いプロセスが[WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/)です。</span><span class="sxs-lookup"><span data-stu-id="f8b24-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="f8b24-112">プロセスが失敗した場合、コンテナーが終了し、Orchestrator が引き継ぎます。</span><span class="sxs-lookup"><span data-stu-id="f8b24-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="f8b24-113">Orchestrator が実行されている 5 つのインスタンスを保持するように指示しました、1 つが失敗した場合は、orchestrator は、失敗した処理を置換する別のコンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f8b24-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="f8b24-114">バッチ ジョブで、プロセスはパラメーターを指定して開始されます。</span><span class="sxs-lookup"><span data-stu-id="f8b24-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="f8b24-115">プロセスが完了すると、作業が完了します。</span><span class="sxs-lookup"><span data-stu-id="f8b24-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="f8b24-116">複数のプロセスが 1 つのコンテナーで実行するシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="f8b24-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="f8b24-117">任意のアーキテクチャのドキュメントではありません、"never、"は常にも、「常にします」。</span><span class="sxs-lookup"><span data-stu-id="f8b24-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="f8b24-118">複数のプロセスを必要とするシナリオで一般的なパターンでは、使用する[スーパーバイザー](http://supervisord.org/)です。</span><span class="sxs-lookup"><span data-stu-id="f8b24-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f8b24-119">[前] (デザインの docker-applications.md) [次へ] (モノリシック applications.md)</span><span class="sxs-lookup"><span data-stu-id="f8b24-119">[Previous] (design-docker-applications.md) [Next] (monolithic-applications.md)</span></span>
