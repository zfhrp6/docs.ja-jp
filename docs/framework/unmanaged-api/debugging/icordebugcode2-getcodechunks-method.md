---
title: "ICorDebugCode2::GetCodeChunks メソッド"
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
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b90913f05cc2e0a3e98a5890f76a41eb2eafc6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="4b3f6-102">ICorDebugCode2::GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="4b3f6-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="4b3f6-103">このコード オブジェクトを構成しているコード チャンクを取得します。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="4b3f6-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b3f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4b3f6-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="4b3f6-106">[in]サイズ、`chunks`配列。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="4b3f6-107">[out]返されるチャンクの数、`chunks`配列。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="4b3f6-108">[out]コードの単一のチャンクを表す"CodeChunkInfo"構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="4b3f6-109">場合の値`cbufSize`0 は、このパラメーターを null にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b3f6-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4b3f6-110">Remarks</span></span>  
 <span data-ttu-id="4b3f6-111">コード チャンク重複、および、それらが連結されたによって順序に従いますが[icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="4b3f6-112">.NET Framework version 2.0 では、Microsoft intermediate language (MSIL) コード オブジェクトには、1 つのコード チャンクを構成します。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b3f6-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="4b3f6-113">Requirements</span></span>  
 <span data-ttu-id="4b3f6-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4b3f6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b3f6-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b3f6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b3f6-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b3f6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b3f6-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b3f6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3f6-118">参照</span><span class="sxs-lookup"><span data-stu-id="4b3f6-118">See Also</span></span>  
 
