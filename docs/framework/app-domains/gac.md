---
title: "グローバル アセンブリ キャッシュ"
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
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eedb33042bd904340cc02526c3f1cf927c09bd9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="global-assembly-cache"></a><span data-ttu-id="c7ce7-102">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="c7ce7-102">Global Assembly Cache</span></span>
<span data-ttu-id="c7ce7-103">共通言語ランタイムがインストールされている各コンピューターには、グローバル アセンブリ キャッシュと呼ばれる、コンピューター全体にわたって使用されるコード キャッシュがあります。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-103">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="c7ce7-104">グローバル アセンブリ キャッシュは、そのコンピューター上の複数のアプリケーションで共有するように特別に指定されたアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-104">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="c7ce7-105">アセンブリを共有するには、必要な場合にだけそれらのアセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-105">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="c7ce7-106">一般的には、明らかにアセンブリを共有する必要がある場合を除いて、アセンブリの依存関係はプライベートにし、アセンブリはアプリケーション ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="c7ce7-107">また、COM 相互運用またはアンマネージ コードからアセンブリにアクセスできるようにするために、アセンブリをグローバル アセンブリ キャッシュにインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-107">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7ce7-108">アセンブリのグローバル アセンブリ キャッシュへのインストールを明示的に避けたい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-108">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="c7ce7-109">アプリケーションを構成するアセンブリの 1 つをグローバル アセンブリ キャッシュに配置した場合は、アプリケーション ディレクトリをコピーする **xcopy** コマンドを使用してアプリケーションをレプリケートしたりインストールしたりすることはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-109">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="c7ce7-110">この場合、グローバル アセンブリ キャッシュ内に配置したアセンブリも移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-110">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="c7ce7-111">アセンブリをグローバル アセンブリ キャッシュに配置するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-111">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
-   <span data-ttu-id="c7ce7-112">グローバル アセンブリ キャッシュを扱えるように設計されたインストーラーを使用する。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-112">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="c7ce7-113">これは、アセンブリをグローバル アセンブリ キャッシュにインストールするための推奨オプションです。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-113">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
-   <span data-ttu-id="c7ce7-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]に用意されている[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) という開発者ツールを使用する。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7ce7-115">配置時に、Windows Installer を使用して、アセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-115">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="c7ce7-116">グローバル アセンブリ キャッシュ ツールの使用は、開発時のみに限定してください。グローバル アセンブリ キャッシュ ツールでは、Windows インストーラーを使用した場合に提供されるアセンブリ参照カウントやその他の機能が提供されません。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="c7ce7-117">.NET Framework 4 以降では、グローバル アセンブリ キャッシュの既定の場所は **%windir%\Microsoft.NET\assembly** です。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-117">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="c7ce7-118">.NET Framework の以前のバージョンでは、既定の場所は **%windir%\assembly** です。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="c7ce7-119">通常、管理者は、書き込みおよび実行アクセスを制御するアクセス制御リスト (ACL: Access Control List) を使用して systemroot ディレクトリを保護します。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="c7ce7-120">グローバル アセンブリ キャッシュは、systemroot ディレクトリのサブディレクトリにインストールされるため、このディレクトリの ACL を継承します。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-120">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="c7ce7-121">グローバル アセンブリ キャッシュからファイルを削除する場合は、管理者権限を持つユーザーに対してだけ許可することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-121">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="c7ce7-122">グローバル アセンブリ キャッシュに配置するアセンブリには、厳密な名前を付けておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-122">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="c7ce7-123">アセンブリをグローバル アセンブリ キャッシュに追加すると、アセンブリを構成するすべてのファイルに対して、整合性チェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-123">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="c7ce7-124">キャッシュはこのような整合性チェックを実行することで、ファイルが変更されたにもかかわらず、マニフェストにその変更が反映されていないなど、アセンブリに不整合が生じていないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c7ce7-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ce7-125">参照</span><span class="sxs-lookup"><span data-stu-id="c7ce7-125">See Also</span></span>  
 [<span data-ttu-id="c7ce7-126">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="c7ce7-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="c7ce7-127">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="c7ce7-127">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="c7ce7-128">厳密な名前付きアセンブリ</span><span class="sxs-lookup"><span data-stu-id="c7ce7-128">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
