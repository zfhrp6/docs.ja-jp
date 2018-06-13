---
title: ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset メソッド
ms.date: 03/30/2017
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 527e686eb0c354c3a1ebba36772e30211e995ab2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425354"
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="bfe53-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="bfe53-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="bfe53-103">参照してください[DefineCatchHandlerILOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="bfe53-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfe53-104">構文</span><span class="sxs-lookup"><span data-stu-id="bfe53-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfe53-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bfe53-105">Parameters</span></span>  
  
|<span data-ttu-id="bfe53-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bfe53-106">Parameter</span></span>|<span data-ttu-id="bfe53-107">説明</span><span class="sxs-lookup"><span data-stu-id="bfe53-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="bfe53-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bfe53-108">Return Value</span></span>  
 <span data-ttu-id="bfe53-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="bfe53-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfe53-110">要件</span><span class="sxs-lookup"><span data-stu-id="bfe53-110">Requirements</span></span>  
 <span data-ttu-id="bfe53-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bfe53-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe53-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfe53-112">See Also</span></span>  
 [<span data-ttu-id="bfe53-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfe53-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
