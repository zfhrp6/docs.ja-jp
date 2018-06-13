---
title: COR_ACTIVE_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86ab3d3a0f460f1ecdf86147b14df205aaf49635
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404201"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="325ba-102">COR_ACTIVE_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="325ba-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="325ba-103">スレッドのフレームで現在アクティブな機能に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="325ba-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="325ba-104">この構造体を使って、 [icordebugthread 2::getactivefunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="325ba-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="325ba-105">構文</span><span class="sxs-lookup"><span data-stu-id="325ba-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="325ba-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="325ba-106">Members</span></span>  
  
|<span data-ttu-id="325ba-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="325ba-107">Member</span></span>|<span data-ttu-id="325ba-108">説明</span><span class="sxs-lookup"><span data-stu-id="325ba-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="325ba-109">アプリケーション ドメインの所有者へのポインター、`ilOffset`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="325ba-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="325ba-110">モジュールの所有者へのポインター、`ilOffset`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="325ba-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="325ba-111">関数の所有者へのポインター、`ilOffset`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="325ba-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="325ba-112">フレームの Microsoft intermediate language (MSIL) オフセットします。</span><span class="sxs-lookup"><span data-stu-id="325ba-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="325ba-113">将来の機能拡張予約されています。</span><span class="sxs-lookup"><span data-stu-id="325ba-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="325ba-114">要件</span><span class="sxs-lookup"><span data-stu-id="325ba-114">Requirements</span></span>  
 <span data-ttu-id="325ba-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="325ba-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="325ba-116">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="325ba-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="325ba-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="325ba-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="325ba-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="325ba-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325ba-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="325ba-119">See Also</span></span>  
 [<span data-ttu-id="325ba-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="325ba-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="325ba-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="325ba-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
