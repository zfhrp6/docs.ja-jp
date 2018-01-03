---
title: "ICorDebugDebugEvent インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c4d777d601866ca9600a7e2b88aca8854f32a17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="8a3f1-102">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a3f1-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="8a3f1-103">すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="8a3f1-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a3f1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8a3f1-104">Methods</span></span>  
  
|<span data-ttu-id="8a3f1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8a3f1-105">Method</span></span>|<span data-ttu-id="8a3f1-106">説明</span><span class="sxs-lookup"><span data-stu-id="8a3f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a3f1-107">GetEventKind メソッド</span><span class="sxs-lookup"><span data-stu-id="8a3f1-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="8a3f1-108">この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="8a3f1-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="8a3f1-109">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="8a3f1-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="8a3f1-110">イベントが発生したスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a3f1-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a3f1-111">コメント</span><span class="sxs-lookup"><span data-stu-id="8a3f1-111">Remarks</span></span>  
 <span data-ttu-id="8a3f1-112">次のインターフェイスは、`ICorDebugDebugEvent` インターフェイスから派生したものです。</span><span class="sxs-lookup"><span data-stu-id="8a3f1-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="8a3f1-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="8a3f1-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="8a3f1-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="8a3f1-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="8a3f1-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="8a3f1-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="8a3f1-116">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="8a3f1-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a3f1-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="8a3f1-117">Requirements</span></span>  
 <span data-ttu-id="8a3f1-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a3f1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a3f1-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a3f1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a3f1-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a3f1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a3f1-121">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a3f1-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3f1-122">参照</span><span class="sxs-lookup"><span data-stu-id="8a3f1-122">See Also</span></span>  
 [<span data-ttu-id="8a3f1-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a3f1-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8a3f1-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8a3f1-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
