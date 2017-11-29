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
ms.openlocfilehash: dced93ab39529ec57fb6fb99603a197fb957be8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="23b6d-102">ICorDebugModuleDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23b6d-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="23b6d-103">拡張、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)モジュール レベルのイベントをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23b6d-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23b6d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="23b6d-104">Methods</span></span>  
  
|<span data-ttu-id="23b6d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="23b6d-105">Method</span></span>|<span data-ttu-id="23b6d-106">説明</span><span class="sxs-lookup"><span data-stu-id="23b6d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23b6d-107">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="23b6d-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="23b6d-108">ロードまたはアンロードされたばかりのマージ モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="23b6d-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b6d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="23b6d-109">Remarks</span></span>  
 <span data-ttu-id="23b6d-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)と[MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)イベントの種類は、このインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="23b6d-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23b6d-111">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="23b6d-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="23b6d-112">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="23b6d-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b6d-113">要件</span><span class="sxs-lookup"><span data-stu-id="23b6d-113">Requirements</span></span>  
 <span data-ttu-id="23b6d-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="23b6d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b6d-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23b6d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23b6d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23b6d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23b6d-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b6d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b6d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="23b6d-118">See Also</span></span>  
 [<span data-ttu-id="23b6d-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="23b6d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="23b6d-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="23b6d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
