---
title: "ICorDebugRegisterSet::GetRegistersAvailable メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa4dd904b07aa2c9157e61e6968e96ef797ad3f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="b4c1b-102">ICorDebugRegisterSet::GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="b4c1b-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="b4c1b-103">これで登録することを示す取得がビット マスク[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)現在利用可能な。</span><span class="sxs-lookup"><span data-stu-id="b4c1b-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c1b-104">構文</span><span class="sxs-lookup"><span data-stu-id="b4c1b-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4c1b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b4c1b-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="b4c1b-106">[out]レジスタが現在使用可能なを示すビット マスクです。</span><span class="sxs-lookup"><span data-stu-id="b4c1b-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4c1b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="b4c1b-107">Remarks</span></span>  
 <span data-ttu-id="b4c1b-108">レジスタは、特定の状況では、その値を特定できない場合に使用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b4c1b-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="b4c1b-109">返されるマスクのビットを含む各レジスタ (1 << レジスタのインデックス)。</span><span class="sxs-lookup"><span data-stu-id="b4c1b-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="b4c1b-110">レジスタがある場合、ビット値は 1 または 0 が使用できない場合。</span><span class="sxs-lookup"><span data-stu-id="b4c1b-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4c1b-111">要件</span><span class="sxs-lookup"><span data-stu-id="b4c1b-111">Requirements</span></span>  
 <span data-ttu-id="b4c1b-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4c1b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4c1b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4c1b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4c1b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4c1b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4c1b-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4c1b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c1b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4c1b-116">See Also</span></span>  
 [<span data-ttu-id="b4c1b-117">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4c1b-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="b4c1b-118">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4c1b-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
