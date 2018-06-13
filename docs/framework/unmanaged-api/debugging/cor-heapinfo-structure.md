---
title: COR_HEAPINFO 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fb1ae367c30bb038bfe25961e91f02f172f486c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405757"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="ba5c7-102">COR_HEAPINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="ba5c7-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="ba5c7-103">列挙可能かどうかなど、ガベージ コレクション ヒープに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5c7-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba5c7-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="ba5c7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ba5c7-105">Members</span></span>  
  
|<span data-ttu-id="ba5c7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ba5c7-106">Member</span></span>|<span data-ttu-id="ba5c7-107">説明</span><span class="sxs-lookup"><span data-stu-id="ba5c7-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="ba5c7-108">`true` ガベージ コレクション構造は有効では、ヒープを列挙することができます。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="ba5c7-109">対象となるアーキテクチャ上のポインターのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="ba5c7-110">プロセスでヒープ論理ガベージ コレクションの数。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="ba5c7-111">`TRUE` 場合は、同時実行ガベージ コレクションの (バック グラウンド) が有効であります。それ以外の場合、`FALSE`です。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="ba5c7-112">メンバー、 [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)をガベージ コレクターがワークステーションまたはサーバーで実行されているかどうかを示す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba5c7-113">コメント</span><span class="sxs-lookup"><span data-stu-id="ba5c7-113">Remarks</span></span>  
 <span data-ttu-id="ba5c7-114">インスタンス、`COR_HEAPINFO`構造体が呼び出しによって返される、 [icordebugprocess 5::getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="ba5c7-115">ガベージ コレクション ヒープ上のオブジェクトを列挙するには、前にする必要があります常に確認する、`areGCStructuresValid`フィールドをヒープが列挙可能な状態であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="ba5c7-116">詳細については、次を参照してください。、 [icordebugprocess 5::getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba5c7-117">要件</span><span class="sxs-lookup"><span data-stu-id="ba5c7-117">Requirements</span></span>  
 <span data-ttu-id="ba5c7-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba5c7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba5c7-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba5c7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba5c7-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba5c7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba5c7-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba5c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5c7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba5c7-122">See Also</span></span>  
 [<span data-ttu-id="ba5c7-123">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="ba5c7-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ba5c7-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ba5c7-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
