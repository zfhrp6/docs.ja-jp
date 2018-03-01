---
title: "ICorDebugRegisterSet::GetRegistersAvailable メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd7ff2b711d81ba1fe8fda9422587ec265dd88dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="7b667-102">ICorDebugRegisterSet::GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="7b667-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="7b667-103">これで登録することを示す取得がビット マスク[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)現在利用可能な。</span><span class="sxs-lookup"><span data-stu-id="7b667-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b667-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b667-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b667-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b667-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="7b667-106">[out]レジスタが現在使用可能なを示すビット マスクです。</span><span class="sxs-lookup"><span data-stu-id="7b667-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b667-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7b667-107">Remarks</span></span>  
 <span data-ttu-id="7b667-108">レジスタは、特定の状況では、その値を特定できない場合に使用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7b667-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="7b667-109">返されるマスクのビットを含む各レジスタ (1 << レジスタのインデックス)。</span><span class="sxs-lookup"><span data-stu-id="7b667-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="7b667-110">レジスタがある場合、ビット値は 1 または 0 が使用できない場合。</span><span class="sxs-lookup"><span data-stu-id="7b667-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b667-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="7b667-111">Requirements</span></span>  
 <span data-ttu-id="7b667-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b667-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b667-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b667-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b667-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b667-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b667-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b667-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b667-116">参照</span><span class="sxs-lookup"><span data-stu-id="7b667-116">See Also</span></span>  
 [<span data-ttu-id="7b667-117">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b667-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="7b667-118">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b667-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
