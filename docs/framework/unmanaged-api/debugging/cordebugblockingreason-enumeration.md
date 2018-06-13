---
title: CorDebugBlockingReason 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe5e1267b619d5900ed9af55dd6079a8f38d6550
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406901"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="31fe6-102">CorDebugBlockingReason 列挙体</span><span class="sxs-lookup"><span data-stu-id="31fe6-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="31fe6-103">指定されたオブジェクト上でスレッドがブロックされる理由を指定します。</span><span class="sxs-lookup"><span data-stu-id="31fe6-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fe6-104">構文</span><span class="sxs-lookup"><span data-stu-id="31fe6-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="31fe6-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="31fe6-105">Members</span></span>  
  
|<span data-ttu-id="31fe6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="31fe6-106">Member</span></span>|<span data-ttu-id="31fe6-107">説明</span><span class="sxs-lookup"><span data-stu-id="31fe6-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="31fe6-108">内部使用のみ。</span><span class="sxs-lookup"><span data-stu-id="31fe6-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="31fe6-109">スレッドがオブジェクトのモニター ロックに関連付けられているクリティカル セクションを取得しようとしています。</span><span class="sxs-lookup"><span data-stu-id="31fe6-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="31fe6-110">通常のいずれかを呼び出すときに発生、<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>または<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="31fe6-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="31fe6-111">スレッドは、オブジェクトのモニター ロックに関連付けられているイベントで待機しています。</span><span class="sxs-lookup"><span data-stu-id="31fe6-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="31fe6-112">通常のいずれかを呼び出すときに発生、 <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="31fe6-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31fe6-113">コメント</span><span class="sxs-lookup"><span data-stu-id="31fe6-113">Remarks</span></span>  
 <span data-ttu-id="31fe6-114">ときに、`BLOCKING_MONITOR_CRITICAL_SECTION`または`BLOCKING_MONITOR_EVENT`でメンバーが使用される、 [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体、`pBlockingObject`構造体を指しますが入力されているオブジェクトを表す"ICorDebugValue"インターフェイスのメンバー.</span><span class="sxs-lookup"><span data-stu-id="31fe6-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="31fe6-115">実装するのには保証も、 [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="31fe6-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31fe6-116">要件</span><span class="sxs-lookup"><span data-stu-id="31fe6-116">Requirements</span></span>  
 <span data-ttu-id="31fe6-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="31fe6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31fe6-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31fe6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31fe6-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31fe6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31fe6-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31fe6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fe6-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="31fe6-121">See Also</span></span>  
 [<span data-ttu-id="31fe6-122">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="31fe6-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="31fe6-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="31fe6-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
