---
title: "CorDebugDebugEventKind 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDebugEventKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90cd2b8d02cb1d16e4932ffdcc3c9b02dc71541a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="9e107-102">CorDebugDebugEventKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="9e107-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="9e107-103">情報がデコードされるによってイベントの種類を示す、 [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9e107-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e107-104">構文</span><span class="sxs-lookup"><span data-stu-id="9e107-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="9e107-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9e107-105">Members</span></span>  
  
|<span data-ttu-id="9e107-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9e107-106">Member</span></span>|<span data-ttu-id="9e107-107">説明</span><span class="sxs-lookup"><span data-stu-id="9e107-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="9e107-108">モジュールの読み込みイベント。</span><span class="sxs-lookup"><span data-stu-id="9e107-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="9e107-109">モジュールのアンロード イベント。</span><span class="sxs-lookup"><span data-stu-id="9e107-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="9e107-110">初回例外。</span><span class="sxs-lookup"><span data-stu-id="9e107-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="9e107-111">ユーザーの初回例外。</span><span class="sxs-lookup"><span data-stu-id="9e107-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="9e107-112">`catch` ハンドラーが存在する例外。</span><span class="sxs-lookup"><span data-stu-id="9e107-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="9e107-113">未処理の例外。</span><span class="sxs-lookup"><span data-stu-id="9e107-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e107-114">コメント</span><span class="sxs-lookup"><span data-stu-id="9e107-114">Remarks</span></span>  
 <span data-ttu-id="9e107-115">メンバー、`CorDebugDebugEventKind`列挙体が呼び出しによって返される、 [icordebugdebugevent::geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9e107-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e107-116">この列挙体は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="9e107-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e107-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="9e107-117">Requirements</span></span>  
 <span data-ttu-id="9e107-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e107-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e107-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e107-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e107-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e107-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e107-121">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e107-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e107-122">参照</span><span class="sxs-lookup"><span data-stu-id="9e107-122">See Also</span></span>  
 [<span data-ttu-id="9e107-123">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="9e107-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
