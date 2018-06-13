---
title: CorDebugHandleType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2898f530fe3f9368778d0f854e8254f7b32d5293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404938"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="2d16b-102">CorDebugHandleType 列挙型</span><span class="sxs-lookup"><span data-stu-id="2d16b-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="2d16b-103">ハンドル型を示します。</span><span class="sxs-lookup"><span data-stu-id="2d16b-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d16b-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d16b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="2d16b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2d16b-105">Members</span></span>  
  
|<span data-ttu-id="2d16b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2d16b-106">Member</span></span>|<span data-ttu-id="2d16b-107">説明</span><span class="sxs-lookup"><span data-stu-id="2d16b-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="2d16b-108">ハンドルが、ガベージ コレクションによるクリアされてからオブジェクトを防ぐことをがします。</span><span class="sxs-lookup"><span data-stu-id="2d16b-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="2d16b-109">ハンドルは、これは防止しませんオブジェクトのガベージ コレクションによって解放される脆弱なです。</span><span class="sxs-lookup"><span data-stu-id="2d16b-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="2d16b-110">オブジェクトを収集するときに、ハンドルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="2d16b-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d16b-111">要件</span><span class="sxs-lookup"><span data-stu-id="2d16b-111">Requirements</span></span>  
 <span data-ttu-id="2d16b-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d16b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d16b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d16b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d16b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d16b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d16b-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d16b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d16b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d16b-116">See Also</span></span>  
 [<span data-ttu-id="2d16b-117">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="2d16b-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
