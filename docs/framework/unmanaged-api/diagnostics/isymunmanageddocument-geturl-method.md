---
title: ISymUnmanagedDocument::GetURL メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a447de2bb01e7bbf838ef5443e3ae7951bf8226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="d09ec-102">ISymUnmanagedDocument::GetURL メソッド</span><span class="sxs-lookup"><span data-stu-id="d09ec-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="d09ec-103">このドキュメントの uniform resource locator (URL) を返します。</span><span class="sxs-lookup"><span data-stu-id="d09ec-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="d09ec-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d09ec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d09ec-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="d09ec-106">[入力] `szURL` バッファーのサイズ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="d09ec-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="d09ec-107">[out]終端の null を含む URL のサイズを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d09ec-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="d09ec-108">[out]URL を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="d09ec-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d09ec-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d09ec-109">Return Value</span></span>  
 <span data-ttu-id="d09ec-110">メソッドが成功した場合は S_OK、それ以外の場合、エラー コード。</span><span class="sxs-lookup"><span data-stu-id="d09ec-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09ec-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d09ec-111">See Also</span></span>  
 [<span data-ttu-id="d09ec-112">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d09ec-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
