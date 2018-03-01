---
title: "ICLRDataTarget::WriteVirtual メソッド"
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
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77c47ff90ff9d225eaa8e1f26a70463ea7d5dd5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="d1ac8-102">ICLRDataTarget::WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="d1ac8-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="d1ac8-103">指定された仮想メモリ アドレスに指定されたバッファーからデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d1ac8-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ac8-104">構文</span><span class="sxs-lookup"><span data-stu-id="d1ac8-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1ac8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1ac8-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d1ac8-106">[in]仮想メモリ アドレスを格納する CLRDATA_ADDRESS です。</span><span class="sxs-lookup"><span data-stu-id="d1ac8-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="d1ac8-107">[in]書き込むデータを格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d1ac8-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="d1ac8-108">[in]書き込むバイト数。</span><span class="sxs-lookup"><span data-stu-id="d1ac8-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="d1ac8-109">[out]実際に書き込まれたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d1ac8-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1ac8-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="d1ac8-110">Requirements</span></span>  
 <span data-ttu-id="d1ac8-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1ac8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1ac8-112">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d1ac8-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d1ac8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1ac8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1ac8-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1ac8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ac8-115">参照</span><span class="sxs-lookup"><span data-stu-id="d1ac8-115">See Also</span></span>  
 [<span data-ttu-id="d1ac8-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1ac8-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
