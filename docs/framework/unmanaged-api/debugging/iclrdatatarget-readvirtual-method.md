---
title: "ICLRDataTarget::ReadVirtual メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.ReadVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84d1a8c37bf9d065317688f42bd554108fd92974
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="cbed8-102">ICLRDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="cbed8-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="cbed8-103">指定されたバッファーに指定された仮想メモリ アドレスからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="cbed8-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbed8-104">構文</span><span class="sxs-lookup"><span data-stu-id="cbed8-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbed8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cbed8-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cbed8-106">[in]仮想メモリ アドレスを格納する CLRDATA_ADDRESS です。</span><span class="sxs-lookup"><span data-stu-id="cbed8-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="cbed8-107">[out]データを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cbed8-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="cbed8-108">[in]バッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="cbed8-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="cbed8-109">[out]返されるバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cbed8-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbed8-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="cbed8-110">Requirements</span></span>  
 <span data-ttu-id="cbed8-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cbed8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbed8-112">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cbed8-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cbed8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbed8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbed8-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbed8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbed8-115">参照</span><span class="sxs-lookup"><span data-stu-id="cbed8-115">See Also</span></span>  
 [<span data-ttu-id="cbed8-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cbed8-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
