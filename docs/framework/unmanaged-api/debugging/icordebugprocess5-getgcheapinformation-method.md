---
title: ICorDebugProcess5::GetGCHeapInformation メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8824ce004cac8bc2ad675c83dc6b5f167f183e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421048"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="546a7-102">ICorDebugProcess5::GetGCHeapInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="546a7-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="546a7-103">現在の列挙可能かどうかなど、ガベージ コレクション ヒープに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="546a7-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="546a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="546a7-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="546a7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="546a7-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="546a7-106">[out]ポインター、 [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)ガベージ コレクション ヒープに関する情報を提供する値。</span><span class="sxs-lookup"><span data-stu-id="546a7-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="546a7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="546a7-107">Remarks</span></span>  
 <span data-ttu-id="546a7-108">`ICorDebugProcess5::GetGCHeapInformation`ヒープを列挙する前にメソッドを呼び出す必要がありますまたは構造体のガベージ コレクションには、プロセスにことを確認するために個々 のヒープ領域は現在有効です。</span><span class="sxs-lookup"><span data-stu-id="546a7-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="546a7-109">コレクションが進行中はガベージ コレクション ヒープを処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="546a7-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="546a7-110">それ以外の場合、列挙体は、無効なガベージ コレクション構造をキャプチャする場合があります。</span><span class="sxs-lookup"><span data-stu-id="546a7-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="546a7-111">要件</span><span class="sxs-lookup"><span data-stu-id="546a7-111">Requirements</span></span>  
 <span data-ttu-id="546a7-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="546a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="546a7-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="546a7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="546a7-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="546a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="546a7-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="546a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546a7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="546a7-116">See Also</span></span>  
 [<span data-ttu-id="546a7-117">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="546a7-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="546a7-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="546a7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
