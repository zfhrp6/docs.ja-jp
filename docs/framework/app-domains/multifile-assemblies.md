---
title: "マルチファイル アセンブリ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bded4fae854d10a17ddd03b8855f6096e18ab87f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="multifile-assemblies"></a><span data-ttu-id="d64a6-102">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="d64a6-102">Multifile Assemblies</span></span>
<span data-ttu-id="d64a6-103">コマンド ライン コンパイラまたは Visual C++ で [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] を使って、マルチファイル アセンブリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d64a6-103">You can create multifile assemblies using command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] with Visual C++.</span></span> <span data-ttu-id="d64a6-104">アセンブリ内の 1 つのファイルには、アセンブリ マニフェストが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d64a6-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="d64a6-105">アプリケーションを起動するアセンブリには、Main メソッドや WinMain メソッドなどのエントリ ポイントも含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d64a6-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>  
  
 <span data-ttu-id="d64a6-106">たとえば、2 つのコード モジュール Client.cs と Stringer.cs を含むアプリケーションがあるものとします。</span><span class="sxs-lookup"><span data-stu-id="d64a6-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="d64a6-107">Stringer.cs は、Client.cs 内のコードによって参照される `myStringer` 名前空間を作成します。</span><span class="sxs-lookup"><span data-stu-id="d64a6-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="d64a6-108">Client.cs には、アプリケーションのエントリ ポイントである `Main` メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d64a6-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="d64a6-109">この例では、2 つのコード モジュールをコンパイルし、さらにアプリケーションを起動するアセンブリ マニフェストを含む 3 番目のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d64a6-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="d64a6-110">アセンブリ マニフェストは、`Client` モジュールと `Stringer` モジュールの両方を参照します。</span><span class="sxs-lookup"><span data-stu-id="d64a6-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d64a6-111">アセンブリに複数のコード モジュールがある場合でも、マルチファイル アセンブリが持つことのできるエントリ ポイントは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="d64a6-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>  
  
 <span data-ttu-id="d64a6-112">マルチファイル アセンブリを作成するのにはいくつかの理由があります。</span><span class="sxs-lookup"><span data-stu-id="d64a6-112">There are several reasons you might want to create a multifile assembly:</span></span>  
  
-   <span data-ttu-id="d64a6-113">異なる言語で記述されたモジュールを結合するため。</span><span class="sxs-lookup"><span data-stu-id="d64a6-113">To combine modules written in different languages.</span></span> <span data-ttu-id="d64a6-114">これは、マルチファイル アセンブリを作成する最も一般的な理由です。</span><span class="sxs-lookup"><span data-stu-id="d64a6-114">This is the most common reason for creating a multifile assembly.</span></span>  
  
-   <span data-ttu-id="d64a6-115">使用頻度の低い型を、必要なときにだけダウンロードされるモジュールに入れることにより、アプリケーションのダウンロードを最適化するため。</span><span class="sxs-lookup"><span data-stu-id="d64a6-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d64a6-116">Microsoft Internet Explorer で `<object>` タグを使ってダウンロードされるアプリケーションを作成する場合は、マルチファイル アセンブリを作成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="d64a6-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="d64a6-117">このシナリオでは、コード モジュールとは別に、アセンブリ マニフェストだけを含むファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d64a6-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="d64a6-118">Internet Explorer は、最初にアセンブリ マニフェストをダウンロードした後、ワーカー スレッドを作成して、追加のモジュールまたは必要なアセンブリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d64a6-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="d64a6-119">アセンブリ マニフェストが含まれるファイルがダウンロードしている間、Internet Explorer はユーザー入力に応答できません。</span><span class="sxs-lookup"><span data-stu-id="d64a6-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="d64a6-120">アセンブリ マニフェストを含むファイルが小さいほど、Internet Explorer が応答しない時間が短くなります。</span><span class="sxs-lookup"><span data-stu-id="d64a6-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>  
  
-   <span data-ttu-id="d64a6-121">複数の開発者が記述したコード モジュールを結合するため。</span><span class="sxs-lookup"><span data-stu-id="d64a6-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="d64a6-122">開発者ごとに各コード モジュールをアセンブリにコンパイルすることもできますが、そうすると、すべてのモジュールがマルチファイル アセンブリに収められている場合であれば公開されない一部の型が強制的に公開されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d64a6-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>  
  
 <span data-ttu-id="d64a6-123">アセンブリを作成した後は、アセンブリ マニフェスト (以降アセンブリ) を含むファイルに署名したり、ファイル (およびアセンブリ) に厳密な名前を付けて、グローバル アセンブリ キャッシュに配置したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="d64a6-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64a6-124">参照</span><span class="sxs-lookup"><span data-stu-id="d64a6-124">See Also</span></span>  
 [<span data-ttu-id="d64a6-125">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="d64a6-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="d64a6-126">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="d64a6-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
