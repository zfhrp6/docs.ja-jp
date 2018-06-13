---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 775f5a2129a635c79a48d5218d5eb91ee83ee779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427884"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="8abaf-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT メソッド</span><span class="sxs-lookup"><span data-stu-id="8abaf-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="8abaf-103">HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="8abaf-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8abaf-104">構文</span><span class="sxs-lookup"><span data-stu-id="8abaf-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8abaf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8abaf-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="8abaf-106">[out]HRESULT へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8abaf-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8abaf-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8abaf-107">Return Value</span></span>  
 <span data-ttu-id="8abaf-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8abaf-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8abaf-109">要件</span><span class="sxs-lookup"><span data-stu-id="8abaf-109">Requirements</span></span>  
 <span data-ttu-id="8abaf-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8abaf-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8abaf-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8abaf-111">See Also</span></span>  
 [<span data-ttu-id="8abaf-112">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8abaf-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
