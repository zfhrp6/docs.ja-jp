---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9938db3f4a3d054fde52139c166fb6a2e2a402df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388057"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="394af-102">pInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="394af-102">pInvokeStackImbalance MDA</span></span>
<span data-ttu-id="394af-103"><xref:System.Runtime.InteropServices.DllImportAttribute> の属性で指定される呼び出し規約、およびマネージ シグネチャ内のパラメーターの宣言が指定されている場合に、プラットフォーム呼び出しが、予想されるスタックの深さに一致しないことを CLR が検出したときに、`pInvokeStackImbalance` マネージ デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="394af-103">The `pInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute as well as the declaration of the parameters in the managed signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="394af-104">`pInvokeStackImbalance` MDA は 32 ビット x86 プラットフォームに対してのみ実装されています。</span><span class="sxs-lookup"><span data-stu-id="394af-104">The `pInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="394af-105">.NET Framework version 3.5 で、 `pInvokeStackImbalance` MDA は既定で無効になります。</span><span class="sxs-lookup"><span data-stu-id="394af-105">In the .NET Framework version 3.5, the `pInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="394af-106">.NET Framework version 3.5 と Visual Studio 2005 を使用すると、`pInvokeStackImbalance` MDA が **[例外]** ダイアログ ボックス (**[デバッグ]** メニューの **[例外]** をクリックすると表示される) の **[マネージ デバッグ アシスタント]** の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="394af-106">When you use the .NET Framework version 3.5 with Visual Studio 2005, the `pInvokeStackImbalance` MDA will appear in the **Managed Debugging Assistants** list in the **Exceptions** dialog box (which is displayed when you click **Exceptions** on the **Debug** menu).</span></span> <span data-ttu-id="394af-107">ただし、`pInvokeStackImbalance` の **[スローされるとき]** のチェック ボックスをオンまたはオフにしても、MDA は有効または無効になりません。MDA がアクティブ化されたときに Visual Studio が例外をスローするかどうかのみを制御します。</span><span class="sxs-lookup"><span data-stu-id="394af-107">However, selecting or clearing the **Thrown** check box for `pInvokeStackImbalance` does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="394af-108">現象</span><span class="sxs-lookup"><span data-stu-id="394af-108">Symptoms</span></span>  
 <span data-ttu-id="394af-109">プラットフォーム呼び出しの実行時または実行後に、アプリケーションでアクセス違反またはメモリ破損が発生します。</span><span class="sxs-lookup"><span data-stu-id="394af-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="394af-110">原因</span><span class="sxs-lookup"><span data-stu-id="394af-110">Cause</span></span>  
 <span data-ttu-id="394af-111">プラットフォーム呼び出しのマネージ シグネチャが、呼び出されているメソッドのアンマネージ シグネチャと一致しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="394af-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="394af-112">この不一致は、正しい数のパラメーターを宣言しないか、適切なサイズのパラメーターを指定しないマネージ シグネチャで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="394af-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="394af-113">また、<xref:System.Runtime.InteropServices.DllImportAttribute> 属性によって指定されている可能性がある呼び出し規約が、アンマネージ呼び出し規約と一致しない場合にも、MDA がアクティブ化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="394af-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="394af-114">解像度</span><span class="sxs-lookup"><span data-stu-id="394af-114">Resolution</span></span>  
 <span data-ttu-id="394af-115">マネージ プラットフォーム呼び出しシグネチャ、および呼び出し規則を確認して、ネイティブ ターゲットのシグネチャと呼び出し規約に一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="394af-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="394af-116">マネージ側とアンマネージ側の両方で、呼び出し規約を明示的に指定してください。</span><span class="sxs-lookup"><span data-stu-id="394af-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="394af-117">また、あまり可能性はありませんが、アンマネージ コンパイラのバグなど、何らかの理由によりアンマネージ関数でスタックの不均衡が発生している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="394af-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="394af-118">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="394af-118">Effect on the Runtime</span></span>  
 <span data-ttu-id="394af-119">すべてのプラットフォーム呼び出しが、CLR の最適化されていないパスを取得するよう強制します。</span><span class="sxs-lookup"><span data-stu-id="394af-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="394af-120">出力</span><span class="sxs-lookup"><span data-stu-id="394af-120">Output</span></span>  
 <span data-ttu-id="394af-121">MDA メッセージが、スタックの不均衡の原因であるプラットフォーム呼び出しメソッド呼び出しの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="394af-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span>  <span data-ttu-id="394af-122">メソッド `SampleMethod` のプラットフォーム呼び出しのサンプル メッセージは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="394af-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a><span data-ttu-id="394af-123">構成</span><span class="sxs-lookup"><span data-stu-id="394af-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="394af-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="394af-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="394af-125">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="394af-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="394af-126">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="394af-126">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
