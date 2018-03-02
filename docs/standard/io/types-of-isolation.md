---
title: "分離のタイプ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a7e9b28601970aecd139d2027bc0ebc73e869fc
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="types-of-isolation"></a><span data-ttu-id="c2091-102">分離のタイプ</span><span class="sxs-lookup"><span data-stu-id="c2091-102">Types of Isolation</span></span>
<span data-ttu-id="c2091-103">分離ストレージへのアクセスは、常にそのストレージを作成したユーザーに限定されます。</span><span class="sxs-lookup"><span data-stu-id="c2091-103">Access to isolated storage is always restricted to the user who created it.</span></span> <span data-ttu-id="c2091-104">この種の分離を実装するために、共通言語ランタイムは、オペレーティング システムが認識するユーザー ID (ストアを開くときにコードが実行しているプロセスに関連付けられた ID) と同じ概念を使用します。</span><span class="sxs-lookup"><span data-stu-id="c2091-104">To implement this type of isolation, the common language runtime uses the same notion of user identity that the operating system recognizes, which is the identity associated with the process in which the code is running when the store is opened.</span></span> <span data-ttu-id="c2091-105">この ID は認証されたユーザーの ID ですが、偽装によって現在のユーザーの ID が動的に変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2091-105">This identity is an authenticated user identity, but impersonation can cause the identity of the current user to change dynamically.</span></span>  
  
 <span data-ttu-id="c2091-106">また、分離ストレージへのアクセスは、アプリケーションのドメインおよびアセンブリ、またはアセンブリのみに関連付けられた ID に従って制限されます。</span><span class="sxs-lookup"><span data-stu-id="c2091-106">Access to isolated storage is also restricted according to the identity associated with the application's domain and assembly, or with the assembly alone.</span></span> <span data-ttu-id="c2091-107">ランタイムは、以下の方法でこのような ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="c2091-107">The runtime obtains these identities in the following ways:</span></span>  
  
-   <span data-ttu-id="c2091-108">ドメイン ID は、アプリケーションの証拠を表します。Web アプリケーションの場合は、完全な URL の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2091-108">Domain identity represents the evidence of the application, which in the case of a web application might be the full URL.</span></span> <span data-ttu-id="c2091-109">シェルでホストされるコードの場合、ドメイン ID はアプリケーション ディレクトリのパスに基づいている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2091-109">For shell-hosted code, the domain identity might be based on the application directory path.</span></span> <span data-ttu-id="c2091-110">たとえば、実行可能ファイルが C:\Office\MyApp.exe というパスから実行される場合、ドメイン ID は C:\Office\MyApp.exe になります。</span><span class="sxs-lookup"><span data-stu-id="c2091-110">For example, if the executable runs from the path C:\Office\MyApp.exe, the domain identity would be C:\Office\MyApp.exe.</span></span>  
  
-   <span data-ttu-id="c2091-111">アセンブリ ID はアセンブリの証拠です。</span><span class="sxs-lookup"><span data-stu-id="c2091-111">Assembly identity is the evidence of the assembly.</span></span> <span data-ttu-id="c2091-112">アセンブリ ID は暗号化デジタル署名に由来することがあります。この場合、アセンブリの[厳密な名前](../../../docs/framework/app-domains/strong-named-assemblies.md)、アセンブリのソフトウェア発行元、または URL の ID である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2091-112">This might come from a cryptographic digital signature, which can be the assembly's [strong name](../../../docs/framework/app-domains/strong-named-assemblies.md), the software publisher of the assembly, or its URL identity.</span></span> <span data-ttu-id="c2091-113">アセンブリに厳密な名前とソフトウェア発行元 ID が両方ともある場合は、ソフトウェア発行元 ID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2091-113">If an assembly has both a strong name and a software publisher identity, then the software publisher identity is used.</span></span> <span data-ttu-id="c2091-114">アセンブリがインターネットから取得され、署名されていない場合は、URL ID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2091-114">If the assembly comes from the Internet and is unsigned, the URL identity is used.</span></span> <span data-ttu-id="c2091-115">アセンブリおよび厳密な名前の詳細については、「[アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2091-115">For more information about assemblies and strong names, see [Programming with Assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md).</span></span>  
  
-   <span data-ttu-id="c2091-116">ローミング ストアは、ローミング ユーザー プロファイルを持つユーザーと共に移動します。</span><span class="sxs-lookup"><span data-stu-id="c2091-116">Roaming stores move with a user that has a roaming user profile.</span></span> <span data-ttu-id="c2091-117">ファイルはネットワーク ディレクトリに書き込まれ、ユーザーがログインする任意のコンピューターにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="c2091-117">Files are written to a network directory and are downloaded to any computer the user logs into.</span></span> <span data-ttu-id="c2091-118">ローミング ユーザー プロファイルの詳細については、「<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2091-118">For more information about roaming user profiles, see <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c2091-119">分離ストレージは、ユーザー、ドメイン、アセンブリの ID の概念を組み合わせることで、次のようにそれぞれ独自の使用シナリオを持つ方法でデータを分離できます。</span><span class="sxs-lookup"><span data-stu-id="c2091-119">By combining the concepts of user, domain, and assembly identity, isolated storage can isolate data in the following ways, each of which has its own usage scenarios:</span></span>  
  
-   [<span data-ttu-id="c2091-120">ユーザーとアセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="c2091-120">Isolation by user and assembly</span></span>](#UserAssembly)  
  
-   [<span data-ttu-id="c2091-121">ユーザー、ドメイン、アセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="c2091-121">Isolation by user, domain, and assembly</span></span>](#UserDomainAssembly)  
  
 <span data-ttu-id="c2091-122">これらの分離のいずれかをローミング ユーザー プロファイルと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="c2091-122">Either of these isolations can be combined with a roaming user profile.</span></span> <span data-ttu-id="c2091-123">詳細については、「[分離ストレージとローミング](#Roaming)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2091-123">For more information, see the section [Isolated Storage and Roaming](#Roaming).</span></span>  
  
 <span data-ttu-id="c2091-124">次の図は、異なるスコープにストアがどのように分離されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="c2091-124">The following illustration demonstrates how stores are isolated in different scopes.</span></span>  
  
 <span data-ttu-id="c2091-125">![ユーザーおよびアセンブリ別の分離](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")</span><span class="sxs-lookup"><span data-stu-id="c2091-125">![Isolation by user and assembly](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")</span></span>  
<span data-ttu-id="c2091-126">分離ストレージの種類</span><span class="sxs-lookup"><span data-stu-id="c2091-126">Types of isolated storage</span></span>  
  
 <span data-ttu-id="c2091-127">分離ストレージは、ローミング ストアを除き、特定のコンピューターのローカルであるストレージ機能を使用するため、常にコンピューターによって暗黙的に隔離されています。</span><span class="sxs-lookup"><span data-stu-id="c2091-127">Note that except for roaming stores, isolated storage is always implicitly isolated by computer because it uses the storage facilities that are local to a given computer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2091-128">分離ストレージは [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="c2091-128">Isolated storage is not available for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="c2091-129">代わりに、 `Windows.Storage` API に含まれる [!INCLUDE[wrt](../../../includes/wrt-md.md)] 名前空間内のアプリケーション データ クラスを使用して、ローカル データとローカル ファイルを格納します。</span><span class="sxs-lookup"><span data-stu-id="c2091-129">Instead, use the application data classes in the `Windows.Storage` namespaces included in the [!INCLUDE[wrt](../../../includes/wrt-md.md)] API to store local data and files.</span></span> <span data-ttu-id="c2091-130">詳細については、Windows デベロッパー センターの[アプリケーション データ](/previous-versions/windows/apps/hh464917(v=win.10))に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2091-130">For more information, see [Application data](/previous-versions/windows/apps/hh464917(v=win.10)) in the Windows Dev Center.</span></span>  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a><span data-ttu-id="c2091-131">ユーザーおよびアセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="c2091-131">Isolation by User and Assembly</span></span>  
 <span data-ttu-id="c2091-132">データ ストアを使用するアセンブリにアプリケーションのドメインからアクセスできる必要がある場合は、ユーザーとアセンブリによる分離が適しています。</span><span class="sxs-lookup"><span data-stu-id="c2091-132">When the assembly that uses the data store needs to be accessible from any application's domain, isolation by user and assembly is appropriate.</span></span> <span data-ttu-id="c2091-133">通常、このような状況では、複数のアプリケーションに適用され、ユーザーの名前やライセンス情報など、特定のアプリケーションには関連付けられないデータを格納するために分離ストレージが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2091-133">Typically, in this situation, isolated storage is used to store data that applies across multiple applications and is not tied to any particular application, such as the user's name or license information.</span></span> <span data-ttu-id="c2091-134">ユーザーとアセンブリによって分離されたストレージにアクセスするには、アプリケーション間で情報を転送するためにコードを信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2091-134">To access storage isolated by user and assembly, code must be trusted to transfer information between applications.</span></span> <span data-ttu-id="c2091-135">通常、ユーザーとアセンブリによる分離はイントラネット上では使用できますが、インターネット上では使用できません。</span><span class="sxs-lookup"><span data-stu-id="c2091-135">Typically, isolation by user and assembly is allowed on intranets but not on the Internet.</span></span> <span data-ttu-id="c2091-136">静的な <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> メソッドを呼び出してユーザーとアセンブリ <xref:System.IO.IsolatedStorage.IsolatedStorageScope> を渡すと、このような分離のストレージが返されます。</span><span class="sxs-lookup"><span data-stu-id="c2091-136">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> method and passing in a user and an assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="c2091-137">次のコード例では、ユーザーとアセンブリによって分離されたストアを取得します。</span><span class="sxs-lookup"><span data-stu-id="c2091-137">The following code example retrieves a store that is isolated by user and assembly.</span></span> <span data-ttu-id="c2091-138">このストアには `isoFile` オブジェクトを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c2091-138">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 <span data-ttu-id="c2091-139">証拠パラメーターを使用する例については、「<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2091-139">For an example that uses the evidence parameters, see <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.</span></span>  
  
 <span data-ttu-id="c2091-140"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> メソッドは、次のコード例に示されているようにショートカットとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2091-140">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="c2091-141">このショートカットを使用してローミング可能なストアを開くことはできません。その場合は <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="c2091-141">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a><span data-ttu-id="c2091-142">ユーザー、ドメイン、およびアセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="c2091-142">Isolation by User, Domain, and Assembly</span></span>  
 <span data-ttu-id="c2091-143">アプリケーションでプライベート データ ストアが必要なサードパーティ アセンブリを使用している場合、プライベート データを格納するために分離ストレージを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2091-143">If your application uses a third-party assembly that requires a private data store, you can use isolated storage to store the private data.</span></span> <span data-ttu-id="c2091-144">ユーザー、ドメイン、アセンブリによる分離では、アセンブリがストアを作成したときに実行されていたアプリケーションによってアセンブリが使用されている場合、かつストアが作成されたときのユーザーがアプリケーションを実行した場合にのみ、特定のアセンブリ内のコードのみがデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c2091-144">Isolation by user, domain, and assembly ensures that only code in a given assembly can access the data, and only when the assembly is used by the application that was running when the assembly created the store, and only when the user for whom the store was created runs the application.</span></span> <span data-ttu-id="c2091-145">ユーザー、ドメイン、アセンブリによる分離では、サードパーティのアセンブリから他のアプリケーションにデータが漏えいされません。</span><span class="sxs-lookup"><span data-stu-id="c2091-145">Isolation by user, domain, and assembly keeps the third-party assembly from leaking data to other applications.</span></span> <span data-ttu-id="c2091-146">分離ストレージを使用したくても、使用する隔離の種類がわからない場合は、この分離方法を既定の選択肢にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2091-146">This isolation type should be your default choice if you know that you want to use isolated storage but are not sure which type of isolation to use.</span></span> <span data-ttu-id="c2091-147"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> の静的な <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドを呼び出し、ユーザー、ドメイン、およびアセンブリ <xref:System.IO.IsolatedStorage.IsolatedStorageScope> を渡すと、この種類の分離でストレージが返されます。</span><span class="sxs-lookup"><span data-stu-id="c2091-147">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> and passing in a user, domain, and assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="c2091-148">次のコード例は、ユーザー、ドメイン、アセンブリによって分離されたストアを取得します。</span><span class="sxs-lookup"><span data-stu-id="c2091-148">The following code example retrieves a store isolated by user, domain, and assembly.</span></span> <span data-ttu-id="c2091-149">このストアには `isoFile` オブジェクトを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c2091-149">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 <span data-ttu-id="c2091-150">次のコード例に示すように、別のメソッドをショートカットとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2091-150">Another method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="c2091-151">このショートカットを使用してローミング可能なストアを開くことはできません。その場合は <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="c2091-151">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a><span data-ttu-id="c2091-152">分離ストレージとローミング</span><span class="sxs-lookup"><span data-stu-id="c2091-152">Isolated Storage and Roaming</span></span>  
 <span data-ttu-id="c2091-153">ローミング ユーザー プロファイルは、ユーザーがネットワーク上で ID を設定し、その ID を使用してネットワーク コンピューターにログインし、すべてのパーソナライズされた設定を実行できる Windows 機能です。</span><span class="sxs-lookup"><span data-stu-id="c2091-153">Roaming user profiles are a Windows feature that enables a user to set up an identity on a network and use that identity to log into any network computer, carrying over all personalized settings.</span></span> <span data-ttu-id="c2091-154">分離ストレージを使用するアセンブリでは、ユーザーの分離ストレージをローミング ユーザー プロファイルと一緒に移動する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c2091-154">An assembly that uses isolated storage can specify that the user's isolated storage should move with the roaming user profile.</span></span> <span data-ttu-id="c2091-155">ローミングは、ユーザーとアセンブリによる分離、またはユーザー、ドメイン、アセンブリによる分離と組み合わせて使用​​できます。</span><span class="sxs-lookup"><span data-stu-id="c2091-155">Roaming can be used in conjunction with isolation by user and assembly or with isolation by user, domain, and assembly.</span></span> <span data-ttu-id="c2091-156">ローミング スコープが使用されない場合、ローミング ユーザー プロファイルが使用されていても、ストアはローミングされません。</span><span class="sxs-lookup"><span data-stu-id="c2091-156">If a roaming scope is not used, stores will not roam even if a roaming user profile is used.</span></span>  
  
 <span data-ttu-id="c2091-157">次のコード例では、ユーザーとアセンブリによって分離されたローミング ストアを取得します。</span><span class="sxs-lookup"><span data-stu-id="c2091-157">The following code example retrieves a roaming store isolated by user and assembly.</span></span> <span data-ttu-id="c2091-158">このストアには `isoFile` オブジェクトを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c2091-158">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 <span data-ttu-id="c2091-159">ドメイン スコープを追加すると、ユーザー、ドメイン、およびアプリケーションによって分離されたローミング ストアを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c2091-159">A domain scope can be added to create a roaming store isolated by user, domain, and application.</span></span> <span data-ttu-id="c2091-160">次のコード例はこの処理方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c2091-160">The following code example demonstrates this.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="c2091-161">参照</span><span class="sxs-lookup"><span data-stu-id="c2091-161">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="c2091-162">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="c2091-162">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
