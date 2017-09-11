---
title: "Docker でのコンソール アプリケーションの実行"
description: "既存の .NET Framework コンソール アプリケーションを Windows Docker コンテナーで実行する方法について説明します。"
author: spboyer
keywords: ".NET, コンテナー, コンソール, アプリケーション"
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2fdce1e131eaa0d6952b2910f73105f097487711
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---

# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="1e773-104">Windows コンテナーでのコンソール アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="1e773-104">Running console applications in Windows containers</span></span>

<span data-ttu-id="1e773-105">コンソール アプリケーションは、状態の単純なクエリから、実行時間の長いドキュメント イメージ処理タスクまで、さまざまな目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e773-105">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="1e773-106">いずれの場合にも、これらのアプリケーションを起動およびスケーリングする機能は、ハードウェアの取得、起動時間、または複数インスタンスの実行による制約を受けます。</span><span class="sxs-lookup"><span data-stu-id="1e773-106">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="1e773-107">Docker コンテナーと Windows Server コンテナーを使用するようにコンソール アプリケーションを移行すると、これらのアプリケーションをクリーンな状態から起動でき、操作を実行してからクリーンにシャットダウンできます。</span><span class="sxs-lookup"><span data-stu-id="1e773-107">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="1e773-108">このトピックでは、コンソール アプリケーションを Windows ベースのコンテナーに移行し、PowerShell スクリプトを使用してこのアプリケーションを起動するために必要な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="1e773-108">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="1e773-109">サンプルのコンソール アプリケーションは、引数 (この場合は質問) を受け取ってランダムな回答を返す単純な例です。</span><span class="sxs-lookup"><span data-stu-id="1e773-109">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="1e773-110">この例では、`customer_id` を受け取ってその税金を処理したり、`image_url` 引数に対してサムネイルを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="1e773-110">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="1e773-111">回答に加えて、`Environment.MachineName` が応答に追加されており、アプリケーションの実行をローカルで行う場合と Windows コンテナーで行う場合の違いが示されます。</span><span class="sxs-lookup"><span data-stu-id="1e773-111">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="1e773-112">アプリケーションをローカルで実行する場合はローカル コンピューター名が返され、Windows コンテナーで実行する場合はコンテナーのセッション ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="1e773-112">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="1e773-113">[完全な例](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator)は GitHub の dotnet/docs レポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="1e773-113">The [complete example](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="1e773-114">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e773-114">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="1e773-115">アプリケーションをコンテナーに移行する作業を開始する前に、いくつかの Docker 用語を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e773-115">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> <span data-ttu-id="1e773-116">*Docker イメージ*は、オペレーティング システム (OS)、システム コンポーネント、アプリケーションなど、実行中のコンテナー用の環境を定義する読み取り専用のテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="1e773-116">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="1e773-117">Docker イメージの重要な特徴の 1 つは、イメージが基本イメージから構成されることです。</span><span class="sxs-lookup"><span data-stu-id="1e773-117">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="1e773-118">新しい各イメージが、特徴の小さなセットを既存のイメージに追加します。</span><span class="sxs-lookup"><span data-stu-id="1e773-118">Each new image adds a small set of features to an existing image.</span></span> 

> <span data-ttu-id="1e773-119">*Docker コンテナー*は、イメージの実行インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="1e773-119">A *Docker container* is a running instance of an image.</span></span> 

<span data-ttu-id="1e773-120">さまざまなコンテナーで同じイメージを実行することで、アプリケーションをスケーリングします。</span><span class="sxs-lookup"><span data-stu-id="1e773-120">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="1e773-121">概念的には、複数のホストで同じアプリケーションを実行する場合に似ています。</span><span class="sxs-lookup"><span data-stu-id="1e773-121">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="1e773-122">Docker アーキテクチャの詳細については、Docker サイトの「[Docker Overview](https://docs.docker.com/engine/understanding-docker/)」 (Docker の概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e773-122">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span> 

<span data-ttu-id="1e773-123">コンソール アプリケーションの移行には、次のいくつかの手順を要します。</span><span class="sxs-lookup"><span data-stu-id="1e773-123">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="1e773-124">アプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="1e773-124">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="1e773-125">イメージの Dockerfile の作成</span><span class="sxs-lookup"><span data-stu-id="1e773-125">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="1e773-126">Docker コンテナーをビルドして実行するプロセス</span><span class="sxs-lookup"><span data-stu-id="1e773-126">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="1e773-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="1e773-127">Prerequisites</span></span>
<span data-ttu-id="1e773-128">Windows コンテナーは、[Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) または [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server) でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1e773-128">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="1e773-129">Windows Server 2016 を使用している場合、Docker for Windows インストーラーによってこの機能は有効にならないので、コンテナーを手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e773-129">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="1e773-130">OS に対してすべての更新プログラムが実行されていることを確認してから、「[Container Host Deployment](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment)」 (コンテナー ホストの展開) の記事にある説明に従って、コンテナーおよび Docker 機能をインストールします。</span><span class="sxs-lookup"><span data-stu-id="1e773-130">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) article to install the containers and Docker features.</span></span>

<span data-ttu-id="1e773-131">Windows コンテナーをサポートするには、Docker for Windows バージョン 1.12 Beta 26 以降が必要になります。</span><span class="sxs-lookup"><span data-stu-id="1e773-131">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="1e773-132">既定では、Docker は Linux ベースのコンテナーを有効にします。Windows コンテナーに切り替えるには、システム トレイで Docker アイコンを右クリックし、**[Switch to Windows containers]** (Windows コンテナーに切り替え) を選択します。</span><span class="sxs-lookup"><span data-stu-id="1e773-132">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="1e773-133">Docker は変更プロセスを実行します。この際、再起動が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e773-133">Docker will run the process to change and a restart may be required.</span></span>

![Windows コンテナー](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a><span data-ttu-id="1e773-135">アプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="1e773-135">Building the application</span></span>
<span data-ttu-id="1e773-136">通常、コンソール アプリケーションは、インストーラー、FTP、またはファイル共有の展開を通して配布されます。</span><span class="sxs-lookup"><span data-stu-id="1e773-136">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="1e773-137">コンテナーへの展開時には、資産をコンパイルし、Docker イメージを作成するときに使用できる場所にステージングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e773-137">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="1e773-138">*Build.ps1* で、スクリプトは資産のビルド タスクを実行するために、[MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) を使用してアプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="1e773-138">In *build.ps1*, the script uses [MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="1e773-139">必要な資産を最終処理するために MSBuild に渡されるいくつかのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="1e773-139">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="1e773-140">コンパイルするプロジェクト ファイルまたはソリューションの名前、出力の場所、および構成 (Release または Debug) です。</span><span class="sxs-lookup"><span data-stu-id="1e773-140">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="1e773-141">`Invoke-MSBuild` への呼び出しで、`OutputPath` は **publish** に設定され、`Configuration` は **Release** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e773-141">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span> 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="1e773-142">Dockerfile の作成</span><span class="sxs-lookup"><span data-stu-id="1e773-142">Creating the Dockerfile</span></span>
<span data-ttu-id="1e773-143">コンソールの .NET Framework アプリケーションに使用される基本イメージは `microsoft/windowsservercore` であり、[Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/) で一般公開されています。</span><span class="sxs-lookup"><span data-stu-id="1e773-143">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="1e773-144">この基本イメージには、Windows Server 2016、.NET Framework 4.6.2 の最小限のインストールが含まれており、Windows コンテナーの基本 OS イメージとして機能します。</span><span class="sxs-lookup"><span data-stu-id="1e773-144">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
<span data-ttu-id="1e773-145">Dockerfile の最初の行は、[`FROM`](https://docs.docker.com/engine/reference/builder/#/from) 命令を使用して基本イメージを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e773-145">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="1e773-146">次に、ファイル内の [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) は、**publish** フォルダーからコンテナーのルート フォルダーにアプリケーション資産をコピーします。最後に、イメージの [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) を設定することで、これがコンテナーの開始時に実行されるコマンドまたはアプリケーションであることを示します。</span><span class="sxs-lookup"><span data-stu-id="1e773-146">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span> 

## <a name="creating-the-image"></a><span data-ttu-id="1e773-147">イメージの作成</span><span class="sxs-lookup"><span data-stu-id="1e773-147">Creating the image</span></span>
<span data-ttu-id="1e773-148">Docker イメージを作成するには、*build.ps1* スクリプトに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e773-148">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="1e773-149">スクリプトを実行すると、「[アプリケーションのビルド](#building-the-application)」セクションで定義した MSBuild からコンパイルされた資産を使用して、`console-random-answer-generator` イメージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e773-149">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="1e773-150">PowerShell コマンド プロンプトから、`.\build.ps1` を使用してスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e773-150">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="1e773-151">ビルドが完了したら、コマンドラインまたは PowerShell プロンプトから `docker images` コマンドを使用します。イメージが作成され、実行できる状態であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1e773-151">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="1e773-152">コンテナーの実行</span><span class="sxs-lookup"><span data-stu-id="1e773-152">Running the container</span></span>
<span data-ttu-id="1e773-153">コンテナーは、コマンドラインから Docker コマンドを使用して起動できます。</span><span class="sxs-lookup"><span data-stu-id="1e773-153">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="1e773-154">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1e773-154">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="1e773-155">PowerShell から `docker ps -a` コマンドを実行すると、コンテナーがまだ存在することがわかります。</span><span class="sxs-lookup"><span data-stu-id="1e773-155">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

<span data-ttu-id="1e773-156">STATUS 列は、"約 1 分前" にアプリケーションが完了しており、シャットダウンできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="1e773-156">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="1e773-157">このコマンドを 100 回実行すれば、実行する作業のない 100 個のコンテナーが静的な状態で残ります。</span><span class="sxs-lookup"><span data-stu-id="1e773-157">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="1e773-158">最初のシナリオでは、理想的な操作は、作業を実行してからシャットダウンまたはクリーンアップを行うことでした。</span><span class="sxs-lookup"><span data-stu-id="1e773-158">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="1e773-159">そのワークフローを実行するには、`--rm` オプションを `docker run` コマンドに追加することで、`Exited` シグナルを受け取ったらすぐにコンテナーが削除されるようにします。</span><span class="sxs-lookup"><span data-stu-id="1e773-159">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="1e773-160">このオプションを指定してコマンドを実行してから、`docker ps -a` コマンドの出力を見ると、コンテナー ID (`Environment.MachineName`) が一覧に表示されていません。</span><span class="sxs-lookup"><span data-stu-id="1e773-160">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="1e773-161">PowerShell を使用したコンテナーの実行</span><span class="sxs-lookup"><span data-stu-id="1e773-161">Running the container using PowerShell</span></span>
<span data-ttu-id="1e773-162">サンプル プロジェクト ファイルには、PowerShell を使用して引数を受け入れるアプリケーションを実行する方法の例として、*run.ps1* も含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e773-162">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="1e773-163">実行するには、PowerShell を開き、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1e773-163">To run, open PowerShell and use the following command:</span></span>

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="1e773-164">まとめ</span><span class="sxs-lookup"><span data-stu-id="1e773-164">Summary</span></span>
<span data-ttu-id="1e773-165">Dockerfile を追加し、アプリケーションを発行するだけで、.NET Framework コンソール アプリケーションをコンテナー化できます。これにより、アプリケーション コードを全く変更せずに、複数のインスタンス、クリーンな起動と停止、および Windows Server 2016 のより多くの機能を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1e773-165">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>

