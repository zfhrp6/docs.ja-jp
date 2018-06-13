---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2f055dc19bf7f40036283102d8cc4549555b992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424769"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="0c0c2-102">ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="0c0c2-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="0c0c2-103">参照してください[DefineKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c0c2-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="0c0c2-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c0c2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c0c2-105">Parameters</span></span>  
  
|<span data-ttu-id="0c0c2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c0c2-106">Parameter</span></span>|<span data-ttu-id="0c0c2-107">説明</span><span class="sxs-lookup"><span data-stu-id="0c0c2-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="0c0c2-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0c0c2-108">Return Value</span></span>  
 <span data-ttu-id="0c0c2-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="0c0c2-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c0c2-110">要件</span><span class="sxs-lookup"><span data-stu-id="0c0c2-110">Requirements</span></span>  
 <span data-ttu-id="0c0c2-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0c0c2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0c2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c0c2-112">See Also</span></span>  
 [<span data-ttu-id="0c0c2-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c0c2-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
