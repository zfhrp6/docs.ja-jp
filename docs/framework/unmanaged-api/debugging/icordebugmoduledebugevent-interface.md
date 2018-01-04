---
title: "ICorDebugModuleDebugEvent インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86cf571180b2df15077547fac3d5dd058dbee83b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="dc451-102">ICorDebugModuleDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc451-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="dc451-103">拡張、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)モジュール レベルのイベントをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="dc451-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc451-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="dc451-104">Methods</span></span>  
  
|<span data-ttu-id="dc451-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dc451-105">Method</span></span>|<span data-ttu-id="dc451-106">説明</span><span class="sxs-lookup"><span data-stu-id="dc451-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc451-107">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="dc451-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="dc451-108">ロードまたはアンロードされたばかりのマージ モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="dc451-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc451-109">コメント</span><span class="sxs-lookup"><span data-stu-id="dc451-109">Remarks</span></span>  
 <span data-ttu-id="dc451-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)と[MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)イベントの種類は、このインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="dc451-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc451-111">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="dc451-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="dc451-112">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="dc451-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc451-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="dc451-113">Requirements</span></span>  
 <span data-ttu-id="dc451-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dc451-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc451-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc451-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc451-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc451-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc451-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc451-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc451-118">参照</span><span class="sxs-lookup"><span data-stu-id="dc451-118">See Also</span></span>  
 [<span data-ttu-id="dc451-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc451-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dc451-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="dc451-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
