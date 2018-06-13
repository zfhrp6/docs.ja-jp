---
title: .NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: ceef4255321e208911a16db0227890bc6654b8c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642925"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="5d2a7-102">.NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d2a7-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="5d2a7-103">同じアプリケーションの COM オブジェクトと .NET Framework オブジェクトを使用する場合は、オブジェクトがメモリ内に存在する方法の違いに対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="5d2a7-104">.NET Framework オブジェクトは、マネージ メモリにある: 共通言語ランタイムによって制御されるメモリ:、必要に応じて、ランタイムによって移動することがあります。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="5d2a7-105">COM オブジェクトでは、アンマネージ メモリ内にあるし、別のメモリ位置に移動するものではありません。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> <span data-ttu-id="5d2a7-106">Visual Studio と[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]これらの相互作用を制御するためのツールがマネージし、アンマネージ コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-106">Visual Studio and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="5d2a7-107">マネージ コードの詳細については、次を参照してください。[共通言語ランタイム](../../../standard/clr.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="5d2a7-108">.NET アプリケーションの COM オブジェクトを使用するだけでなくすることも COM 経由のアンマネージ コードからアクセスできるオブジェクトを開発する Visual Basic を使用するには</span><span class="sxs-lookup"><span data-stu-id="5d2a7-108">In addition to using COM objects in .NET applications, you may also want to use Visual Basic to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="5d2a7-109">このページのリンクは、COM および .NET Framework のオブジェクト間の相互作用の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5d2a7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d2a7-110">Related Sections</span></span>  
 [<span data-ttu-id="5d2a7-111">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="5d2a7-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="5d2a7-112">Visual Basic では、COM オブジェクト、ActiveX コントロール、Win32 の Dll、管理対象のオブジェクトや COM オブジェクトの継承などの COM 相互運用性を説明するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="5d2a7-113">COM 相互運用ラッパー エラー</span><span class="sxs-lookup"><span data-stu-id="5d2a7-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="5d2a7-114">プロジェクト システムは、特定のコンポーネントの COM 相互運用ラッパーを作成できない場合の結果とオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="5d2a7-115">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="5d2a7-115">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="5d2a7-116">簡単な説明、マネージとアンマネージ コード間の相互作用の問題の一部と、さらに調査へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="5d2a7-117">COM ラッパー</span><span class="sxs-lookup"><span data-stu-id="5d2a7-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="5d2a7-118">マネージ コードから COM メソッドを呼び出すには、ランタイム呼び出し可能ラッパーと .NET オブジェクトのメソッドを呼び出す COM クライアントを許可する COM 呼び出し可能ラッパーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="5d2a7-119">高度な COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="5d2a7-119">Advanced COM Interoperability</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="5d2a7-120">ラッパー、例外、継承、スレッド処理、イベント、変換、またはマーシャ リングに関する COM 相互運用性を説明するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="5d2a7-121">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="5d2a7-121">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 <span data-ttu-id="5d2a7-122">共通言語ランタイム アセンブリで等価な定義に、COM タイプ ライブラリ内の型定義の変換に使用できるツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d2a7-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
