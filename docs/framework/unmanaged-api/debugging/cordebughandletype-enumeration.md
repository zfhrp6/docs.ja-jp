---
title: "CorDebugHandleType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugHandleType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugHandleType
helpviewer_keywords: CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 408c66bd33ba12b2c674dd6c4a049acfb8c4c986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="700a5-102">CorDebugHandleType 列挙型</span><span class="sxs-lookup"><span data-stu-id="700a5-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="700a5-103">ハンドル型を示します。</span><span class="sxs-lookup"><span data-stu-id="700a5-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="700a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="700a5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="700a5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="700a5-105">Members</span></span>  
  
|<span data-ttu-id="700a5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="700a5-106">Member</span></span>|<span data-ttu-id="700a5-107">説明</span><span class="sxs-lookup"><span data-stu-id="700a5-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="700a5-108">ハンドルが、ガベージ コレクションによるクリアされてからオブジェクトを防ぐことをがします。</span><span class="sxs-lookup"><span data-stu-id="700a5-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="700a5-109">ハンドルは、これは防止しませんオブジェクトのガベージ コレクションによって解放される脆弱なです。</span><span class="sxs-lookup"><span data-stu-id="700a5-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="700a5-110">オブジェクトを収集するときに、ハンドルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="700a5-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="700a5-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="700a5-111">Requirements</span></span>  
 <span data-ttu-id="700a5-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="700a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="700a5-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="700a5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="700a5-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="700a5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="700a5-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="700a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700a5-116">参照</span><span class="sxs-lookup"><span data-stu-id="700a5-116">See Also</span></span>  
 [<span data-ttu-id="700a5-117">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="700a5-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
