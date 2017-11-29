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
ms.openlocfilehash: c20b7dd1bcbc27edb9be11419b7919250301d488
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="b8d9d-102">ICorDebugDataTarget2::EnumerateThreadIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="b8d9d-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="b8d9d-103">アクティブなスレッド ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d9d-104">構文</span><span class="sxs-lookup"><span data-stu-id="b8d9d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8d9d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8d9d-105">Parameters</span></span>  
 <span data-ttu-id="b8d9d-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="b8d9d-106">cThreadIDs</span></span>  
 <span data-ttu-id="b8d9d-107">[入力] ID を返すことのできるスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="b8d9d-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="b8d9d-108">pcThreadIds</span></span>  
 <span data-ttu-id="b8d9d-109">[出力] `ULONG32` 配列に書き込まれたスレッド ID の実際の数を示す `pThreadIds` へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="b8d9d-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="b8d9d-110">pThreadIDs</span></span>  
 <span data-ttu-id="b8d9d-111">スレッド識別子の配列。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8d9d-112">コメント</span><span class="sxs-lookup"><span data-stu-id="b8d9d-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d9d-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8d9d-114">要件</span><span class="sxs-lookup"><span data-stu-id="b8d9d-114">Requirements</span></span>  
 <span data-ttu-id="b8d9d-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md).**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8d9d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8d9d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8d9d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8d9d-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d9d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d9d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8d9d-118">See Also</span></span>  
 [<span data-ttu-id="b8d9d-119">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8d9d-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="b8d9d-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8d9d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
