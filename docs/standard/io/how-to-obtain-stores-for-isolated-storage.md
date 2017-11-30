---
title: "方法 : 分離ストレージでストアを取得する"
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
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb0b877aa0f4cee36bd1f8c1cea624cf9368fbaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="426dd-102">方法 : 分離ストレージでストアを取得する</span><span class="sxs-lookup"><span data-stu-id="426dd-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="426dd-103">分離ストアは、データ コンパートメント内の仮想ファイル システムを公開します。</span><span class="sxs-lookup"><span data-stu-id="426dd-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="426dd-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>クラスがいくつかの分離ストアと対話するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="426dd-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="426dd-105">作成し、ストアを取得する<xref:System.IO.IsolatedStorage.IsolatedStorageFile>3 つの静的メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="426dd-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
-   <span data-ttu-id="426dd-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>ユーザーおよびアセンブリによる分離ストレージを返します。</span><span class="sxs-lookup"><span data-stu-id="426dd-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
-   <span data-ttu-id="426dd-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>ドメインとアセンブリが分離される記憶域を返します。</span><span class="sxs-lookup"><span data-stu-id="426dd-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="426dd-108">両方のメソッドが呼び出されるコードに属しているストアを取得します。</span><span class="sxs-lookup"><span data-stu-id="426dd-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
-   <span data-ttu-id="426dd-109">静的メソッド<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>スコープ パラメーターの組み合わせに渡すことで指定されている分離ストアを返します。</span><span class="sxs-lookup"><span data-stu-id="426dd-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="426dd-110">次のコードでは、ユーザー、アセンブリ、およびドメイン別に分離されたストアを返します。</span><span class="sxs-lookup"><span data-stu-id="426dd-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="426dd-111">使用することができます、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>ローミング ユーザー プロファイルを使用して、ストアを移動することを指定します。</span><span class="sxs-lookup"><span data-stu-id="426dd-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="426dd-112">これを設定する方法の詳細については、次を参照してください。[分離のタイプ](../../../docs/standard/io/types-of-isolation.md)です。</span><span class="sxs-lookup"><span data-stu-id="426dd-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="426dd-113">別のアセンブリ内から取得される分離ストアは、既定では、異なるストアです。</span><span class="sxs-lookup"><span data-stu-id="426dd-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="426dd-114">パラメーターのアセンブリまたはドメインの証拠を渡すことで、別のアセンブリまたはドメインのストアにアクセスすることができます、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="426dd-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="426dd-115">これには、アプリケーション ドメインの id を使用して分離ストレージにアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="426dd-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="426dd-116">詳細については、次を参照してください。、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドのオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="426dd-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="426dd-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、および<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>を返し、<xref:System.IO.IsolatedStorage.IsolatedStorageFile>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="426dd-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="426dd-118">状況に最適などの分離タイプを決定するために、次を参照してください。[分離のタイプ](../../../docs/standard/io/types-of-isolation.md)です。</span><span class="sxs-lookup"><span data-stu-id="426dd-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="426dd-119">分離ストレージ ファイル オブジェクトがある場合を読み取り、書き込み、作成、分離ストレージのメソッドを使用して、ファイルおよびディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="426dd-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="426dd-120">コードに渡すことを防止するためのメカニズムがない、<xref:System.IO.IsolatedStorage.IsolatedStorageFile>されるコードをオブジェクトには、ストア自体を取得するための十分なアクセスにないです。</span><span class="sxs-lookup"><span data-stu-id="426dd-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="426dd-121">参照時にのみドメインとアセンブリの id と分離ストレージのアクセス許可がチェックされて、<xref:System.IO.IsolatedStorage.IsolatedStorage>オブジェクトは、取得したでは通常、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="426dd-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="426dd-122">参照を保護する<xref:System.IO.IsolatedStorage.IsolatedStorageFile>オブジェクトは、そのため、これらの参照を使用するコードの責任です。</span><span class="sxs-lookup"><span data-stu-id="426dd-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="426dd-123">例</span><span class="sxs-lookup"><span data-stu-id="426dd-123">Example</span></span>  
 <span data-ttu-id="426dd-124">次のコードでは、ユーザーおよびアセンブリ別に分離されたストアを取得するクラスの単純な例を提供します。</span><span class="sxs-lookup"><span data-stu-id="426dd-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="426dd-125">追加することでユーザー、ドメイン、およびアセンブリ別に分離されたストアを取得するコードを変更することができます<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType>引数にする、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドのパス。</span><span class="sxs-lookup"><span data-stu-id="426dd-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="426dd-126">コードを実行した後、」と入力して、ストアが作成されたことを確認できます**StoreAdm/LIST**コマンドライン。</span><span class="sxs-lookup"><span data-stu-id="426dd-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="426dd-127">これにより、実行、[分離ストレージ ツール (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)し、ユーザーの現在の分離を格納すべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="426dd-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="426dd-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="426dd-128">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="426dd-129">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="426dd-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="426dd-130">分離のタイプ</span><span class="sxs-lookup"><span data-stu-id="426dd-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)  
 [<span data-ttu-id="426dd-131">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="426dd-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
