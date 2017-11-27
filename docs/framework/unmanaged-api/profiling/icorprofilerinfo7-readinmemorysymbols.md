---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type: COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ada9f629c3a3c3d8b7c32ebc180c4788b6f6d3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="4f715-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="4f715-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="4f715-103">[[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="4f715-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="4f715-104">メモリ内のシンボルのストリームからバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="4f715-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f715-105">構文</span><span class="sxs-lookup"><span data-stu-id="4f715-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f715-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f715-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4f715-107">[in]メモリ内ストリームを含むモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="4f715-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="4f715-108">[in]バイトの読み取りを開始位置をメモリ内ストリーム内のオフセット。</span><span class="sxs-lookup"><span data-stu-id="4f715-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="4f715-109">[out]データのコピー先となるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4f715-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="4f715-110">バッファーが必要`countSymbolBytes`使用可能な領域。</span><span class="sxs-lookup"><span data-stu-id="4f715-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="4f715-111">[in]コピーするバイト数。</span><span class="sxs-lookup"><span data-stu-id="4f715-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="4f715-112">[out]メソッドが戻るときに、実際に読み取ったバイト数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f715-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f715-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="4f715-113">Return Value</span></span>  
 <span data-ttu-id="4f715-114">`S_OK`、読み取られたバイト数、0 でない場合。</span><span class="sxs-lookup"><span data-stu-id="4f715-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="4f715-115">`CORPROF_E_MODULE_IS_DYNAMIC`を使用して、モジュールが作成された場合<xref:System.Reflection.Emit>です。</span><span class="sxs-lookup"><span data-stu-id="4f715-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f715-116">コメント</span><span class="sxs-lookup"><span data-stu-id="4f715-116">Remarks</span></span>  
 <span data-ttu-id="4f715-117">`ReadInMemorySymbols`メソッドの読み取りを試みます`countSymbolBytes`オフセットで始まるデータ`symbolsReadOffset`メモリ内のストリーム内です。</span><span class="sxs-lookup"><span data-stu-id="4f715-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="4f715-118">データがコピー`pSymbolBytes`が予期されて`countSymbolBytes`使用可能な領域。</span><span class="sxs-lookup"><span data-stu-id="4f715-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="4f715-119">`pCountSymbolsBytesRead`実際の少ない可能性がありますが、読み取られたバイト数を含むより`countSymbolBytes`ストリームの末尾に達した場合。</span><span class="sxs-lookup"><span data-stu-id="4f715-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f715-120">現在の実装は、Reflection.Emit をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4f715-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="4f715-121">メソッドを返しますのかどうか、モジュールは、Reflection.Emit を使用して作成された、`CORPROF_E_MODULE_IS_DYNAMIC`です。</span><span class="sxs-lookup"><span data-stu-id="4f715-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f715-122">要件</span><span class="sxs-lookup"><span data-stu-id="4f715-122">Requirements</span></span>  
 <span data-ttu-id="4f715-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f715-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f715-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f715-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f715-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f715-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f715-126">**.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f715-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f715-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f715-127">See Also</span></span>  
 [<span data-ttu-id="4f715-128">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f715-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
