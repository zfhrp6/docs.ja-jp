---
title: "ICorDebugDataTarget::ReadVirtual メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.ReadVirtual Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b9f0399c05155a9925624e5c9d6bcb6a52f024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="ac4b7-102">ICorDebugDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="ac4b7-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="ac4b7-103">指定したアドレスから始まる連続したメモリのブロックを取得し、指定されたバッファーで返します。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac4b7-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac4b7-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac4b7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac4b7-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ac4b7-106">[in]要求されたメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="ac4b7-107">[out]メモリを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="ac4b7-108">[in]ターゲット アドレスから取得するバイト数。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="ac4b7-109">[out]ターゲット アドレスから実際に読み取られたバイト数。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="ac4b7-110">これより少ない`bytesRequested`です。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac4b7-111">コメント</span><span class="sxs-lookup"><span data-stu-id="ac4b7-111">Remarks</span></span>  
 <span data-ttu-id="ac4b7-112">(指定した開始アドレス) にある最初のバイトを読み取ることができます、呼び出しは成功した場合 (読み取りをサポートする効率的な自己言及的な null で終わる文字列と同様に、長さのデータ構造の) を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac4b7-113">要件</span><span class="sxs-lookup"><span data-stu-id="ac4b7-113">Requirements</span></span>  
 <span data-ttu-id="ac4b7-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac4b7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac4b7-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac4b7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac4b7-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac4b7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac4b7-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac4b7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac4b7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac4b7-118">See Also</span></span>  
 [<span data-ttu-id="ac4b7-119">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac4b7-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="ac4b7-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac4b7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ac4b7-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ac4b7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
