---
title: "相互運用アプリケーションの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0682fd149134531781346d21245a0b1fd3fc4d43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-an-interop-application"></a><span data-ttu-id="d784e-102">相互運用アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="d784e-102">Deploying an Interop Application</span></span>
<span data-ttu-id="d784e-103">通常、相互運用アプリケーションには、.NET クライアント アセンブリ、個別の COM タイプ ライブラリを表す 1 つ以上の相互運用機能アセンブリ、および 1 つ以上の登録済み COM コンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d784e-103">An interop application typically includes a .NET client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span> <span data-ttu-id="d784e-104">Visual Studio および [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、タイプ ライブラリを相互運用機能アセンブリにインポートして変換するためのツールが用意されています。詳細については、「[タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d784e-104">Visual Studio and the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provide tools to import and convert a type library to an interop assembly, as discussed in [Importing a Type Library as an Assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span></span> <span data-ttu-id="d784e-105">相互運用アプリケーションを配置する方法には、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="d784e-105">There are two ways to deploy an interop application:</span></span>  
  
-   <span data-ttu-id="d784e-106">埋め込まれた相互運用機能型を使用する: [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。</span><span class="sxs-lookup"><span data-stu-id="d784e-106">By using embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="d784e-107">コンパイラは、アプリケーションで使用する型情報のみを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="d784e-107">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="d784e-108">アプリケーションで相互運用機能アセンブリを配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d784e-108">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="d784e-109">この手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d784e-109">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="d784e-110">相互運用機能アセンブリを配置する: 相互運用機能アセンブリへの標準の参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d784e-110">By deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="d784e-111">この場合、アプリケーションで相互運用機能アセンブリを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d784e-111">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="d784e-112">この手法を採用し、プライベートの COM コンポーネントを使用しない場合は、常に、マネージ コードに組み込む予定の COM コンポーネントの作成者によって発行されたプライマリ相互運用機能アセンブリ (PIA) を参照します。</span><span class="sxs-lookup"><span data-stu-id="d784e-112">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="d784e-113">プライマリ相互運用機能アセンブリの生成と使用の詳細については、「[プライマリ相互運用機能](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d784e-113">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).</span></span>  
  
 <span data-ttu-id="d784e-114">埋め込まれた相互運用機能型を使用すると、配置を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d784e-114">If you use embedded interop types, deployment is simple and straightforward.</span></span> <span data-ttu-id="d784e-115">特別な操作を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d784e-115">There is nothing special you need to do.</span></span> <span data-ttu-id="d784e-116">ここからは、アプリケーションで相互運用機能アセンブリを配置するシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d784e-116">The rest of this article describes the scenarios for deploying interop assemblies with your application.</span></span>  
  
## <a name="deploying-interop-assemblies"></a><span data-ttu-id="d784e-117">相互運用機能アセンブリの配置</span><span class="sxs-lookup"><span data-stu-id="d784e-117">Deploying Interop Assemblies</span></span>  
 <span data-ttu-id="d784e-118">アセンブリには厳密な名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d784e-118">Assemblies can have strong names.</span></span> <span data-ttu-id="d784e-119">厳密な名前のアセンブリには、一意の識別子を提供する、発行者の公開キーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d784e-119">A strong-named assembly includes the publisher's public key, which provides a unique identity.</span></span> <span data-ttu-id="d784e-120">発行者は、**/keyfile** オプションを使用して、[タイプ ライブラリ インポーター (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) で生成されたアセンブリに署名できます。</span><span class="sxs-lookup"><span data-stu-id="d784e-120">Assemblies that are produced by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) can be signed by the publisher by using the **/keyfile** option.</span></span> <span data-ttu-id="d784e-121">署名付きアセンブリは、グローバル アセンブリ キャッシュにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d784e-121">You can install signed assemblies into the global assembly cache.</span></span> <span data-ttu-id="d784e-122">署名のないアセンブリは、プライベート アセンブリとしてユーザーのコンピューターにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d784e-122">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
### <a name="private-assemblies"></a><span data-ttu-id="d784e-123">プライベート アセンブリ</span><span class="sxs-lookup"><span data-stu-id="d784e-123">Private Assemblies</span></span>  
 <span data-ttu-id="d784e-124">プライベートに使用するアセンブリをインストールするには、アプリケーションの実行可能ファイルと、インポートされた COM 型を含む相互運用機能アセンブリの両方を同じディレクトリ構造にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d784e-124">To install an assembly to be used privately, both the application executable and the interop assembly that contains imported COM types must be installed in the same directory structure.</span></span> <span data-ttu-id="d784e-125">別個のアプリケーション ディレクトリに配置された Client1.exe と Client2.exe によってプライベートに使用される、署名のない相互運用機能アセンブリを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="d784e-125">The following illustration shows an unsigned interop assembly to be used privately by Client1.exe and Client2.exe, which reside in separate application directories.</span></span> <span data-ttu-id="d784e-126">この例の LOANLib.dll という相互運用機能アセンブリは、2 回インストールされています。</span><span class="sxs-lookup"><span data-stu-id="d784e-126">The interop assembly, which is called LOANLib.dll in this example, is installed twice.</span></span>  
  
 <span data-ttu-id="d784e-127">![ディレクトリ構造と Windows レジストリ](../../../docs/framework/interop/media/comdeployprivate.gif "comdeployprivate")</span><span class="sxs-lookup"><span data-stu-id="d784e-127">![Directory structure and Windows registry](../../../docs/framework/interop/media/comdeployprivate.gif "comdeployprivate")</span></span>  
<span data-ttu-id="d784e-128">プライベートに配置する場合のディレクトリ構造とレジストリ エントリ</span><span class="sxs-lookup"><span data-stu-id="d784e-128">Directory structure and registry entries for a private deployment</span></span>  
  
 <span data-ttu-id="d784e-129">アプリケーションに関連付けられているすべての COM コンポーネントを、Windows レジストリにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d784e-129">All COM components associated with the application must be installed in the Windows registry.</span></span> <span data-ttu-id="d784e-130">この図の Client1.exe と Client2.exe が別のコンピューターにインストールされている場合は、両方のコンピューターで COM コンポーネントを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d784e-130">If Client1.exe and Client2.exe in the illustration are installed on different computers, you must register the COM components on both computers.</span></span>  
  
### <a name="shared-assemblies"></a><span data-ttu-id="d784e-131">共有アセンブリ</span><span class="sxs-lookup"><span data-stu-id="d784e-131">Shared Assemblies</span></span>  
 <span data-ttu-id="d784e-132">複数のアプリケーションによって共有されるアセンブリは、グローバル アセンブリ キャッシュと呼ばれる集中化されたリポジトリにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d784e-132">Assemblies that are shared by multiple applications should be installed in a centralized repository called the global assembly cache.</span></span> <span data-ttu-id="d784e-133">.NET クライアントは、署名され、グローバル アセンブリ キャッシュにインストールされた、相互運用機能アセンブリの同じコピーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d784e-133">.NET clients can access the same copy of the interop assembly, which is signed and installed in the global assembly cache.</span></span> <span data-ttu-id="d784e-134">プライマリ相互運用機能アセンブリの生成と使用の詳細については、「[プライマリ相互運用機能](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d784e-134">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d784e-135">参照</span><span class="sxs-lookup"><span data-stu-id="d784e-135">See Also</span></span>  
 [<span data-ttu-id="d784e-136">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="d784e-136">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="d784e-137">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="d784e-137">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="d784e-138">マネージ コードの COM 型の使用</span><span class="sxs-lookup"><span data-stu-id="d784e-138">Using COM Types in Managed Code</span></span>](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [<span data-ttu-id="d784e-139">相互運用プロジェクトのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d784e-139">Compiling an Interop Project</span></span>](../../../docs/framework/interop/compiling-an-interop-project.md)
