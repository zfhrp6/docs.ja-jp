---
title: nonComVisibleBaseClass MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b00d8396b07eb445414fb85cd830d595a513be0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="008ae-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="008ae-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="008ae-103">`nonComVisibleBaseClass` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、COM 参照可能ではない基本クラスから派生した COM 参照可能マネージ クラスの COM 呼び出し可能ラッパー (CCW: COM Callable Wrapper) で、ネイティブ コードまたはアンマネージ コードによって `QueryInterface` 呼び出しがなされるとアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="008ae-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="008ae-104">`QueryInterface` 呼び出しによって MDA がアクティブになるのは、COM 参照可能マネージ クラスのクラス インターフェイスまたは既定の `IDispatch` が呼び出しによって要求された場合のみです。</span><span class="sxs-lookup"><span data-stu-id="008ae-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="008ae-105">`QueryInterface` 呼び出しが、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性が適用され、COM 参照可能クラスによって明示的に実装された明示的なインターフェイスに対する呼び出しである場合、この MDA はアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="008ae-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="008ae-106">症状</span><span class="sxs-lookup"><span data-stu-id="008ae-106">Symptoms</span></span>  
 <span data-ttu-id="008ae-107">ネイティブ コードからなされた `QueryInterface` 呼び出しが COR_E_INVALIDOPERATION HRESULT により失敗します。</span><span class="sxs-lookup"><span data-stu-id="008ae-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="008ae-108">HRESULT は、この MDA をアクティブにする `QueryInterface` 呼び出しをランタイムが許可しないことによって発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="008ae-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="008ae-109">原因</span><span class="sxs-lookup"><span data-stu-id="008ae-109">Cause</span></span>  
 <span data-ttu-id="008ae-110">ランタイムは、COM 参照可能ではないクラスから派生した COM 参照可能クラスのクラス インターフェイスまたは既定の `IDispatch` インターフェイスに対する `QueryInterface` 呼び出しを許可できません。これは、バージョン管理に関係する問題が発生する可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="008ae-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="008ae-111">たとえば、COM 参照可能でない基本クラスにパブリック メンバーを追加した場合、基本クラス メンバーを含む派生クラスの vtable がこの変更によって変更されるため、派生クラスを使用する既存の COM クライアントが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="008ae-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="008ae-112">COM に公開されている明示的なインターフェイスの場合は、インターフェイスの基本メンバーが vtable に含まれないため、この問題は発生しません。</span><span class="sxs-lookup"><span data-stu-id="008ae-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="008ae-113">解像度</span><span class="sxs-lookup"><span data-stu-id="008ae-113">Resolution</span></span>  
 <span data-ttu-id="008ae-114">クラス インターフェイスを公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="008ae-114">Do not expose the class interface.</span></span> <span data-ttu-id="008ae-115">明示的なインターフェイスを定義し、それに <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="008ae-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="008ae-116">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="008ae-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="008ae-117">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="008ae-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="008ae-118">出力</span><span class="sxs-lookup"><span data-stu-id="008ae-118">Output</span></span>  
 <span data-ttu-id="008ae-119">非 COM 参照可能クラス `Base` から派生した COM 参照可能クラス `Derived` で `QueryInterface` 呼び出しを実行した場合のメッセージ例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="008ae-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="008ae-120">構成</span><span class="sxs-lookup"><span data-stu-id="008ae-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="008ae-121">参照</span><span class="sxs-lookup"><span data-stu-id="008ae-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="008ae-122">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="008ae-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="008ae-123">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="008ae-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
