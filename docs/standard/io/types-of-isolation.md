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
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6b07c090a381925f5330a820214126a121d3790b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-isolation"></a><span data-ttu-id="f74fd-102">分離のタイプ</span><span class="sxs-lookup"><span data-stu-id="f74fd-102">Types of Isolation</span></span>
<span data-ttu-id="f74fd-103">分離ストレージへのアクセスは、常に作成したユーザーを制限します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-103">Access to isolated storage is always restricted to the user who created it.</span></span> <span data-ttu-id="f74fd-104">この種の分離を実装するのには、共通言語ランタイムは、これは、コードが実行されているストアが開かれたときに、プロセスに関連付けられた id を同じオペレーティング システムが認識されると、ユーザー id の概念に使用します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-104">To implement this type of isolation, the common language runtime uses the same notion of user identity that the operating system recognizes, which is the identity associated with the process in which the code is running when the store is opened.</span></span> <span data-ttu-id="f74fd-105">この id は、認証されたユーザー id が、権限借用を動的に変更する現在のユーザーの id が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-105">This identity is an authenticated user identity, but impersonation can cause the identity of the current user to change dynamically.</span></span>  
  
 <span data-ttu-id="f74fd-106">分離ストレージへのアクセスは、アプリケーションのドメインとアセンブリ、またはアセンブリだけに関連付けられた id に従って制限もあります。</span><span class="sxs-lookup"><span data-stu-id="f74fd-106">Access to isolated storage is also restricted according to the identity associated with the application's domain and assembly, or with the assembly alone.</span></span> <span data-ttu-id="f74fd-107">ランタイムは、次の方法でこれらの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-107">The runtime obtains these identities in the following ways:</span></span>  
  
-   <span data-ttu-id="f74fd-108">ドメイン id では、可能性のある web アプリケーションの場合、完全な URL と、アプリケーションの証拠を表します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-108">Domain identity represents the evidence of the application, which in the case of a web application might be the full URL.</span></span> <span data-ttu-id="f74fd-109">シェルでホストされているコードでは、ドメイン id がに基づいて、アプリケーションのディレクトリ パス。</span><span class="sxs-lookup"><span data-stu-id="f74fd-109">For shell-hosted code, the domain identity might be based on the application directory path.</span></span> <span data-ttu-id="f74fd-110">C:\Office\MyApp.exe パスから、実行可能ファイルが実行される場合など、ドメイン id では、C:\Office\MyApp.exe になります。</span><span class="sxs-lookup"><span data-stu-id="f74fd-110">For example, if the executable runs from the path C:\Office\MyApp.exe, the domain identity would be C:\Office\MyApp.exe.</span></span>  
  
-   <span data-ttu-id="f74fd-111">アセンブリ id は、アセンブリの証拠です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-111">Assembly identity is the evidence of the assembly.</span></span> <span data-ttu-id="f74fd-112">アセンブリの可能性がある暗号化デジタル署名から取得できます[厳密な名前](../../../docs/framework/app-domains/strong-named-assemblies.md)のソフトウェア発行元、アセンブリ、またはその URL の id。</span><span class="sxs-lookup"><span data-stu-id="f74fd-112">This might come from a cryptographic digital signature, which can be the assembly's [strong name](../../../docs/framework/app-domains/strong-named-assemblies.md), the software publisher of the assembly, or its URL identity.</span></span> <span data-ttu-id="f74fd-113">厳密な名前とソフトウェアの発行元の id の両方のアセンブリがある、ソフトウェアの発行元 id が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-113">If an assembly has both a strong name and a software publisher identity, then the software publisher identity is used.</span></span> <span data-ttu-id="f74fd-114">アセンブリが、インターネットを起源が署名されていない場合は、URL の id が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-114">If the assembly comes from the Internet and is unsigned, the URL identity is used.</span></span> <span data-ttu-id="f74fd-115">アセンブリと厳密な名前の詳細については、次を参照してください。[アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-115">For more information about assemblies and strong names, see [Programming with Assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md).</span></span>  
  
-   <span data-ttu-id="f74fd-116">ローミング ストアは、ローミング ユーザー プロファイルを持つユーザーと共に移動します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-116">Roaming stores move with a user that has a roaming user profile.</span></span> <span data-ttu-id="f74fd-117">ファイルは、ネットワーク ディレクトリに書き込まれ、ユーザーがログインする任意のコンピューターにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-117">Files are written to a network directory and are downloaded to any computer the user logs into.</span></span> <span data-ttu-id="f74fd-118">移動ユーザー プロファイルの詳細については、次を参照してください。<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-118">For more information about roaming user profiles, see <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f74fd-119">ユーザー、ドメイン、およびアセンブリ id の概念を組み合わせることにより、分離ストレージは、それぞれが独自の用途を持つ次の方法でデータを特定できます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-119">By combining the concepts of user, domain, and assembly identity, isolated storage can isolate data in the following ways, each of which has its own usage scenarios:</span></span>  
  
-   [<span data-ttu-id="f74fd-120">ユーザーおよびアセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="f74fd-120">Isolation by user and assembly</span></span>](#UserAssembly)  
  
-   [<span data-ttu-id="f74fd-121">ユーザー、ドメイン、およびアセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="f74fd-121">Isolation by user, domain, and assembly</span></span>](#UserDomainAssembly)  
  
 <span data-ttu-id="f74fd-122">これらの分離のいずれかは、移動ユーザー プロファイルと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-122">Either of these isolations can be combined with a roaming user profile.</span></span> <span data-ttu-id="f74fd-123">詳細については、セクションを参照して[分離ストレージとローミング](#Roaming)です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-123">For more information, see the section [Isolated Storage and Roaming](#Roaming).</span></span>  
  
 <span data-ttu-id="f74fd-124">次の図は、さまざまなスコープでのストアの分離方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-124">The following illustration demonstrates how stores are isolated in different scopes.</span></span>  
  
 <span data-ttu-id="f74fd-125">![ユーザーおよびアセンブリによる分離](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")</span><span class="sxs-lookup"><span data-stu-id="f74fd-125">![Isolation by user and assembly](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")</span></span>  
<span data-ttu-id="f74fd-126">分離ストレージの種類</span><span class="sxs-lookup"><span data-stu-id="f74fd-126">Types of isolated storage</span></span>  
  
 <span data-ttu-id="f74fd-127">を除き、ストアを移動するには、分離ストレージは常に暗黙的にコンピューター別に分離は、特定のコンピューターに対してローカルな記憶域機能を使用しているために注意してください。</span><span class="sxs-lookup"><span data-stu-id="f74fd-127">Note that except for roaming stores, isolated storage is always implicitly isolated by computer because it uses the storage facilities that are local to a given computer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f74fd-128">分離ストレージは [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="f74fd-128">Isolated storage is not available for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="f74fd-129">代わりに、 `Windows.Storage` API に含まれる [!INCLUDE[wrt](../../../includes/wrt-md.md)] 名前空間内のアプリケーション データ クラスを使用して、ローカル データとローカル ファイルを格納します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-129">Instead, use the application data classes in the `Windows.Storage` namespaces included in the [!INCLUDE[wrt](../../../includes/wrt-md.md)] API to store local data and files.</span></span> <span data-ttu-id="f74fd-130">詳細については、Windows デベロッパー センターの [アプリケーション データ](http://go.microsoft.com/fwlink/?LinkId=229175) に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f74fd-130">For more information, see [Application data](http://go.microsoft.com/fwlink/?LinkId=229175) in the Windows Dev Center.</span></span>  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a><span data-ttu-id="f74fd-131">ユーザーおよびアセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="f74fd-131">Isolation by User and Assembly</span></span>  
 <span data-ttu-id="f74fd-132">データを使用するアセンブリを格納する任意のアプリケーションのドメインからアクセスできる必要があります、ときにユーザーおよびアセンブリによる分離が適しています。</span><span class="sxs-lookup"><span data-stu-id="f74fd-132">When the assembly that uses the data store needs to be accessible from any application's domain, isolation by user and assembly is appropriate.</span></span> <span data-ttu-id="f74fd-133">通常、このような状況では、複数のアプリケーション全体に適用され、ユーザーの名前やライセンス情報など、特定のアプリケーションに関連付けられていないデータを格納する分離ストレージが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-133">Typically, in this situation, isolated storage is used to store data that applies across multiple applications and is not tied to any particular application, such as the user's name or license information.</span></span> <span data-ttu-id="f74fd-134">ユーザーおよびアセンブリ別に分離された記憶域にアクセスするにコードをアプリケーション間で情報を転送するために信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f74fd-134">To access storage isolated by user and assembly, code must be trusted to transfer information between applications.</span></span> <span data-ttu-id="f74fd-135">通常、ユーザーおよびアセンブリによる分離では、イントラネットではなく、インターネットが許可されます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-135">Typically, isolation by user and assembly is allowed on intranets but not on the Internet.</span></span> <span data-ttu-id="f74fd-136">静的なを呼び出して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType>メソッドおよびユーザーとアセンブリに渡すこと<xref:System.IO.IsolatedStorage.IsolatedStorageScope>このような分離ストレージを返します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-136">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> method and passing in a user and an assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="f74fd-137">次のコード例では、ユーザーおよびアセンブリ別に分離されたストアを取得します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-137">The following code example retrieves a store that is isolated by user and assembly.</span></span> <span data-ttu-id="f74fd-138">ストアを介してアクセスできる、`isoFile`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f74fd-138">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 <span data-ttu-id="f74fd-139">証拠パラメーターを使用する例は、次を参照してください。<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-139">For an example that uses the evidence parameters, see <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.</span></span>  
  
 <span data-ttu-id="f74fd-140"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>メソッドは、次のコード例に示すように、簡単な方法として使用します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-140">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="f74fd-141">ローミングに対応するストアを開くには、このショートカットを使用できません。使用して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>このような場合です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-141">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a><span data-ttu-id="f74fd-142">ユーザー、ドメイン、およびアセンブリによる分離</span><span class="sxs-lookup"><span data-stu-id="f74fd-142">Isolation by User, Domain, and Assembly</span></span>  
 <span data-ttu-id="f74fd-143">アプリケーションでは、プライベート データ ストアを必要とするサード パーティ製のアセンブリを使用する場合は、プライベート データを格納する分離ストレージを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-143">If your application uses a third-party assembly that requires a private data store, you can use isolated storage to store the private data.</span></span> <span data-ttu-id="f74fd-144">ユーザー、ドメイン、およびアセンブリによる分離確実にだけで、特定のアセンブリ内のコードは、データにアクセスできるアセンブリが、アセンブリには、ストアが作成されるときに実行されていたアプリケーションで使用される場合にのみと、ストアの作成対象のユーザーが実行時にのみ、 アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="f74fd-144">Isolation by user, domain, and assembly ensures that only code in a given assembly can access the data, and only when the assembly is used by the application that was running when the assembly created the store, and only when the user for whom the store was created runs the application.</span></span> <span data-ttu-id="f74fd-145">ユーザー、ドメイン、およびアセンブリによる分離では、他のアプリケーションへのデータの漏洩からサードパーティ製のアセンブリが保持されます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-145">Isolation by user, domain, and assembly keeps the third-party assembly from leaking data to other applications.</span></span> <span data-ttu-id="f74fd-146">この分離型は、分離ストレージを使用するが、不明などの種類の分離を使用することがわかっている場合、既定の選択肢をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f74fd-146">This isolation type should be your default choice if you know that you want to use isolated storage but are not sure which type of isolation to use.</span></span> <span data-ttu-id="f74fd-147">呼び出す、静的な<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドの<xref:System.IO.IsolatedStorage.IsolatedStorageFile>を渡すユーザー、ドメイン、およびアセンブリと<xref:System.IO.IsolatedStorage.IsolatedStorageScope>このような分離ストレージを返します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-147">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> and passing in a user, domain, and assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="f74fd-148">次のコード例では、ユーザー、ドメイン、およびアセンブリ別に分離されたストアを取得します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-148">The following code example retrieves a store isolated by user, domain, and assembly.</span></span> <span data-ttu-id="f74fd-149">ストアを介してアクセスできる、`isoFile`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f74fd-149">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 <span data-ttu-id="f74fd-150">別の方法を次のコード例に示すように簡単な方法として使用します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-150">Another method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="f74fd-151">ローミングに対応するストアを開くには、このショートカットを使用できません。使用して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>このような場合です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-151">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a><span data-ttu-id="f74fd-152">分離ストレージとローミング</span><span class="sxs-lookup"><span data-stu-id="f74fd-152">Isolated Storage and Roaming</span></span>  
 <span data-ttu-id="f74fd-153">移動ユーザー プロファイルは、ユーザーがネットワーク上の id を設定し、その id を使用して、個人用に設定されたすべての設定に実行するすべてのネットワーク コンピューターにログインできるようにする Windows の機能です。</span><span class="sxs-lookup"><span data-stu-id="f74fd-153">Roaming user profiles are a Windows feature that enables a user to set up an identity on a network and use that identity to log into any network computer, carrying over all personalized settings.</span></span> <span data-ttu-id="f74fd-154">分離ストレージを使用したアセンブリでは、ユーザーの分離ストレージは、ローミング ユーザー プロファイルと移動する必要がありますを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-154">An assembly that uses isolated storage can specify that the user's isolated storage should move with the roaming user profile.</span></span> <span data-ttu-id="f74fd-155">ユーザー、ドメイン、およびアセンブリ別、と共に、ユーザーおよびアセンブリによる分離または分離を使用したしてローミングを使用することがことができます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-155">Roaming can be used in conjunction with isolation by user and assembly or with isolation by user, domain, and assembly.</span></span> <span data-ttu-id="f74fd-156">ローミングのスコープを使用しない場合、ローミング ユーザー プロファイルを使用する場合でもストアは移動しません。</span><span class="sxs-lookup"><span data-stu-id="f74fd-156">If a roaming scope is not used, stores will not roam even if a roaming user profile is used.</span></span>  
  
 <span data-ttu-id="f74fd-157">次のコード例では、ユーザーおよびアセンブリ別に分離されたローミング ストアを取得します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-157">The following code example retrieves a roaming store isolated by user and assembly.</span></span> <span data-ttu-id="f74fd-158">ストアを介してアクセスできる、`isoFile`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f74fd-158">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 <span data-ttu-id="f74fd-159">ユーザー、ドメイン、およびアプリケーション別に分離されたローミング ストアを作成するのには、ドメイン スコープを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f74fd-159">A domain scope can be added to create a roaming store isolated by user, domain, and application.</span></span> <span data-ttu-id="f74fd-160">次のコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="f74fd-160">The following code example demonstrates this.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="f74fd-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="f74fd-161">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="f74fd-162">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="f74fd-162">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
