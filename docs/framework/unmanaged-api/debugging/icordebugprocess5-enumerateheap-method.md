---
title: ICorDebugProcess5::EnumerateHeap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 412ade32daaed4802215c628ab94b535fc542b93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423346"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="a02dd-102">ICorDebugProcess5::EnumerateHeap メソッド</span><span class="sxs-lookup"><span data-stu-id="a02dd-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="a02dd-103">マネージ ヒープのオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a02dd-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02dd-104">構文</span><span class="sxs-lookup"><span data-stu-id="a02dd-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a02dd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a02dd-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="a02dd-106">[out]アドレスへのポインター、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)インターフェイスであるオブジェクトをマネージ ヒープ上に存在するオブジェクトの列挙子。</span><span class="sxs-lookup"><span data-stu-id="a02dd-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a02dd-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a02dd-107">Remarks</span></span>  
 <span data-ttu-id="a02dd-108">呼び出しの前に、`ICorDebugProcess5::EnumerateHeap`メソッドを呼び出す必要があります、 [icordebugprocess 5::getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)メソッドの値を確認し、 `areGCStructuresValid` 、返されたフィールド[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)現在の状態で、ガベージ コレクション ヒープが列挙可能なことを確認するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a02dd-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="a02dd-109">さらに、`ICorDebugProcess5::EnumerateHeap`返します`E_FAIL`マネージ ヒープが割り当てられているが早すぎるのでメモリの前に、プロセスの有効期間にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="a02dd-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="a02dd-110">[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)インターフェイス オブジェクトは、標準的な列挙子を列挙することができます ICorDebugEnum インターフェイスから派生した[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a02dd-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="a02dd-111">このメソッドは追加、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)のコレクション オブジェクト[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)すべてのオブジェクトに関する情報を提供するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="a02dd-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="a02dd-112">コレクションを含めることがありますも[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)でルートがないオブジェクトに関する情報を提供するインスタンスは、オブジェクトが、ガベージ コレクターによって収集されていません。</span><span class="sxs-lookup"><span data-stu-id="a02dd-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a02dd-113">要件</span><span class="sxs-lookup"><span data-stu-id="a02dd-113">Requirements</span></span>  
 <span data-ttu-id="a02dd-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a02dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02dd-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a02dd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a02dd-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a02dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a02dd-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02dd-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a02dd-118">See Also</span></span>  
 [<span data-ttu-id="a02dd-119">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a02dd-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="a02dd-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a02dd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
