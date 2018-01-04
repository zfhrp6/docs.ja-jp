---
title: "ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6116ee89cb643cc0010ef2c8a463fa131777584e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="53291-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="53291-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="53291-103">取得では、特定のドキュメントに行と、メソッドの末尾行を最大を最小を開始します。</span><span class="sxs-lookup"><span data-stu-id="53291-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53291-104">構文</span><span class="sxs-lookup"><span data-stu-id="53291-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53291-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="53291-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="53291-106">[in]ドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="53291-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="53291-107">[out]ポインター、`ULONG32`開始行を受け取る。</span><span class="sxs-lookup"><span data-stu-id="53291-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="53291-108">[out]ポインター、`ULONG32`の最終行を受け取る。</span><span class="sxs-lookup"><span data-stu-id="53291-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53291-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="53291-109">Return Value</span></span>  
 <span data-ttu-id="53291-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="53291-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53291-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="53291-111">Requirements</span></span>  
 <span data-ttu-id="53291-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="53291-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53291-113">参照</span><span class="sxs-lookup"><span data-stu-id="53291-113">See Also</span></span>  
 [<span data-ttu-id="53291-114">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53291-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
