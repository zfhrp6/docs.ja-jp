---
title: "ICorDebugRegisterSet::GetRegisters メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7edae3d3be1bcfb80b7a1e432fd5f25e119f078f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="681b1-102">ICorDebugRegisterSet::GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="681b1-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="681b1-103">(現在のコードを実行しているコンピューター) 上の各レジスタの値を取得ビット マスクで指定されています。</span><span class="sxs-lookup"><span data-stu-id="681b1-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="681b1-104">構文</span><span class="sxs-lookup"><span data-stu-id="681b1-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="681b1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="681b1-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="681b1-106">[in]値が取得するにはどのレジスタを指定するビット マスクです。</span><span class="sxs-lookup"><span data-stu-id="681b1-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="681b1-107">各ビットは、レジスタに対応します。</span><span class="sxs-lookup"><span data-stu-id="681b1-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="681b1-108">ビットは 1 つに設定されている場合は、レジスタの値が取得されます。それ以外の場合、レジスタの値は取得されません。</span><span class="sxs-lookup"><span data-stu-id="681b1-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="681b1-109">[in]取得するレジスタの値の数。</span><span class="sxs-lookup"><span data-stu-id="681b1-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="681b1-110">[out]配列`CORDB_REGISTER`レジスタの値を受け取る各のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="681b1-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="681b1-111">コメント</span><span class="sxs-lookup"><span data-stu-id="681b1-111">Remarks</span></span>  
 <span data-ttu-id="681b1-112">配列のサイズをビット マスクのいずれかに設定されたビットの数と同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="681b1-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="681b1-113">`regCount`パラメーターは、レジスタの値を受け取るバッファー内の要素の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="681b1-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="681b1-114">場合、`regCount`マスクによって示されるレジスタの数の値が小さすぎる、セットから大きい番号のレジスタは切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="681b1-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="681b1-115">場合、`regCount`値が大きすぎるため、未使用`regBuffer`要素は変更できません。</span><span class="sxs-lookup"><span data-stu-id="681b1-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="681b1-116">使用可能なレジスタを指定するビット マスク場合`GetRegisters`そのレジスタの中間の値を返します。</span><span class="sxs-lookup"><span data-stu-id="681b1-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="681b1-117">要件</span><span class="sxs-lookup"><span data-stu-id="681b1-117">Requirements</span></span>  
 <span data-ttu-id="681b1-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="681b1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="681b1-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="681b1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="681b1-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="681b1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="681b1-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="681b1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681b1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="681b1-122">See Also</span></span>  
 [<span data-ttu-id="681b1-123">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="681b1-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="681b1-124">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="681b1-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
