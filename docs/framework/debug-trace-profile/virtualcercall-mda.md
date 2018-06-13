---
title: virtualCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2f2104768144da244679e5d0be884d70a3ba6b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386653"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="62f90-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="62f90-102">virtualCERCall MDA</span></span>
<span data-ttu-id="62f90-103">`virtualCERCall` マネージ デバッグ アシスタント (MDA) は、制約された実行領域 (CER) 呼び出し先の呼び出しサイトが、仮想ターゲット (つまり、インターフェイスを使用した最終ではない仮想メソッドまたは呼び出しの仮想呼び出し) を参照していることを示す警告としてアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="62f90-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="62f90-104">共通言語ランタイム (CLR) は、中間言語およびメタデータの分析だけでは、これらの呼び出しの呼び出し先メソッドを予測できません。</span><span class="sxs-lookup"><span data-stu-id="62f90-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="62f90-105">その結果、CER グラフの一部としてコール ツリーを準備できません。また、そのサブツリー内のスレッドの中止を自動的にブロックできません。</span><span class="sxs-lookup"><span data-stu-id="62f90-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="62f90-106">呼び出し対象の計算に必要な追加情報が実行時に判明すると、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> メソッドの明示的な呼び出しを使用して CER の拡張が必要な可能性がある場合に、この MDA は警告します。</span><span class="sxs-lookup"><span data-stu-id="62f90-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="62f90-107">現象</span><span class="sxs-lookup"><span data-stu-id="62f90-107">Symptoms</span></span>  
 <span data-ttu-id="62f90-108">スレッドが中止されたとき、またはアプリケーション ドメインがアンロードされたときに CER が実行されません。</span><span class="sxs-lookup"><span data-stu-id="62f90-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="62f90-109">原因</span><span class="sxs-lookup"><span data-stu-id="62f90-109">Cause</span></span>  
 <span data-ttu-id="62f90-110">CER に、自動的に準備できない仮想メソッドの呼び出しが含まれています。</span><span class="sxs-lookup"><span data-stu-id="62f90-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="62f90-111">解像度</span><span class="sxs-lookup"><span data-stu-id="62f90-111">Resolution</span></span>  
 <span data-ttu-id="62f90-112">仮想メソッドの <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="62f90-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="62f90-113">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="62f90-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="62f90-114">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="62f90-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="62f90-115">出力</span><span class="sxs-lookup"><span data-stu-id="62f90-115">Output</span></span>  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="62f90-116">構成</span><span class="sxs-lookup"><span data-stu-id="62f90-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="62f90-117">例</span><span class="sxs-lookup"><span data-stu-id="62f90-117">Example</span></span>  
  
```  
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="62f90-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="62f90-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="62f90-119">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="62f90-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="62f90-120">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="62f90-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
