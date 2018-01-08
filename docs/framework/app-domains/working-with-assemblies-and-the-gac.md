---
title: "アセンブリとグローバル アセンブリ キャッシュの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f1ee4855745573a4b73b409279d70906191bfd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="ebf67-102">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="ebf67-102">Working with Assemblies and the Global Assembly Cache</span></span>
<span data-ttu-id="ebf67-103">あるアセンブリを複数のアプリケーションで共有する場合は、そのアセンブリをグローバル アセンブリ キャッシュ内にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ebf67-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="ebf67-104">共通言語ランタイムをインストールしている各コンピューターは、このコードをコンピューター全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ebf67-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="ebf67-105">グローバル アセンブリ キャッシュは、そのコンピューター上の複数のアプリケーションで共有するように指定されたアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="ebf67-106">グローバル アセンブリ キャッシュ内にインストールされるアセンブリは、厳密な名前を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebf67-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebf67-107">グローバル アセンブリ キャッシュ内に配置されるアセンブリは、アセンブリ名とファイル名の拡張子を除く部分が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebf67-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="ebf67-108">たとえば、アセンブリ名が myAssembly のアセンブリの場合、ファイル名は myAssembly.exe または myAssembly.dll である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebf67-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
 <span data-ttu-id="ebf67-109">アセンブリの共有が必要な場合にだけ、アセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="ebf67-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="ebf67-110">一般的には、明らかにアセンブリを共有する必要がある場合を除いて、アセンブリの依存関係はプライベートにし、アセンブリはアプリケーション ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="ebf67-111">また、COM 相互運用 (機能) またはアンマネージ コードからアセンブリにアクセスできるようにするために、アセンブリをグローバル アセンブリ キャッシュにインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ebf67-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
 <span data-ttu-id="ebf67-112">アセンブリをグローバル アセンブリ キャッシュにインストールする理由は、いくつか考えられます。</span><span class="sxs-lookup"><span data-stu-id="ebf67-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="ebf67-113">共有の場所。</span><span class="sxs-lookup"><span data-stu-id="ebf67-113">Shared location.</span></span>  
  
     <span data-ttu-id="ebf67-114">複数のアプリケーションで使用するアセンブリは、グローバル アセンブリ キャッシュに配置できます。</span><span class="sxs-lookup"><span data-stu-id="ebf67-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="ebf67-115">たとえば、すべてのアプリケーションがグローバル アセンブリ キャッシュ内の 1 つのアセンブリを使用する場合は、アセンブリへの参照をリダイレクトするバージョン ポリシー ステートメントを Machine.config ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="ebf67-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
-   <span data-ttu-id="ebf67-116">ファイル セキュリティ。</span><span class="sxs-lookup"><span data-stu-id="ebf67-116">File security.</span></span>  
  
     <span data-ttu-id="ebf67-117">通常、管理者は、書き込みおよび実行アクセスを制御するアクセス制御リスト (ACL: Access Control List) を使用して systemroot ディレクトリを保護します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="ebf67-118">グローバル アセンブリ キャッシュは、systemroot ディレクトリにインストールされるため、このディレクトリの ACL を継承します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="ebf67-119">グローバル アセンブリ キャッシュからファイルを削除する場合は、管理者権限を持つユーザーに対してだけ許可することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ebf67-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
-   <span data-ttu-id="ebf67-120">side-by-side でのバージョン管理。</span><span class="sxs-lookup"><span data-stu-id="ebf67-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="ebf67-121">名前は同じでもバージョン情報が異なるアセンブリの複数のコピーを、グローバル アセンブリ キャッシュ内で管理できます。</span><span class="sxs-lookup"><span data-stu-id="ebf67-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="ebf67-122">追加の検索場所。</span><span class="sxs-lookup"><span data-stu-id="ebf67-122">Additional search location.</span></span>  
  
     <span data-ttu-id="ebf67-123">共通言語ランタイムは、構成ファイル内のコードベース情報をプローブまたは使用する前に、グローバル アセンブリ キャッシュ内にアセンブリ要求と一致するアセンブリがあるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="ebf67-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="ebf67-124">アセンブリのグローバル アセンブリ キャッシュへのインストールを明示的に避けたい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ebf67-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="ebf67-125">アプリケーションを構成するアセンブリの 1 つをグローバル アセンブリ キャッシュに配置した場合は、アプリケーション ディレクトリをコピーする XCOPY を使用してアプリケーションをレプリケートしたりインストールしたりすることはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="ebf67-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="ebf67-126">この場合は、グローバル アセンブリ キャッシュ内のアセンブリも移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebf67-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebf67-127">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ebf67-127">In This Section</span></span>  
 [<span data-ttu-id="ebf67-128">方法: グローバル アセンブリ キャッシュにアセンブリをインストールする</span><span class="sxs-lookup"><span data-stu-id="ebf67-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 <span data-ttu-id="ebf67-129">アセンブリをグローバル アセンブリ キャッシュにインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ebf67-130">方法: グローバル アセンブリ キャッシュの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="ebf67-130">How to: View the Contents of the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 <span data-ttu-id="ebf67-131">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュの内容を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ebf67-132">方法: グローバル アセンブリ キャッシュからアセンブリを削除する</span><span class="sxs-lookup"><span data-stu-id="ebf67-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 <span data-ttu-id="ebf67-133">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュからアセンブリを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ebf67-134">サービス コンポーネントとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="ebf67-134">Using Serviced Components with the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 <span data-ttu-id="ebf67-135">サービス コンポーネント (マネージ COM+ コンポーネント) をグローバル アセンブリ キャッシュに配置する必要がある理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ebf67-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebf67-136">Related Sections</span></span>  
 [<span data-ttu-id="ebf67-137">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="ebf67-137">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="ebf67-138">アセンブリの作成の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-138">Provides an overview of creating assemblies.</span></span>  
  
 [<span data-ttu-id="ebf67-139">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="ebf67-139">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 <span data-ttu-id="ebf67-140">グローバル アセンブリ キャッシュについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-140">Describes the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ebf67-141">方法: アセンブリの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="ebf67-141">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="ebf67-142">[Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリ内の MSIL (Microsoft Intermediate Language) 情報を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
 [<span data-ttu-id="ebf67-143">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="ebf67-143">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="ebf67-144">共通言語ランタイムが、アプリケーションを構成するアセンブリを検出して読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="ebf67-145">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="ebf67-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="ebf67-146">マネージ アプリケーションを構成するブロックであるアセンブリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ebf67-146">Describes assemblies, the building blocks of managed applications.</span></span>
