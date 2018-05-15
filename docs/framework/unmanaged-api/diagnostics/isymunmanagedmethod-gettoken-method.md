---
title: ISymUnmanagedMethod::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89ae648e38b6349bfad0a37724a9bdc1ae05e365
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="8b1ad-102">ISymUnmanagedMethod::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="8b1ad-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="8b1ad-103">このメソッドのメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="8b1ad-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b1ad-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b1ad-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b1ad-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="8b1ad-106">[out]ポインター、`mdMethodDef`メタデータの格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="8b1ad-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b1ad-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8b1ad-107">Return Value</span></span>  
 <span data-ttu-id="8b1ad-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8b1ad-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b1ad-109">要件</span><span class="sxs-lookup"><span data-stu-id="8b1ad-109">Requirements</span></span>  
 <span data-ttu-id="8b1ad-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8b1ad-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b1ad-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b1ad-111">See Also</span></span>  
 [<span data-ttu-id="8b1ad-112">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b1ad-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
