---
title: ISymUnmanagedDocument::FindClosestLine メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f31dad53f42fdd8f7ac3a0cb995b507ecc3590d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="a63c0-102">ISymUnmanagedDocument::FindClosestLine メソッド</span><span class="sxs-lookup"><span data-stu-id="a63c0-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="a63c0-103">行を指定した場合も、シーケンス ポイントができない可能性があります、このドキュメントでは、シーケンス ポイントである最も近い行を返します。</span><span class="sxs-lookup"><span data-stu-id="a63c0-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63c0-104">構文</span><span class="sxs-lookup"><span data-stu-id="a63c0-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a63c0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a63c0-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="a63c0-106">[in]このドキュメント内の行。</span><span class="sxs-lookup"><span data-stu-id="a63c0-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a63c0-107">[out]行を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a63c0-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a63c0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a63c0-108">Return Value</span></span>  
 <span data-ttu-id="a63c0-109">メソッドが成功した場合は S_OK、それ以外の場合、エラー コード。</span><span class="sxs-lookup"><span data-stu-id="a63c0-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63c0-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a63c0-110">See Also</span></span>  
 [<span data-ttu-id="a63c0-111">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a63c0-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
