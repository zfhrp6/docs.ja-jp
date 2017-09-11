---
title: ".NET Framework アプリケーション (Visual Basic) での COM 相互運用性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6b68f35c1c63e2d7d229f89336b86c4a062e5ec9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="9dfb8-102">.NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9dfb8-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="9dfb8-103">同じアプリケーションの COM オブジェクトと .NET Framework のオブジェクトを使用する場合は、オブジェクトをメモリにする方法の違いに対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="9dfb8-104">.NET Framework オブジェクトがマネージ メモリ内に、共通言語ランタイムによって制御されるメモリ: 必要に応じて、ランタイムによって移動できます。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="9dfb8-105">COM オブジェクトでは、アンマネージ メモリ内にあり、別のメモリ位置に移動するものではありません。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="9dfb8-106">および[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]これらの相互作用を制御するためのツールがマネージし、アンマネージ コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-106"> and the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="9dfb8-107">マネージ コードに関する詳細については、次を参照してください。[共通言語ランタイム](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-107">For more information about managed code, see [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span></span>  
  
 <span data-ttu-id="9dfb8-108">.NET アプリケーションで COM オブジェクトを使用するだけでなくすることも使用する[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]COM 経由のアンマネージ コードからアクセス可能なオブジェクトを開発するには</span><span class="sxs-lookup"><span data-stu-id="9dfb8-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="9dfb8-109">このページのリンクは、COM および .NET Framework のオブジェクト間の対話についての詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9dfb8-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dfb8-110">Related Sections</span></span>  
 [<span data-ttu-id="9dfb8-111">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="9dfb8-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="9dfb8-112">COM オブジェクト、ActiveX コントロール、Win32 Dll、マネージ オブジェクトおよび COM オブジェクトの継承を含む Visual Basic での COM 相互運用性を説明するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="9dfb8-113">COM 相互運用ラッパー エラー</span><span class="sxs-lookup"><span data-stu-id="9dfb8-113">COM Interop Wrapper Error</span></span>](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="9dfb8-114">プロジェクト システムは、特定のコンポーネントの COM 相互運用ラッパーを作成できない場合の結果とオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="9dfb8-115">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="9dfb8-115">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="9dfb8-116">について簡単にマネージ コードとアンマネージ コード間の相互作用の問題のいくつかについて説明し、詳細な情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="9dfb8-117">COM ラッパー</span><span class="sxs-lookup"><span data-stu-id="9dfb8-117">COM Wrappers</span></span>](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 <span data-ttu-id="9dfb8-118">マネージ コードを COM メソッドを呼び出すには、ランタイム呼び出し可能ラッパーと、.NET オブジェクトのメソッドを呼び出す COM クライアントを許可する COM 呼び出し可能ラッパーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="9dfb8-119">高度な COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="9dfb8-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="9dfb8-120">ラッパー、例外、継承、スレッド処理、イベント、変換、またはマーシャ リングに関する COM 相互運用性を説明するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="9dfb8-121">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="9dfb8-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="9dfb8-122">共通言語ランタイム アセンブリで等価な定義に、COM タイプ ライブラリ内で見つかった種類の定義の変換に使用できるツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9dfb8-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
