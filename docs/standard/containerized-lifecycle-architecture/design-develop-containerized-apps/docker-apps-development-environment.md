---
title: "Docker アプリの開発環境"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad1a6e4cb0974ebb067cf1a7be987d696e8bc82a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="fc8ca-104">Docker アプリの開発環境</span><span class="sxs-lookup"><span data-stu-id="fc8ca-104">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="fc8ca-105">開発ツールの選択: IDE やエディター</span><span class="sxs-lookup"><span data-stu-id="fc8ca-105">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="fc8ca-106">かにかかわらずする場合、完全かつ強力な IDE または軽量とアジャイル エディターでは、Microsoft に対応する際に Docker アプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-106">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="fc8ca-107">Visual Studio Code と Docker CLI (Mac、Linux、および Windows 用のクロスプラット フォーム ツール)</span><span class="sxs-lookup"><span data-stu-id="fc8ca-107">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="fc8ca-108">任意の開発言語をサポートする、軽量のクロスプラット フォーム エディターを使用する場合は、Visual Studio Code と Docker CLI を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-108">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="fc8ca-109">これらの製品では、簡単かつ堅牢なエクスペリエンスを合理化開発者ワークフローにとって重要となるを提供します。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-109">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="fc8ca-110">"Docker の Mac"または"Docker for Windows の"(開発環境) をインストールすると、Docker の開発者は、Windows または Linux (ランタイム環境) の両方のアプリをビルドするのに 1 つの Docker CLI を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-110">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="fc8ca-111">さらに、Visual Studio Code エディターから Docker コマンドを実行するには、Dockerfile とショートカット タスク用の IntelliSense と Docker の拡張機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-111">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="fc8ca-112">Visual Studio のコードをダウンロードするには<https://code.visualstudio.com/download>です。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-112">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="fc8ca-113">Mac および Windows の Docker をダウンロードするには<http://www.docker.com/products/docker>です。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-113">To download Docker for Mac and Windows, go to <http://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="fc8ca-114">Docker ツールと visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc8ca-114">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="fc8ca-115">Visual Studio 2015 を使用している場合は、"Docker Tools for Visual Studio です"のアドオン ツールをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-115">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="fc8ca-116">Visual Studio 2017 の Docker ツールに付属でビルドされた既にです。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-116">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="fc8ca-117">どちらの場合に、開発し、実行、および選択した Docker 環境内で直接、アプリケーションを検証することができます。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-117">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="fc8ca-118">F5 キーを押して、Docker に直接、アプリケーション (1 つのコンテナーまたは複数のコンテナー) はデバッグは、ホストまたは Ctrl + f5 キーを押して編集し、コンテナーを再構築しなくてもアプリを更新します。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-118">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="fc8ca-119">これは、Linux または Windows の Docker コンテナーを作成する Windows 開発者にとって最も簡単で強力な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-119">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="fc8ca-120">Visual Studio の Docker のツールをダウンロードするには<https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>です。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-120">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="fc8ca-121">言語やフレームワークの選択</span><span class="sxs-lookup"><span data-stu-id="fc8ca-121">Language and framework choices</span></span>

<span data-ttu-id="fc8ca-122">Docker のアプリケーションと最近のほとんどの言語で Microsoft のツールを開発することができます。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-122">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="fc8ca-123">最初の一覧を次に示しますが、これに限定されません。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-123">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="fc8ca-124">.NET core と ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fc8ca-124">.NET Core and ASP.NET Core</span></span>

-   <span data-ttu-id="fc8ca-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="fc8ca-125">Node.js</span></span>

-   <span data-ttu-id="fc8ca-126">Golang</span><span class="sxs-lookup"><span data-stu-id="fc8ca-126">Golang</span></span>

-   <span data-ttu-id="fc8ca-127">Java</span><span class="sxs-lookup"><span data-stu-id="fc8ca-127">Java</span></span>

-   <span data-ttu-id="fc8ca-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="fc8ca-128">Ruby</span></span>

-   <span data-ttu-id="fc8ca-129">Python</span><span class="sxs-lookup"><span data-stu-id="fc8ca-129">Python</span></span>

<span data-ttu-id="fc8ca-130">基本的には、Linux または Windows で Docker でサポートされている最新の言語を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="fc8ca-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="fc8ca-131">[前](調整-高-スケーラビリティ-availability.md) [次へ] (docker-アプリ-内側のループ-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fc8ca-131">[Previous] (orchestrate-high-scalability-availability.md) [Next] (docker-apps-inner-loop-workflow.md)</span></span>
