---
title: "ICorDebugRegisterSet2::GetRegistersAvailable メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f91b30b2ab50fc74049365d5c290bbaae1e20b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="2d656-102">ICorDebugRegisterSet2::GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="2d656-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="2d656-103">使用可能なレジスタのビットマップを提供するバイト配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d656-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d656-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d656-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d656-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2d656-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="2d656-106">[in] `availableRegChunks` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="2d656-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="2d656-107">[out]バイトの配列を各ビットは、レジスタに対応します。</span><span class="sxs-lookup"><span data-stu-id="2d656-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="2d656-108">レジスタがある場合は、レジスタの対応するビットが設定されます。</span><span class="sxs-lookup"><span data-stu-id="2d656-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d656-109">コメント</span><span class="sxs-lookup"><span data-stu-id="2d656-109">Remarks</span></span>  
 <span data-ttu-id="2d656-110">CorDebugRegister 列挙型の値は、異なるマイクロプロセッサのレジスタを指定します。</span><span class="sxs-lookup"><span data-stu-id="2d656-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="2d656-111">各値の上位 5 ビットは、インデックスに、`availableRegChunks`バイトの配列。</span><span class="sxs-lookup"><span data-stu-id="2d656-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="2d656-112">各値の下位 3 ビットは、インデックス付きのバイト内のビット位置を特定します。</span><span class="sxs-lookup"><span data-stu-id="2d656-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="2d656-113">指定された、`CorDebugRegister`マスク内の登録の位置、特定のレジスタを指定する値は次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="2d656-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1.  <span data-ttu-id="2d656-114">正確なバイトのアクセスに必要なインデックスの抽出、`availableRegChunks`配列。</span><span class="sxs-lookup"><span data-stu-id="2d656-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="2d656-115">`CorDebugRegister`値 >> 3</span><span class="sxs-lookup"><span data-stu-id="2d656-115">`CorDebugRegister` value >> 3</span></span>  
  
2.  <span data-ttu-id="2d656-116">ビット 0 が最下位ビットをここでは、インデックス付きのバイト内のビット位置を抽出します。</span><span class="sxs-lookup"><span data-stu-id="2d656-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="2d656-117">`CorDebugRegister`値 & 7</span><span class="sxs-lookup"><span data-stu-id="2d656-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d656-118">要件</span><span class="sxs-lookup"><span data-stu-id="2d656-118">Requirements</span></span>  
 <span data-ttu-id="2d656-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d656-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d656-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d656-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d656-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d656-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d656-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d656-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d656-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d656-123">See Also</span></span>  
 [<span data-ttu-id="2d656-124">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d656-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="2d656-125">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d656-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
