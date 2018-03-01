---
title: "CorDebugExceptionCallbackType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4efc969395e30dcc237d2ad99c9bc67ee30f4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="4fea5-102">CorDebugExceptionCallbackType 列挙型</span><span class="sxs-lookup"><span data-stu-id="4fea5-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="4fea5-103">指定されたコールバックの型を示す、 [icordebugmanagedcallback 2::exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)イベント。</span><span class="sxs-lookup"><span data-stu-id="4fea5-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fea5-104">構文</span><span class="sxs-lookup"><span data-stu-id="4fea5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="4fea5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4fea5-105">Members</span></span>  
  
|<span data-ttu-id="4fea5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4fea5-106">Member</span></span>|<span data-ttu-id="4fea5-107">説明</span><span class="sxs-lookup"><span data-stu-id="4fea5-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="4fea5-108">例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="4fea5-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="4fea5-109">例外のワインド プロセスでは、ユーザー コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="4fea5-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="4fea5-110">例外ワインド プロセスの検出、`catch`ユーザー コードのブロックです。</span><span class="sxs-lookup"><span data-stu-id="4fea5-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="4fea5-111">例外は処理されませんでした。</span><span class="sxs-lookup"><span data-stu-id="4fea5-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fea5-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="4fea5-112">Requirements</span></span>  
 <span data-ttu-id="4fea5-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4fea5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fea5-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fea5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fea5-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fea5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fea5-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fea5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fea5-117">参照</span><span class="sxs-lookup"><span data-stu-id="4fea5-117">See Also</span></span>  
 [<span data-ttu-id="4fea5-118">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="4fea5-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
