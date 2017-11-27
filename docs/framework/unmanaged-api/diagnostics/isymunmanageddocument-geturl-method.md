---
title: "ISymUnmanagedDocument::GetURL メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetURL
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 591383fee2f9b22a00956193555c719e72d722bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="5a385-102">ISymUnmanagedDocument::GetURL メソッド</span><span class="sxs-lookup"><span data-stu-id="5a385-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="5a385-103">このドキュメントの uniform resource locator (URL) を返します。</span><span class="sxs-lookup"><span data-stu-id="5a385-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a385-104">構文</span><span class="sxs-lookup"><span data-stu-id="5a385-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a385-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a385-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="5a385-106">[入力] `szURL` バッファーのサイズ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="5a385-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="5a385-107">[out]終端の null を含む URL のサイズを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5a385-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="5a385-108">[out]URL を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="5a385-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a385-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5a385-109">Return Value</span></span>  
 <span data-ttu-id="5a385-110">メソッドが成功した場合は S_OK、それ以外の場合、エラー コード。</span><span class="sxs-lookup"><span data-stu-id="5a385-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a385-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a385-111">See Also</span></span>  
 [<span data-ttu-id="5a385-112">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a385-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
