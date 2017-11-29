---
title: invalidVariant MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ee537dcb03dc76968b829f827c73542c07922a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="9ad46-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="9ad46-102">invalidVariant MDA</span></span>
<span data-ttu-id="9ad46-103">`invalidVariant` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、ネイティブ コードまたはアンマネージ コードからマネージ コードへの呼び出し時に、無効な `VARIANT` 構造体が見つかるとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="9ad46-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9ad46-104">症状</span><span class="sxs-lookup"><span data-stu-id="9ad46-104">Symptoms</span></span>  
 <span data-ttu-id="9ad46-105">`VARIANT` からオブジェクトへのマーシャリングを含む、ネイティブ コードとマネージ コードの間の遷移中に、予期しない動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="9ad46-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9ad46-106">原因</span><span class="sxs-lookup"><span data-stu-id="9ad46-106">Cause</span></span>  
 <span data-ttu-id="9ad46-107">ネイティブ コードが、不適切な `VARIANT` 構造体をマネージ コードに渡しています。</span><span class="sxs-lookup"><span data-stu-id="9ad46-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="9ad46-108">ランタイムは、この `VARIANT` をオブジェクトにマーシャリングしようとし、`VARIANT` が有効でない場合に MDA がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="9ad46-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="9ad46-109">無効な `VARIANT` には、`VARTYPE` VT_EMPTY &#124; VT_BYREF の `VARIANT` や、`VARTYPE` VT_VARIANT の `VARIANT` などがあります。</span><span class="sxs-lookup"><span data-stu-id="9ad46-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9ad46-110">解決策</span><span class="sxs-lookup"><span data-stu-id="9ad46-110">Resolution</span></span>  
 <span data-ttu-id="9ad46-111">`VARIANT` を渡すネイティブ コードまたはアンマネージ コードでは、`VARIANT` の形式と初期化が正しいことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ad46-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9ad46-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="9ad46-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="9ad46-113">この MDA は、ランタイムの動作への影響はありません。</span><span class="sxs-lookup"><span data-stu-id="9ad46-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9ad46-114">出力</span><span class="sxs-lookup"><span data-stu-id="9ad46-114">Output</span></span>  
 <span data-ttu-id="9ad46-115">無効な `VARIANT` がアンマネージ モジュールによりマネージ コードに渡されたことを、ランタイムが検出したことを示す MDA メッセージです。</span><span class="sxs-lookup"><span data-stu-id="9ad46-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9ad46-116">構成</span><span class="sxs-lookup"><span data-stu-id="9ad46-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ad46-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ad46-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="9ad46-118">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="9ad46-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9ad46-119">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="9ad46-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
