---
title: ISymUnmanagedMethod::GetNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53a47cf67edb36b06c92be83cb23c2e1dd1e75cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424431"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="a31b4-102">ISymUnmanagedMethod::GetNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="a31b4-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="a31b4-103">このメソッドが定義されている外側の名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="a31b4-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a31b4-104">構文</span><span class="sxs-lookup"><span data-stu-id="a31b4-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a31b4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a31b4-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a31b4-106">[out]設定されているポインターに返された[ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a31b4-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a31b4-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a31b4-107">Return Value</span></span>  
 <span data-ttu-id="a31b4-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="a31b4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a31b4-109">要件</span><span class="sxs-lookup"><span data-stu-id="a31b4-109">Requirements</span></span>  
 <span data-ttu-id="a31b4-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a31b4-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31b4-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a31b4-111">See Also</span></span>  
 [<span data-ttu-id="a31b4-112">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a31b4-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
