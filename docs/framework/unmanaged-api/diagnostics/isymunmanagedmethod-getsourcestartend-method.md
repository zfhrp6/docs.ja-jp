---
title: "ISymUnmanagedMethod::GetSourceStartEnd メソッド"
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
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2bdc044d4560b616bd6eeb8d642567add1f659f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="34d8e-102">ISymUnmanagedMethod::GetSourceStartEnd メソッド</span><span class="sxs-lookup"><span data-stu-id="34d8e-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="34d8e-103">このメソッドのソースの開始と終了のドキュメントの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="34d8e-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="34d8e-104">最初の配列の位置は、開始と 2 番目の配列の位置は、終了します。</span><span class="sxs-lookup"><span data-stu-id="34d8e-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d8e-105">構文</span><span class="sxs-lookup"><span data-stu-id="34d8e-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34d8e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34d8e-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="34d8e-107">[in]開始日と終了ソース ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="34d8e-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="34d8e-108">[in]ソース ドキュメントの開始日と、対応する行を終了します。</span><span class="sxs-lookup"><span data-stu-id="34d8e-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="34d8e-109">[in]ソース ドキュメントの開始と終了値で、対応する列。</span><span class="sxs-lookup"><span data-stu-id="34d8e-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="34d8e-110">[out]`true`位置が定義されている、それ以外の場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="34d8e-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34d8e-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="34d8e-111">Return Value</span></span>  
 <span data-ttu-id="34d8e-112">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="34d8e-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34d8e-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="34d8e-113">Requirements</span></span>  
 <span data-ttu-id="34d8e-114">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="34d8e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d8e-115">参照</span><span class="sxs-lookup"><span data-stu-id="34d8e-115">See Also</span></span>  
 [<span data-ttu-id="34d8e-116">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="34d8e-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
