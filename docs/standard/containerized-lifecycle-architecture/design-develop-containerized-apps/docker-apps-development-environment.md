---
title: "Docker アプリの開発環境"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: eedba16136ad394bda45cc871944f9b876c8ee38
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2017
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="2944f-104">Docker アプリの開発環境</span><span class="sxs-lookup"><span data-stu-id="2944f-104">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="2944f-105">開発ツールの選択: IDE やエディター</span><span class="sxs-lookup"><span data-stu-id="2944f-105">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="2944f-106">かにかかわらずする場合、完全かつ強力な IDE または軽量とアジャイル エディターでは、Microsoft に対応する際に Docker アプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="2944f-106">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="2944f-107">Visual Studio Code と Docker CLI (Mac、Linux、および Windows 用のクロスプラット フォーム ツール)</span><span class="sxs-lookup"><span data-stu-id="2944f-107">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="2944f-108">任意の開発言語をサポートする、軽量のクロスプラット フォーム エディターを使用する場合は、Visual Studio Code と Docker CLI を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2944f-108">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="2944f-109">これらの製品では、簡単かつ堅牢なエクスペリエンスを合理化開発者ワークフローにとって重要となるを提供します。</span><span class="sxs-lookup"><span data-stu-id="2944f-109">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="2944f-110">"Docker の Mac"または"Docker for Windows の"(開発環境) をインストールすると、Docker の開発者は、Windows または Linux (ランタイム環境) の両方のアプリをビルドするのに 1 つの Docker CLI を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2944f-110">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="2944f-111">さらに、Visual Studio Code エディターから Docker コマンドを実行するには、Dockerfile とショートカット タスク用の IntelliSense と Docker の拡張機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2944f-111">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="2944f-112">Visual Studio のコードをダウンロードするには<https://code.visualstudio.com/download>です。</span><span class="sxs-lookup"><span data-stu-id="2944f-112">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="2944f-113">Mac および Windows の Docker をダウンロードするには<http://www.docker.com/products/docker>です。</span><span class="sxs-lookup"><span data-stu-id="2944f-113">To download Docker for Mac and Windows, go to <http://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="2944f-114">Docker ツールと visual Studio</span><span class="sxs-lookup"><span data-stu-id="2944f-114">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="2944f-115">Visual Studio 2015 を使用している場合は、"Docker Tools for Visual Studio です"のアドオン ツールをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="2944f-115">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="2944f-116">Visual Studio 2017 の Docker ツールに付属でビルドされた既にです。</span><span class="sxs-lookup"><span data-stu-id="2944f-116">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="2944f-117">どちらの場合に、開発し、実行、および選択した Docker 環境内で直接、アプリケーションを検証することができます。</span><span class="sxs-lookup"><span data-stu-id="2944f-117">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="2944f-118">F5 キーを押して、Docker に直接、アプリケーション (1 つのコンテナーまたは複数のコンテナー) はデバッグは、ホストまたは Ctrl + f5 キーを押して編集し、コンテナーを再構築しなくてもアプリを更新します。</span><span class="sxs-lookup"><span data-stu-id="2944f-118">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="2944f-119">これは、Linux または Windows の Docker コンテナーを作成する Windows 開発者にとって最も簡単で強力な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="2944f-119">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="2944f-120">Visual Studio の Docker のツールをダウンロードするには<https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>です。</span><span class="sxs-lookup"><span data-stu-id="2944f-120">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="2944f-121">言語やフレームワークの選択</span><span class="sxs-lookup"><span data-stu-id="2944f-121">Language and framework choices</span></span>

<span data-ttu-id="2944f-122">Docker のアプリケーションと最近のほとんどの言語で Microsoft のツールを開発することができます。</span><span class="sxs-lookup"><span data-stu-id="2944f-122">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="2944f-123">最初の一覧を次に示しますが、これに限定されません。</span><span class="sxs-lookup"><span data-stu-id="2944f-123">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="2944f-124">.NET core と ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2944f-124">.NET Core and ASP.NET Core</span></span>

-   <span data-ttu-id="2944f-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="2944f-125">Node.js</span></span>

-   <span data-ttu-id="2944f-126">Golang</span><span class="sxs-lookup"><span data-stu-id="2944f-126">Golang</span></span>

-   <span data-ttu-id="2944f-127">Java</span><span class="sxs-lookup"><span data-stu-id="2944f-127">Java</span></span>

-   <span data-ttu-id="2944f-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="2944f-128">Ruby</span></span>

-   <span data-ttu-id="2944f-129">Python</span><span class="sxs-lookup"><span data-stu-id="2944f-129">Python</span></span>

<span data-ttu-id="2944f-130">基本的には、Linux または Windows で Docker でサポートされている最新の言語を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2944f-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2944f-131">[前](調整-高-スケーラビリティ-availability.md) [次へ] (docker-アプリ-内側のループ-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2944f-131">[Previous] (orchestrate-high-scalability-availability.md) [Next] (docker-apps-inner-loop-workflow.md)</span></span>
