---
title: "ISymUnmanagedAsyncMethod インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3ee944940cef0d3162a020c81353fd6b8cfb82f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="69d71-102">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69d71-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="69d71-103">このインターフェイスは、読み取りの補足[ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="69d71-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d71-104">構文</span><span class="sxs-lookup"><span data-stu-id="69d71-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="69d71-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-105">Methods</span></span>  
 <span data-ttu-id="69d71-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="69d71-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="69d71-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-107">Method</span></span>|<span data-ttu-id="69d71-108">説明</span><span class="sxs-lookup"><span data-stu-id="69d71-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69d71-109">GetAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="69d71-110">参照してください[DefineAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="69d71-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="69d71-111">GetAsyncStepInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="69d71-112">参照してください[DefineAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="69d71-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="69d71-113">GetCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="69d71-114">参照してください[DefineCatchHandlerILOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="69d71-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="69d71-115">GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="69d71-116">参照してください[DefineKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="69d71-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="69d71-117">HasCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="69d71-118">参照してください[DefineCatchHandlerILOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="69d71-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="69d71-119">IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="69d71-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="69d71-120">か、メソッドが非同期の情報を持つかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="69d71-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="69d71-121">このメソッドが戻る場合`FALSE`し、このインターフェイスで、他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="69d71-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="69d71-122">すべての戻り値は`E_UNEXPECTED`ここでします。</span><span class="sxs-lookup"><span data-stu-id="69d71-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69d71-123">要件</span><span class="sxs-lookup"><span data-stu-id="69d71-123">Requirements</span></span>  
 <span data-ttu-id="69d71-124">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="69d71-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d71-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="69d71-125">See Also</span></span>  
 [<span data-ttu-id="69d71-126">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="69d71-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
