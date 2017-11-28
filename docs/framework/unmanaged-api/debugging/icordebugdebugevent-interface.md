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
ms.openlocfilehash: b4422b165f06b60dedff95fc3de58e5627db7fac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="7ebe0-102">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7ebe0-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="7ebe0-103">すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="7ebe0-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ebe0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7ebe0-104">Methods</span></span>  
  
|<span data-ttu-id="7ebe0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7ebe0-105">Method</span></span>|<span data-ttu-id="7ebe0-106">説明</span><span class="sxs-lookup"><span data-stu-id="7ebe0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ebe0-107">GetEventKind メソッド</span><span class="sxs-lookup"><span data-stu-id="7ebe0-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="7ebe0-108">この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="7ebe0-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="7ebe0-109">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="7ebe0-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="7ebe0-110">イベントが発生したスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="7ebe0-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ebe0-111">コメント</span><span class="sxs-lookup"><span data-stu-id="7ebe0-111">Remarks</span></span>  
 <span data-ttu-id="7ebe0-112">次のインターフェイスは、`ICorDebugDebugEvent` インターフェイスから派生したものです。</span><span class="sxs-lookup"><span data-stu-id="7ebe0-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="7ebe0-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="7ebe0-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="7ebe0-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="7ebe0-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="7ebe0-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="7ebe0-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="7ebe0-116">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="7ebe0-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ebe0-117">要件</span><span class="sxs-lookup"><span data-stu-id="7ebe0-117">Requirements</span></span>  
 <span data-ttu-id="7ebe0-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7ebe0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ebe0-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ebe0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ebe0-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ebe0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ebe0-121">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ebe0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebe0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ebe0-122">See Also</span></span>  
 [<span data-ttu-id="7ebe0-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7ebe0-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7ebe0-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="7ebe0-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
