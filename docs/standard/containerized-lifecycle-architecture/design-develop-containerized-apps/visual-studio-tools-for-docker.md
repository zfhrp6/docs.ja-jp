---
title: "Visual Studio Tools for Docker (Windows 上の Visual Studio) を使用"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0525633b23625d915fd447d438c6281fb14b3b46
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="32f99-104">Visual Studio Tools for Docker (Windows 上の Visual Studio) を使用</span><span class="sxs-lookup"><span data-stu-id="32f99-104">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="32f99-105">Visual Studio Code と Docker CLI を使用する場合は、Docker は、ワークフローに似ています、Visual Studio Tools を使用するときに、開発者ワークフロー (実際には、それが同じ Docker CLI) に基づくは作業を開始する方が簡単です、プロセスを簡略化し、大きい値を提供ビルドで生産性は、実行、およびタスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="32f99-105">The developer workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI (in fact, it is based on the same Docker CLI), but it is easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="32f99-106">実行し、f5 キーや ctrl キーを押しながら f5 キーを押して Visual Studio からのような単純な操作を使用して、コンテナーをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="32f99-106">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="32f99-107">さらに高いを実行し、1 つのコンテナーをデバッグすることだけでなく、Visual Studio 2017 するも実行およびデバッグできます (ソリューション全体) のコンテナーのグループ、同時に、ソリューション レベルで同じ docker compose.yml ファイルで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="32f99-107">Even more, with Visual Studio 2017, in addition to being able to run and debug a single container, you also can run and debug a group of containers (a whole solution) at the same time if they are defined in the same docker-compose.yml file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="32f99-108">ローカル環境を構成します。</span><span class="sxs-lookup"><span data-stu-id="32f99-108">Configuring your local environment</span></span>

<span data-ttu-id="32f99-109">Docker for Windows の最新のバージョンでは、これまでにアプリケーションを開発 Docker のため、次の参照で説明したように、セットアップは単純ですより簡単です。</span><span class="sxs-lookup"><span data-stu-id="32f99-109">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="32f99-110">**詳細情報:** Docker for Windows のインストールに関する詳細については、するには<https://docs.docker.com/docker-for-windows/>します。</span><span class="sxs-lookup"><span data-stu-id="32f99-110">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="32f99-111">Visual Studio 2015 を使用している場合は、更新プログラム 3 またはそれ以降のバージョンと Visual Studio Tools for Docker が必要です。</span><span class="sxs-lookup"><span data-stu-id="32f99-111">If you're using Visual Studio 2015, you must have Update 3 or a later version plus the Visual Studio Tools for Docker.</span></span>

<span data-ttu-id="32f99-112">**詳細情報:** Visual Studio をインストールする方法の詳細についてを参照してください[https://www.visualstudio.com/\ 製品/vs-2015-製品のエディション](https://www.visualstudio.com/products/vs-2015-product-editions)です。</span><span class="sxs-lookup"><span data-stu-id="32f99-112">**More info:** For instructions on installing Visual Studio, go to [https://www.visualstudio.com/\ products/vs-2015-product-editions](https://www.visualstudio.com/products/vs-2015-product-editions).</span></span>

<span data-ttu-id="32f99-113">Visual Studio Tools for Docker のインストールに関する詳細を参照するには、するには<http://aka.ms/vstoolsfordocker>と<https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>です。</span><span class="sxs-lookup"><span data-stu-id="32f99-113">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span></span>

<span data-ttu-id="32f99-114">Visual Studio 2017 を使用している場合、Docker のサポートは既にに含まれます。</span><span class="sxs-lookup"><span data-stu-id="32f99-114">If you're using Visual Studio 2017, Docker support is already included.</span></span>

## <a name="using-docker-tools-in-visual-studio-2015"></a><span data-ttu-id="32f99-115">Visual Studio 2015 での Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="32f99-115">Using Docker Tools in Visual Studio 2015</span></span>

<span data-ttu-id="32f99-116">Visual Studio Tools for Docker では、開発し、検証にローカルで、Docker コンテナー for Linux で Linux Docker ホストまたは VM、または Windows 上で直接、Windows コンテナーの一貫した方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="32f99-116">The Visual Studio Tools for Docker provides a consistent way to develop and validate locally your Docker containers for Linux in a Linux Docker host or VM, or your Windows Containers directly on Windows.</span></span>

<span data-ttu-id="32f99-117">1 つのコンテナーを使用している場合は、.NET Core プロジェクトに Docker のサポートを有効にはまずを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32f99-117">If you're using a single container, the first thing you need to begin is to turn on Docker support into your .NET Core project.</span></span> <span data-ttu-id="32f99-118">これを行うには、図 4-25 を示すように、プロジェクト ファイルを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="32f99-118">To do this, right-click your project file, as shown in Figure 4-25.</span></span>

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

<span data-ttu-id="32f99-120">図 4-25: をオンに Visual Studio プロジェクトの Docker のサポート</span><span class="sxs-lookup"><span data-stu-id="32f99-120">Figure 4-25: Turning on Docker support for your Visual Studio project</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="32f99-121">Visual Studio 2017 で Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="32f99-121">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="32f99-122">追加すると Docker のサポート サービス プロジェクト、ソリューション内 (図 4-26 を参照)、Visual Studio ではだけに DockerFile ファイルをプロジェクトに追加されませんも追加しているサービス セクションで、ソリューションの docker compose.yml ファイル (またはしていない場合は、ファイルを作成します。存在)。</span><span class="sxs-lookup"><span data-stu-id="32f99-122">When you add Docker support to a service project in your solution (see Figure 4-26), Visual Studio is not just adding a DockerFile file to your project, it also is adding a service section in your solution's docker-compose.yml files (or creating the files if they didn't exist).</span></span> <span data-ttu-id="32f99-123">Multicontainer、ソリューションの作成を開始する簡単な方法はdocker compose.yml ファイルを開いて、それらを他の機能も更新できます。</span><span class="sxs-lookup"><span data-stu-id="32f99-123">It's an easy way to begin composing your multicontainer solution; you then can open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image32.png)

<span data-ttu-id="32f99-124">Visual Studio 2017 プロジェクトでサポートされる Docker ソリューションの図 4-26: オンにします。</span><span class="sxs-lookup"><span data-stu-id="32f99-124">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

<span data-ttu-id="32f99-125">この操作は、プロジェクトに DockerFile を追加するだけでなく、グローバルの docker-compose.yml ソリューション レベルで設定するのに必要な構成の行のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="32f99-125">This action not only adds the DockerFile to your project, it also adds the required configuration lines of code to a global docker-compose.yml set at the solution level.</span></span>

<span data-ttu-id="32f99-126">できるサポートを有効に Docker で Visual Studio 2017、ASP.NET Core プロジェクトを作成するときに図 4-27 を示すようにします。</span><span class="sxs-lookup"><span data-stu-id="32f99-126">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![](./media/image33.png)

<span data-ttu-id="32f99-127">図 4-27: をオンにする Docker のサポート、プロジェクトを作成するときに</span><span class="sxs-lookup"><span data-stu-id="32f99-127">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="32f99-128">Visual Studio でソリューションに Docker のサポートを追加すると後も表示されます追加 docker compose.yml ファイルが、ソリューション エクスプ ローラーで新しいノード ツリー図 4-28 を示されています。</span><span class="sxs-lookup"><span data-stu-id="32f99-128">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in Solution Explorer with the added docker-compose.yml files, as depicted in Figure 4-28.</span></span>

![](./media/image34.PNG)

<span data-ttu-id="32f99-129">図 4-28: docker compose.yml ファイルこれでソリューション エクスプ ローラーで表示します。</span><span class="sxs-lookup"><span data-stu-id="32f99-129">Figure 4-28: docker-compose.yml files now display in Solution Explorer</span></span>

<span data-ttu-id="32f99-130">Multicontainer を展開することを実行すると、1 つの docker compose.yml ファイルを使用してアプリケーション docker の構成。環境 (運用と開発) と、実行によっての値をオーバーライドするために、Visual Studio が、それらのグループを追加するただし、型 (デバッグとリリース)。</span><span class="sxs-lookup"><span data-stu-id="32f99-130">You could deploy a multicontainer application by using a single docker-compose.yml file when you run docker-compose up; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="32f99-131">この機能は、後続の章でよく説明されます。</span><span class="sxs-lookup"><span data-stu-id="32f99-131">This capability will be better explained in later chapters.</span></span>

<span data-ttu-id="32f99-132">**詳細情報:** サービスの実装と Docker の Visual Studio Tools の使用の詳細については、次の記事を読み取る。</span><span class="sxs-lookup"><span data-stu-id="32f99-132">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="32f99-133">ビルド、デバッグ、更新、およびローカル Docker コンテナーでのアプリの更新: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="32f99-133">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="32f99-134">リモート Docker ホストに、ASP.NET のコンテナーの展開: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="32f99-134">Deploy an ASP.NET container to a remote Docker host: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="32f99-135">[前] (docker-アプリ-内側のループ-workflow.md) [次へ] (set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="32f99-135">[Previous] (docker-apps-inner-loop-workflow.md) [Next] (set-up-windows-containers-with-powershell.md)</span></span>
