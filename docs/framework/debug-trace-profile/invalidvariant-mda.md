---
title: invalidVariant MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 426b9df449b12d2f34fa70fc721cc050fa3e4ddd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386720"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="64efc-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="64efc-102">invalidVariant MDA</span></span>
<span data-ttu-id="64efc-103">`invalidVariant` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、ネイティブ コードまたはアンマネージ コードからマネージ コードへの呼び出し時に、無効な `VARIANT` 構造体が見つかるとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="64efc-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="64efc-104">症状</span><span class="sxs-lookup"><span data-stu-id="64efc-104">Symptoms</span></span>  
 <span data-ttu-id="64efc-105">`VARIANT` からオブジェクトへのマーシャリングを含む、ネイティブ コードとマネージ コードの間の遷移中に、予期しない動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="64efc-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="64efc-106">原因</span><span class="sxs-lookup"><span data-stu-id="64efc-106">Cause</span></span>  
 <span data-ttu-id="64efc-107">ネイティブ コードが、不適切な `VARIANT` 構造体をマネージ コードに渡しています。</span><span class="sxs-lookup"><span data-stu-id="64efc-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="64efc-108">ランタイムは、この `VARIANT` をオブジェクトにマーシャリングしようとし、`VARIANT` が有効でない場合に MDA がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="64efc-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="64efc-109">無効な `VARIANT` には、`VARTYPE` VT_EMPTY &#124; VT_BYREF の `VARIANT` や、`VARTYPE` VT_VARIANT の `VARIANT` などがあります。</span><span class="sxs-lookup"><span data-stu-id="64efc-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="64efc-110">解像度</span><span class="sxs-lookup"><span data-stu-id="64efc-110">Resolution</span></span>  
 <span data-ttu-id="64efc-111">`VARIANT` を渡すネイティブ コードまたはアンマネージ コードでは、`VARIANT` の形式と初期化が正しいことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64efc-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="64efc-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="64efc-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="64efc-113">この MDA は、ランタイムの動作への影響はありません。</span><span class="sxs-lookup"><span data-stu-id="64efc-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="64efc-114">出力</span><span class="sxs-lookup"><span data-stu-id="64efc-114">Output</span></span>  
 <span data-ttu-id="64efc-115">無効な `VARIANT` がアンマネージ モジュールによりマネージ コードに渡されたことを、ランタイムが検出したことを示す MDA メッセージです。</span><span class="sxs-lookup"><span data-stu-id="64efc-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="64efc-116">構成</span><span class="sxs-lookup"><span data-stu-id="64efc-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64efc-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="64efc-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="64efc-118">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="64efc-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="64efc-119">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="64efc-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
