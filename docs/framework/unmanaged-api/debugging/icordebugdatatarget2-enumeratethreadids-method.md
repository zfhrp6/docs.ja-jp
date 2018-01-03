---
title: "ICorDebugDataTarget2::EnumerateThreadIDs メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9030f7f8453de98f535cf8212e55c7daee94e8e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="aff54-102">ICorDebugDataTarget2::EnumerateThreadIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="aff54-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="aff54-103">アクティブなスレッド ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="aff54-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff54-104">構文</span><span class="sxs-lookup"><span data-stu-id="aff54-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aff54-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aff54-105">Parameters</span></span>  
 <span data-ttu-id="aff54-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="aff54-106">cThreadIDs</span></span>  
 <span data-ttu-id="aff54-107">[入力] ID を返すことのできるスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="aff54-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="aff54-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="aff54-108">pcThreadIds</span></span>  
 <span data-ttu-id="aff54-109">[出力] `ULONG32` 配列に書き込まれたスレッド ID の実際の数を示す `pThreadIds` へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aff54-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="aff54-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="aff54-110">pThreadIDs</span></span>  
 <span data-ttu-id="aff54-111">スレッド識別子の配列。</span><span class="sxs-lookup"><span data-stu-id="aff54-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aff54-112">コメント</span><span class="sxs-lookup"><span data-stu-id="aff54-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff54-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aff54-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff54-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="aff54-114">Requirements</span></span>  
 <span data-ttu-id="aff54-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md).**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aff54-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aff54-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aff54-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aff54-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff54-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff54-118">参照</span><span class="sxs-lookup"><span data-stu-id="aff54-118">See Also</span></span>  
 [<span data-ttu-id="aff54-119">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aff54-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="aff54-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aff54-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
