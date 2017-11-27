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
ms.openlocfilehash: 3cff81968926f608de8d28d730a00e79dc8b1c3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="c5695-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="c5695-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="c5695-103">取得では、特定のドキュメントに行と、メソッドの末尾行を最大を最小を開始します。</span><span class="sxs-lookup"><span data-stu-id="c5695-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5695-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5695-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5695-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5695-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="c5695-106">[in]ドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c5695-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="c5695-107">[out]ポインター、`ULONG32`開始行を受け取る。</span><span class="sxs-lookup"><span data-stu-id="c5695-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="c5695-108">[out]ポインター、`ULONG32`の最終行を受け取る。</span><span class="sxs-lookup"><span data-stu-id="c5695-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5695-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c5695-109">Return Value</span></span>  
 <span data-ttu-id="c5695-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="c5695-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5695-111">要件</span><span class="sxs-lookup"><span data-stu-id="c5695-111">Requirements</span></span>  
 <span data-ttu-id="c5695-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c5695-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5695-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5695-113">See Also</span></span>  
 [<span data-ttu-id="c5695-114">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5695-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
