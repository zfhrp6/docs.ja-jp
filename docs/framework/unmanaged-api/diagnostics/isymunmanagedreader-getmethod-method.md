---
title: ISymUnmanagedReader::GetMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9f1056d8d5ec4486e748d3b079507943a8a72ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="18bcc-102">ISymUnmanagedReader::GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="18bcc-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="18bcc-103">メソッドのトークンを指定、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="18bcc-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18bcc-104">構文</span><span class="sxs-lookup"><span data-stu-id="18bcc-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18bcc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18bcc-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="18bcc-106">[in]メソッド トークンです。</span><span class="sxs-lookup"><span data-stu-id="18bcc-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="18bcc-107">[out]返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18bcc-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18bcc-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="18bcc-108">Return Value</span></span>  
 <span data-ttu-id="18bcc-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="18bcc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18bcc-110">要件</span><span class="sxs-lookup"><span data-stu-id="18bcc-110">Requirements</span></span>  
 <span data-ttu-id="18bcc-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18bcc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18bcc-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="18bcc-112">See Also</span></span>  
 [<span data-ttu-id="18bcc-113">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18bcc-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
