---
title: "ISymUnmanagedMethod::GetRanges メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRanges
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e17b411e39e522006092d79380566484f8fab67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="58b08-102">ISymUnmanagedMethod::GetRanges メソッド</span><span class="sxs-lookup"><span data-stu-id="58b08-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="58b08-103">指定されたドキュメント内の位置には、Microsoft intermediate language (MSIL をこのメソッド内に含まれる位置) の範囲に先頭と末尾オフセットのペアの対応する配列を返します。</span><span class="sxs-lookup"><span data-stu-id="58b08-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="58b08-104">配列整数の配列は、[開始、終了、開始、終了] の形式があります。</span><span class="sxs-lookup"><span data-stu-id="58b08-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="58b08-105">範囲のペアの数は、2 で割った値配列の長さです。</span><span class="sxs-lookup"><span data-stu-id="58b08-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58b08-106">構文</span><span class="sxs-lookup"><span data-stu-id="58b08-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58b08-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58b08-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="58b08-108">[in]オフセットを要求する対象のドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="58b08-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="58b08-109">[in]範囲に対応するドキュメント行。</span><span class="sxs-lookup"><span data-stu-id="58b08-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="58b08-110">[in]範囲に対応するドキュメント列。</span><span class="sxs-lookup"><span data-stu-id="58b08-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="58b08-111">[in] `ranges` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="58b08-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="58b08-112">[out]ポインター、`ULONG32`範囲の格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="58b08-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="58b08-113">[out]範囲を受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58b08-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58b08-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="58b08-114">Return Value</span></span>  
 <span data-ttu-id="58b08-115">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="58b08-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b08-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="58b08-116">Requirements</span></span>  
 <span data-ttu-id="58b08-117">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="58b08-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b08-118">参照</span><span class="sxs-lookup"><span data-stu-id="58b08-118">See Also</span></span>  
 [<span data-ttu-id="58b08-119">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58b08-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
