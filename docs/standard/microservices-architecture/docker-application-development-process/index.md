---
title: Docker ベースのアプリケーションの開発プロセス
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker ベースのアプリケーションの開発プロセス'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 881817f4f1007edad85eefb9002d56764cbf2a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="630bf-103">Docker ベースのアプリケーションの開発プロセス</span><span class="sxs-lookup"><span data-stu-id="630bf-103">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="630bf-104">*Visual Studio と Visual Studio Tools for Docker を使用して IDE に重点を置くか、Docker CLI と Visual Studio Code を使用して CLI/エディターに重点を置くか、好みの方法でコンテナー化された .NET アプリケーションを開発します。*</span><span class="sxs-lookup"><span data-stu-id="630bf-104">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="630bf-105">Docker アプリの開発環境</span><span class="sxs-lookup"><span data-stu-id="630bf-105">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="630bf-106">開発ツールの選択: IDE またはエディター</span><span class="sxs-lookup"><span data-stu-id="630bf-106">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="630bf-107">完全で強力な IDE または軽量でアジャイルなエディターのどちらを選んでも、Microsoft では Docker アプリケーションの開発に使用できるツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="630bf-107">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="630bf-108">**Visual Studio (Windows 版)**。</span><span class="sxs-lookup"><span data-stu-id="630bf-108">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="630bf-109">Docker ベースのアプリケーションを開発するには、Docker 用のツールが既に組み込まれている Visual Studio 2017 以降のバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="630bf-109">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="630bf-110">Tools for Docker を使用して、ターゲットの Docker 環境で直接アプリケーションの開発、実行、および検証ができます。</span><span class="sxs-lookup"><span data-stu-id="630bf-110">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="630bf-111">F5 キーを押すと、Docker ホスト内で直接アプリケーション (1 つのコンテナー、または複数のコンテナー) を実行してデバックできます。または、CTRL キーを押しながら F5 キーを押すと、コンテナーを再構築しなくても、アプリケーションを編集して更新できます。</span><span class="sxs-lookup"><span data-stu-id="630bf-111">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="630bf-112">これは、Docker ベース アプリを開発する場合の最も強力な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="630bf-112">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="630bf-113">**Visual Studio for Mac**。</span><span class="sxs-lookup"><span data-stu-id="630bf-113">**Visual Studio for Mac**.</span></span> <span data-ttu-id="630bf-114">これは、macOS 上で実行する、Docker ベースのアプリケーションの開発をサポートする Xamarin Studio の進化版の IDE です。</span><span class="sxs-lookup"><span data-stu-id="630bf-114">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="630bf-115">これは、強力な IDE を使用したい Mac コンピューターで作業する開発者にとって好ましい選択肢です。</span><span class="sxs-lookup"><span data-stu-id="630bf-115">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="630bf-116">**Visual Studio Code と Docker CLI**。</span><span class="sxs-lookup"><span data-stu-id="630bf-116">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="630bf-117">任意の開発言語をサポートする軽量なクロスプラット フォーム エディターを選択すると、Microsoft Visual Studio Code (VS Code) と Docker CLI を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="630bf-117">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="630bf-118">これは、Mac、Linux、および Windows のクロスプラット フォーム開発アプローチです。</span><span class="sxs-lookup"><span data-stu-id="630bf-118">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="630bf-119">[Docker Community Edition (CE)](https://www.docker.com/community-edition) ツールをインストールすることで、1 つの Docker CLI を使用して Windows と Linux の両方のアプリを構築することができます。</span><span class="sxs-lookup"><span data-stu-id="630bf-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="630bf-120">さらに、Visual Studio Code は、Dockerfiles の IntelliSense などの Docker の拡張機能や、エディターから Docker コマンドを実行するショートカット タスクをサポートします。</span><span class="sxs-lookup"><span data-stu-id="630bf-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="630bf-121">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="630bf-121">Additional resources</span></span>

-   <span data-ttu-id="630bf-122">**Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="630bf-122">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="630bf-123">**Visual Studio Code**。</span><span class="sxs-lookup"><span data-stu-id="630bf-123">**Visual Studio Code**.</span></span> <span data-ttu-id="630bf-124">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="630bf-124">Official site.</span></span>
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   <span data-ttu-id="630bf-125">**Mac および Windows の Docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="630bf-125">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="630bf-126">.NET 言語および Docker コンテナーのフレームワーク</span><span class="sxs-lookup"><span data-stu-id="630bf-126">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="630bf-127">このガイドの前のセクションで触れたように、Docker コンテナー化された NET アプリケーションを開発する際に、.NET Framework、.NET Core、またはオープン ソースの Mono プロジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="630bf-127">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="630bf-128">Linux または Windows コンテナーをターゲットにする場合、使用している .NET Framework に応じて、C\#、F\#、または Visual Basic で開発できます。</span><span class="sxs-lookup"><span data-stu-id="630bf-128">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="630bf-129">.NET 言語の詳細については、ブログ投稿「[The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/)」 (.NET 言語戦略) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="630bf-129">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="630bf-130">[前へ] (../architect-microservice-container-applications/using-azure-service-fabric.md) [次へ] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="630bf-130">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
