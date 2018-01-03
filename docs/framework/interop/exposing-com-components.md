---
title: ".NET Framework への COM コンポーネントの公開"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9361de4726b1dc58238db5ca7b5605f2cc75485d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="b24c1-102">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="b24c1-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="b24c1-103">このセクションでは、既存の COM コンポーネントをマネージ コードに公開するために必要なプロセスをまとめています。</span><span class="sxs-lookup"><span data-stu-id="b24c1-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="b24c1-104">.NET Framework と緊密に統合される COM サーバーの詳細については、「[Design Considerations for Interoperation](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)」(相互運用のためのデザインの考慮事項) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b24c1-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).</span></span>  
  
 <span data-ttu-id="b24c1-105">既存の COM コンポーネントは、中間層のビジネス アプリケーション、または独立した機能として、マネージ コードでの貴重なリソースです。</span><span class="sxs-lookup"><span data-stu-id="b24c1-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="b24c1-106">理想的なコンポーネントは、プライマリ相互運用機能アセンブリがあり、COM で課せられるプログラミング標準に厳密に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="b24c1-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="b24c1-107">.NET Framework に COM コンポーネントを公開するには</span><span class="sxs-lookup"><span data-stu-id="b24c1-107">To expose COM components to the .NET Framework</span></span>  
  
1.  <span data-ttu-id="b24c1-108">[タイプ ライブラリをアセンブリとしてインポートする](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="b24c1-108">[Import a type library as an assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="b24c1-109">共通言語ランタイムでは、COM 型を含め、すべてのタイプにメタデータが必要です。</span><span class="sxs-lookup"><span data-stu-id="b24c1-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="b24c1-110">メタデータとしてインポートされた COM 型を含むアセンブリを取得するには、複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="b24c1-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2.  <span data-ttu-id="b24c1-111">[マネージ コードで COM 型を作成する](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)。</span><span class="sxs-lookup"><span data-stu-id="b24c1-111">[Create COM types in managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span></span>  
  
     <span data-ttu-id="b24c1-112">任意のマネージ型で行うのと同じ方法で、COM オブジェクトで COM 型の検査、インスタンスのアクティブ化、およびメソッドの呼び出しができます。</span><span class="sxs-lookup"><span data-stu-id="b24c1-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3.  <span data-ttu-id="b24c1-113">[相互運用プロジェクトをコンパイルする](../../../docs/framework/interop/compiling-an-interop-project.md)。</span><span class="sxs-lookup"><span data-stu-id="b24c1-113">[Compile an interop project](../../../docs/framework/interop/compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="b24c1-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] では、共通言語仕様 (CLS) に準拠する複数の言語 ([!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C#、C++ など) のコンパイラが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b24c1-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4.  <span data-ttu-id="b24c1-115">[相互運用アプリケーションを展開する](../../../docs/framework/interop/deploying-an-interop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b24c1-115">[Deploy an interop application](../../../docs/framework/interop/deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="b24c1-116">相互運用アプリケーションは、[厳密な名前を付けた](../../../docs/framework/app-domains/strong-named-assemblies.md)、署名されたアセンブリとして、グローバル アセンブリ キャッシュに最適に展開されます。</span><span class="sxs-lookup"><span data-stu-id="b24c1-116">Interop applications are best deployed as [strong-named](../../../docs/framework/app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24c1-117">参照</span><span class="sxs-lookup"><span data-stu-id="b24c1-117">See Also</span></span>  
 [<span data-ttu-id="b24c1-118">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="b24c1-118">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="b24c1-119">相互運用のためのデザインの考慮事項</span><span class="sxs-lookup"><span data-stu-id="b24c1-119">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 [<span data-ttu-id="b24c1-120">COM 相互運用機能のサンプル: .NET クライアントおよび COM サーバー</span><span class="sxs-lookup"><span data-stu-id="b24c1-120">COM Interop Sample: .NET Client and COM Server</span></span>](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)  
 [<span data-ttu-id="b24c1-121">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b24c1-121">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="b24c1-122">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="b24c1-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
