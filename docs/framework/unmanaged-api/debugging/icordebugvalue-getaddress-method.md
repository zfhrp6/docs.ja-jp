---
title: "ICorDebugValue::GetAddress メソッド"
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
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8aa5a0c3740b6cf97d2a5d855343a36b90fd538
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="6991e-102">ICorDebugValue::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="6991e-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="6991e-103">デバッグ対象プロセスでは、この"ICorDebugValue"オブジェクトのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6991e-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6991e-104">構文</span><span class="sxs-lookup"><span data-stu-id="6991e-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6991e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6991e-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="6991e-106">[out]ポインター、`CORDB_ADDRESS`この値のオブジェクトのアドレスを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6991e-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6991e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="6991e-107">Remarks</span></span>  
 <span data-ttu-id="6991e-108">値が使用できない場合は 0 (ゼロ) が返されます。</span><span class="sxs-lookup"><span data-stu-id="6991e-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="6991e-109">これは、値は、少なくとも一部レジスタ場合に発生する可能性がありますか、ガベージ コレクター ハンドルに格納されている (`GCHandle`)。</span><span class="sxs-lookup"><span data-stu-id="6991e-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6991e-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="6991e-110">Requirements</span></span>  
 <span data-ttu-id="6991e-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6991e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6991e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6991e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6991e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6991e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6991e-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6991e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6991e-115">参照</span><span class="sxs-lookup"><span data-stu-id="6991e-115">See Also</span></span>  
 
