---
title: "ICorDebugCode::GetCode メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f906fddf8073a00d2a3741613aae537b8604af67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="b3040-102">ICorDebugCode::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="b3040-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="b3040-103">指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="b3040-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="b3040-104">.NET Framework version 2.0 では、このメソッドは廃止されました。</span><span class="sxs-lookup"><span data-stu-id="b3040-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b3040-105">使用して[icordebugcode 2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b3040-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3040-106">構文</span><span class="sxs-lookup"><span data-stu-id="b3040-106">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3040-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3040-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="b3040-108">[in]関数の最初のオフセット。</span><span class="sxs-lookup"><span data-stu-id="b3040-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b3040-109">[in]関数の最後のオフセット。</span><span class="sxs-lookup"><span data-stu-id="b3040-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="b3040-110">[in]サイズ、`buffer`にコードを返される配列。</span><span class="sxs-lookup"><span data-stu-id="b3040-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b3040-111">[out]コードが返される先の配列。</span><span class="sxs-lookup"><span data-stu-id="b3040-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="b3040-112">[out]返されるバイト数。</span><span class="sxs-lookup"><span data-stu-id="b3040-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3040-113">コメント</span><span class="sxs-lookup"><span data-stu-id="b3040-113">Remarks</span></span>  
 <span data-ttu-id="b3040-114">場合は、関数のコードは、複数のチャンクに分割して、ネイティブのオフセットの昇順で連結されます。</span><span class="sxs-lookup"><span data-stu-id="b3040-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="b3040-115">命令の境界はチェックされません。</span><span class="sxs-lookup"><span data-stu-id="b3040-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3040-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="b3040-116">Requirements</span></span>  
 <span data-ttu-id="b3040-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3040-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3040-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3040-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3040-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3040-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3040-120">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="b3040-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3040-121">参照</span><span class="sxs-lookup"><span data-stu-id="b3040-121">See Also</span></span>  
 [<span data-ttu-id="b3040-122">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="b3040-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
