---
title: "Docker ベースのアプリケーションの開発プロセス"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker ベースのアプリケーションの開発プロセス"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc91c7d5e2e27602afd6d583bf09adae3caea59e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="11e55-104">Docker ベースのアプリケーションの開発プロセス</span><span class="sxs-lookup"><span data-stu-id="11e55-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="11e55-105">*Visual Studio と Visual Studio Tools for Docker を使用して IDE に重点を置くか、Docker CLI と Visual Studio Code を使用して CLI/エディターに重点を置くか、好みの方法でコンテナー化された .NET アプリケーションを開発します。*</span><span class="sxs-lookup"><span data-stu-id="11e55-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="11e55-106">Docker アプリの開発環境</span><span class="sxs-lookup"><span data-stu-id="11e55-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="11e55-107">開発ツールの選択: IDE またはエディター</span><span class="sxs-lookup"><span data-stu-id="11e55-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="11e55-108">完全で強力な IDE または軽量でアジャイルなエディターのどちらを選んでも、Microsoft では Docker アプリケーションの開発に使用できるツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="11e55-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="11e55-109">**Visual Studio (Windows 版)**。</span><span class="sxs-lookup"><span data-stu-id="11e55-109">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="11e55-110">Docker ベースのアプリケーションを開発するには、Docker 用のツールが既に組み込まれている Visual Studio 2017 以降のバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="11e55-110">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="11e55-111">Tools for Docker を使用して、ターゲットの Docker 環境で直接アプリケーションの開発、実行、および検証ができます。</span><span class="sxs-lookup"><span data-stu-id="11e55-111">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="11e55-112">F5 キーを押すと、Docker ホスト内で直接アプリケーション (1 つのコンテナー、または複数のコンテナー) を実行してデバックできます。または、CTRL キーを押しながら F5 キーを押すと、コンテナーを再構築しなくても、アプリケーションを編集して更新できます。</span><span class="sxs-lookup"><span data-stu-id="11e55-112">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="11e55-113">これは、Docker ベース アプリを開発する場合の最も強力な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="11e55-113">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="11e55-114">**Visual Studio for Mac**。</span><span class="sxs-lookup"><span data-stu-id="11e55-114">**Visual Studio for Mac**.</span></span> <span data-ttu-id="11e55-115">これは、macOS 上で実行する、Docker ベースのアプリケーションの開発をサポートする Xamarin Studio の進化版の IDE です。</span><span class="sxs-lookup"><span data-stu-id="11e55-115">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="11e55-116">これは、強力な IDE を使用したい Mac コンピューターで作業する開発者にとって好ましい選択肢です。</span><span class="sxs-lookup"><span data-stu-id="11e55-116">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="11e55-117">**Visual Studio Code と Docker CLI**。</span><span class="sxs-lookup"><span data-stu-id="11e55-117">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="11e55-118">任意の開発言語をサポートする軽量なクロスプラット フォーム エディターを選択すると、Microsoft Visual Studio Code (VS Code) と Docker CLI を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="11e55-118">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="11e55-119">これは、Mac、Linux、および Windows のクロスプラット フォーム開発アプローチです。</span><span class="sxs-lookup"><span data-stu-id="11e55-119">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="11e55-120">[Docker Community Edition (CE)](https://www.docker.com/community-edition) ツールをインストールすることで、1 つの Docker CLI を使用して Windows と Linux の両方のアプリを構築することができます。</span><span class="sxs-lookup"><span data-stu-id="11e55-120">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="11e55-121">さらに、Visual Studio Code は、Dockerfiles の IntelliSense などの Docker の拡張機能や、エディターから Docker コマンドを実行するショートカット タスクをサポートします。</span><span class="sxs-lookup"><span data-stu-id="11e55-121">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="11e55-122">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="11e55-122">Additional resources</span></span>

-   <span data-ttu-id="11e55-123">**Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="11e55-123">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="11e55-124">**Visual Studio Code**。</span><span class="sxs-lookup"><span data-stu-id="11e55-124">**Visual Studio Code**.</span></span> <span data-ttu-id="11e55-125">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="11e55-125">Official site.</span></span>
    [<span data-ttu-id="11e55-126">*https://code.visualstudio.com/download*</span><span class="sxs-lookup"><span data-stu-id="11e55-126">*https://code.visualstudio.com/download*</span></span>](https://code.visualstudio.com/download)

-   <span data-ttu-id="11e55-127">**Mac および Windows の Docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="11e55-127">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="11e55-128">.NET 言語および Docker コンテナーのフレームワーク</span><span class="sxs-lookup"><span data-stu-id="11e55-128">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="11e55-129">このガイドの前のセクションで触れたように、Docker コンテナー化された NET アプリケーションを開発する際に、.NET Framework、.NET Core、またはオープン ソースの Mono プロジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="11e55-129">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="11e55-130">Linux または Windows コンテナーをターゲットにする場合、使用している .NET Framework に応じて、C\#、F\#、または Visual Basic で開発できます。</span><span class="sxs-lookup"><span data-stu-id="11e55-130">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="11e55-131">.NET 言語の詳細については、ブログ投稿「[The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/)」 (.NET 言語戦略) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11e55-131">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="11e55-132">[前へ] (../architect-microservice-container-applications/using-azure-service-fabric.md) [次へ] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="11e55-132">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
