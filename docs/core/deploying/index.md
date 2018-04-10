---
title: .NET Core アプリケーション展開
description: .NET Core アプリケーションの展開。
keywords: .NET, .NET Core, .NET Core 展開
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
ms.workload:
- dotnetcore
ms.openlocfilehash: 87a70ac246e37c646f9be578a03dda7037cfdd2d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-application-deployment"></a><span data-ttu-id="198ff-104">.NET Core アプリケーションの展開</span><span class="sxs-lookup"><span data-stu-id="198ff-104">.NET Core application deployment</span></span>

<span data-ttu-id="198ff-105">.NET Core アプリケーションに対して、次の 2 種類の展開を作成できます。</span><span class="sxs-lookup"><span data-stu-id="198ff-105">You can create two types of deployments for .NET Core applications:</span></span>

- <span data-ttu-id="198ff-106">フレームワークに依存する展開。</span><span class="sxs-lookup"><span data-stu-id="198ff-106">Framework-dependent deployment.</span></span> <span data-ttu-id="198ff-107">名前が示すように、フレームワークに依存する展開 (FDD) は、ターゲット システムに .NET Core のシステム全体の共有バージョンが存在することに依存します。</span><span class="sxs-lookup"><span data-stu-id="198ff-107">As the name implies, framework-dependent deployment (FDD) relies on the presence of a shared system-wide version of .NET Core on the target system.</span></span> <span data-ttu-id="198ff-108">.NET Core は既に存在するので、アプリは .NET Core のインストール間で移植することもできます。</span><span class="sxs-lookup"><span data-stu-id="198ff-108">Because .NET Core is already present, your app is also portable between installations of .NET Core.</span></span> <span data-ttu-id="198ff-109">アプリには、それ自体のコード、および .NET Core ライブラリの外部にあるサードパーティの依存関係のみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="198ff-109">Your app contains only its own code and any third-party dependencies that are outside of the .NET Core libraries.</span></span> <span data-ttu-id="198ff-110">FDD には、コマンドラインから [dotnet ユーティリティ](../tools/dotnet.md)を使って起動できる *.dll* ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="198ff-110">FDDs contain *.dll* files that can be launched by using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span> <span data-ttu-id="198ff-111">たとえば、`dotnet app.dll` は `app` という名前のアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="198ff-111">For example, `dotnet app.dll` runs an application named `app`.</span></span>

- <span data-ttu-id="198ff-112">自己完結型の展開。</span><span class="sxs-lookup"><span data-stu-id="198ff-112">Self-contained deployment.</span></span> <span data-ttu-id="198ff-113">FDD とは異なり、自己完結型の展開 (SCD) は、ターゲット システムに共有コンポーネントが存在することに依存しません。</span><span class="sxs-lookup"><span data-stu-id="198ff-113">Unlike FDD, a self-contained deployment (SCD) doesn't rely on the presence of shared components on the target system.</span></span> <span data-ttu-id="198ff-114">.NET Core ライブラリと .NET Core ランタイムの両方を含むすべてのコンポーネントがアプリケーションに含まれており、他の .NET Core アプリケーションから分離されています。</span><span class="sxs-lookup"><span data-stu-id="198ff-114">All components, including both the .NET Core libraries and the .NET Core runtime, are included with the application and are isolated from other .NET Core applications.</span></span> <span data-ttu-id="198ff-115">SCD には、プラットフォーム固有の .NET Core ホストの名前変更後のバージョンである実行可能ファイル (`app` という名前のアプリケーションに対する Windows プラットフォーム上の *app.exe* など)、および実際のアプリケーションである *.dll* ファイル (*app.dll* など) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="198ff-115">SCDs include an executable (such as *app.exe* on Windows platforms for an application named `app`), which is  a renamed version of the platform-specific .NET Core host, and a *.dll* file (such as *app.dll*), which is the actual application.</span></span>

## <a name="framework-dependent-deployments-fdd"></a><span data-ttu-id="198ff-116">フレームワークに依存する展開 (FDD)</span><span class="sxs-lookup"><span data-stu-id="198ff-116">Framework-dependent deployments (FDD)</span></span>

<span data-ttu-id="198ff-117">FDD では、アプリ、およびサードパーティの依存関係のみを展開します。</span><span class="sxs-lookup"><span data-stu-id="198ff-117">For an FDD, you deploy only your app and any third-party dependencies.</span></span> <span data-ttu-id="198ff-118">アプリは、ターゲット システムに存在する .NET Core のバージョンを使うので、.NET Core を展開する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="198ff-118">You don't have to deploy .NET Core, since your app will use the version of .NET Core that's present on the target system.</span></span> <span data-ttu-id="198ff-119">これは、.NET Core アプリの既定の展開モデルです。</span><span class="sxs-lookup"><span data-stu-id="198ff-119">This is the default deployment model for .NET Core apps.</span></span>

### <a name="why-create-a-framework-dependent-deployment"></a><span data-ttu-id="198ff-120">フレームワークに依存する展開を作成する理由</span><span class="sxs-lookup"><span data-stu-id="198ff-120">Why create a framework-dependent deployment?</span></span>

<span data-ttu-id="198ff-121">FDD の展開には、次のいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="198ff-121">Deploying an FDD has a number of advantages:</span></span>

- <span data-ttu-id="198ff-122">.NET Core アプリが実行されるターゲットのオペレーティング システムを事前に定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="198ff-122">You don't have to define the target operating systems that your .NET Core app will run on in advance.</span></span> <span data-ttu-id="198ff-123">.NET Core は、オペレーティング システムに関係なく実行可能ファイルとライブラリに共通の PE ファイル形式を使用するので、.NET Core は、基になるオペレーティング システムに関係なくアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="198ff-123">Because .NET Core uses a common PE file format for executables and libraries regardless of operating system, .NET Core can execute your app regardless of the underlying operating system.</span></span> <span data-ttu-id="198ff-124">PE ファイル形式の詳細については、「[.NET Assembly File Format](../../standard/assembly-format.md)」 (.NET アセンブリのファイル形式) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="198ff-124">For more information on the PE file format, see [.NET Assembly File Format](../../standard/assembly-format.md).</span></span>

- <span data-ttu-id="198ff-125">展開パッケージは小サイズです。</span><span class="sxs-lookup"><span data-stu-id="198ff-125">The size of your deployment package is small.</span></span> <span data-ttu-id="198ff-126">.NET Core 自体ではなく、アプリとその依存関係のみを展開します。</span><span class="sxs-lookup"><span data-stu-id="198ff-126">You only deploy your app and its dependencies, not .NET Core itself.</span></span>

- <span data-ttu-id="198ff-127">複数のアプリが、同じ .NET Core インストールを使用します。これにより、ホスト システム上のディスク領域とメモリ使用量の両方が削減されます。</span><span class="sxs-lookup"><span data-stu-id="198ff-127">Multiple apps use the same .NET Core installation, which reduces both disk space and memory usage on host systems.</span></span>

<span data-ttu-id="198ff-128">次のいくつかの短所もあります。</span><span class="sxs-lookup"><span data-stu-id="198ff-128">There are also a few disadvantages:</span></span>

- <span data-ttu-id="198ff-129">ターゲットとする .NET Core のバージョンまたはそれ以降のバージョンがホスト システムに既にインストールされている場合にのみ、アプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="198ff-129">Your app can run only if the version of .NET Core that you target, or a later version, is already installed on the host system.</span></span>

- <span data-ttu-id="198ff-130">将来のリリースでは、ユーザーの認識なしに .NET Core ランタイムおよびライブラリが変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="198ff-130">It's possible for the .NET Core runtime and libraries to change without your knowledge in future releases.</span></span> <span data-ttu-id="198ff-131">まれなケースでは、アプリのビヘイビアーが変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="198ff-131">In rare cases, this may change the behavior of your app.</span></span>

## <a name="self-contained-deployments-scd"></a><span data-ttu-id="198ff-132">自己完結型の展開 (SCD)</span><span class="sxs-lookup"><span data-stu-id="198ff-132">Self-contained deployments (SCD)</span></span>

<span data-ttu-id="198ff-133">自己完結型の展開では、アプリおよびすべての必要なサードパーティの依存関係と共に、アプリのビルドに使った .NET Core のバージョンも展開します。</span><span class="sxs-lookup"><span data-stu-id="198ff-133">For a self-contained deployment, you deploy your app and any required third-party dependencies along with the version of .NET Core that you used to build the app.</span></span> <span data-ttu-id="198ff-134">SCD の作成には、さまざまなプラットフォーム上の [.NET Core のネイティブの依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)は含まれないので、アプリが実行する前にこれらが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="198ff-134">Creating an SCD doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) on various platforms, so these must be present before the app runs.</span></span>

<span data-ttu-id="198ff-135">FDD および SCD の展開では別個のホスト実行可能ファイルを使用するため、発行元のシグネチャで SCD のホスト実行可能ファイルに署名できます。</span><span class="sxs-lookup"><span data-stu-id="198ff-135">FDD and SCD deployments use separate host executables, so you can sign a host executable for an SCD with your publisher signature.</span></span>

### <a name="why-deploy-a-self-contained-deployment"></a><span data-ttu-id="198ff-136">自己完結型の展開を展開する理由</span><span class="sxs-lookup"><span data-stu-id="198ff-136">Why deploy a self-contained deployment?</span></span>

<span data-ttu-id="198ff-137">自己完結型の展開を展開するのには、次の 2 つの主な利点があります。</span><span class="sxs-lookup"><span data-stu-id="198ff-137">Deploying a Self-contained deployment has two major advantages:</span></span>

- <span data-ttu-id="198ff-138">アプリで展開されている .NET Core のバージョンは、あなただけがコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="198ff-138">You have sole control of the version of .NET Core that is deployed with your app.</span></span> <span data-ttu-id="198ff-139">.NET Core を操作できるのはあなただけです。</span><span class="sxs-lookup"><span data-stu-id="198ff-139">.NET Core can be serviced only by you.</span></span>

- <span data-ttu-id="198ff-140">ターゲット システムが実行できる .NET Core のバージョンを提供しているので、ターゲット システムで .NET Core アプリを確実に実行できます。</span><span class="sxs-lookup"><span data-stu-id="198ff-140">You can be assured that the target system can run your .NET Core app, since you're providing the version of .NET Core that it will run on.</span></span>

<span data-ttu-id="198ff-141">また、次のいくつかの短所もあります。</span><span class="sxs-lookup"><span data-stu-id="198ff-141">It also has a number of disadvantages:</span></span>

- <span data-ttu-id="198ff-142">.NET Core が展開パッケージに含まれているので、展開パッケージをビルドするターゲット プラットフォームを事前に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="198ff-142">Because .NET Core is included in your deployment package, you must select the target platforms for which you build deployment packages in advance.</span></span>

- <span data-ttu-id="198ff-143">.NET Core だけでなくアプリおよびそのサードパーティの依存関係を含める必要があるので、展開パッケージは比較的大きくなります。</span><span class="sxs-lookup"><span data-stu-id="198ff-143">The size of your deployment package is relatively large, since you have to include .NET Core as well as your app and its third-party dependencies.</span></span>

- <span data-ttu-id="198ff-144">多数の自己完結型の .NET Core アプリをシステムに展開すると、各アプリが .NET Core ファイルを複製するので、非常に多くのディスク領域を使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="198ff-144">Deploying numerous self-contained .NET Core apps to a system can consume significant amounts of disk space, since each app duplicates .NET Core files.</span></span>

## <a name="step-by-step-examples"></a><span data-ttu-id="198ff-145">手順の例</span><span class="sxs-lookup"><span data-stu-id="198ff-145">Step-by-step examples</span></span>

<span data-ttu-id="198ff-146">CLI ツールで .NET Core アプリを展開する手順の例については、「[Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md)」(CLI ツールで .NET Core アプリを展開する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="198ff-146">For step-by-step examples of deploying .NET Core apps with CLI tools, see [Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md).</span></span> <span data-ttu-id="198ff-147">Visual Studio で .NET Core アプリを展開する手順の例については、「[Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md)」(Visual Studio で .NET Core アプリを展開する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="198ff-147">For step-by-step examples of deploying .NET Core apps with Visual Studio, see [Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md).</span></span> <span data-ttu-id="198ff-148">各トピックには、次の展開の例が含まれます。</span><span class="sxs-lookup"><span data-stu-id="198ff-148">Each topic includes examples of the following deployments:</span></span>

- <span data-ttu-id="198ff-149">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="198ff-149">Framework-dependent deployment</span></span>
- <span data-ttu-id="198ff-150">サードパーティの依存関係を含む、フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="198ff-150">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="198ff-151">自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="198ff-151">Self-contained deployment</span></span>
- <span data-ttu-id="198ff-152">サードパーティの依存関係を含む、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="198ff-152">Self-contained deployment with third-party dependencies</span></span>

# <a name="see-also"></a><span data-ttu-id="198ff-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="198ff-153">See also</span></span>

<span data-ttu-id="198ff-154">[CLI ツールで .NET Core アプリを展開する](deploy-with-cli.md) </span><span class="sxs-lookup"><span data-stu-id="198ff-154">[Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md) </span></span>  
<span data-ttu-id="198ff-155">[Visual Studio で .NET Core アプリを展開する](deploy-with-vs.md) </span><span class="sxs-lookup"><span data-stu-id="198ff-155">[Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md) </span></span>  
<span data-ttu-id="198ff-156">[パッケージ、メタパッケージ、フレームワーク](../packages.md) </span><span class="sxs-lookup"><span data-stu-id="198ff-156">[Packages, Metapackages and Frameworks](../packages.md) </span></span>  
[<span data-ttu-id="198ff-157">.NET Core のランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="198ff-157">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
