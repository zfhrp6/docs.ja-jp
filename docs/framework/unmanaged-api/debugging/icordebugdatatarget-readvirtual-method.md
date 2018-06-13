---
title: ICorDebugDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d9e619e4176633074242521133d42f191f140ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412192"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="6051b-102">ICorDebugDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="6051b-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="6051b-103">指定したアドレスから始まる連続したメモリのブロックを取得し、指定されたバッファーで返します。</span><span class="sxs-lookup"><span data-stu-id="6051b-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6051b-104">構文</span><span class="sxs-lookup"><span data-stu-id="6051b-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6051b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6051b-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="6051b-106">[in]要求されたメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="6051b-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="6051b-107">[out]メモリを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="6051b-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="6051b-108">[in]ターゲット アドレスから取得するバイト数。</span><span class="sxs-lookup"><span data-stu-id="6051b-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="6051b-109">[out]ターゲット アドレスから実際に読み取られたバイト数。</span><span class="sxs-lookup"><span data-stu-id="6051b-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="6051b-110">これより少ない`bytesRequested`です。</span><span class="sxs-lookup"><span data-stu-id="6051b-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6051b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="6051b-111">Remarks</span></span>  
 <span data-ttu-id="6051b-112">(指定した開始アドレス) にある最初のバイトを読み取ることができます、呼び出しは成功した場合 (読み取りをサポートする効率的な自己言及的な null で終わる文字列と同様に、長さのデータ構造の) を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6051b-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6051b-113">要件</span><span class="sxs-lookup"><span data-stu-id="6051b-113">Requirements</span></span>  
 <span data-ttu-id="6051b-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6051b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6051b-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6051b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6051b-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6051b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6051b-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6051b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6051b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6051b-118">See Also</span></span>  
 [<span data-ttu-id="6051b-119">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6051b-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="6051b-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6051b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6051b-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="6051b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
