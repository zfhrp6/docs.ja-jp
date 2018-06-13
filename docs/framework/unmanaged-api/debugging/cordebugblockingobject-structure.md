---
title: CorDebugBlockingObject 構造体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed7db321b32657087b791758096c692f25f3d7f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407837"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="9cf33-102">CorDebugBlockingObject 構造体</span><span class="sxs-lookup"><span data-stu-id="9cf33-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="9cf33-103">スレッドとスレッドがブロックされている特定の理由をブロックしているオブジェクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="9cf33-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf33-104">構文</span><span class="sxs-lookup"><span data-stu-id="9cf33-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="9cf33-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9cf33-105">Members</span></span>  
  
|<span data-ttu-id="9cf33-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9cf33-106">Member</span></span>|<span data-ttu-id="9cf33-107">説明</span><span class="sxs-lookup"><span data-stu-id="9cf33-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="9cf33-108">スレッドがブロックしているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9cf33-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="9cf33-109">このオブジェクトは、現在の同期状態の期間に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="9cf33-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="9cf33-110">予想される場合があります、同じ同期された状態で同じオブジェクトで 2 つのスレッドのブロックは場合、 [icordebugvalue::getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)を同じ値を返すメソッド。</span><span class="sxs-lookup"><span data-stu-id="9cf33-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="9cf33-111">ただし、インターフェイスは、同等のポインターができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9cf33-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="9cf33-112">ブロックしている操作の前に時間をミリ秒単位は、タイムアウト、または値を示すものではタイムアウトしない INFINITE されます。タイムアウト値は、時間が残っているではなく、ブロック操作の時間の合計の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="9cf33-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="9cf33-113">このオブジェクトのスレッドがブロックされている理由です。</span><span class="sxs-lookup"><span data-stu-id="9cf33-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cf33-114">コメント</span><span class="sxs-lookup"><span data-stu-id="9cf33-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cf33-115">要件</span><span class="sxs-lookup"><span data-stu-id="9cf33-115">Requirements</span></span>  
 <span data-ttu-id="9cf33-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9cf33-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cf33-117">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="9cf33-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="9cf33-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cf33-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cf33-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cf33-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf33-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cf33-120">See Also</span></span>  
 [<span data-ttu-id="9cf33-121">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="9cf33-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="9cf33-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9cf33-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
