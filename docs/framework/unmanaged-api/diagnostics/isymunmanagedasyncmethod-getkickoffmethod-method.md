---
title: "ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e017097183243c84a2ce40cc473067e05c80c3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="400f4-102">ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="400f4-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="400f4-103">参照してください[DefineKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="400f4-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="400f4-104">構文</span><span class="sxs-lookup"><span data-stu-id="400f4-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="400f4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="400f4-105">Parameters</span></span>  
  
|<span data-ttu-id="400f4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="400f4-106">Parameter</span></span>|<span data-ttu-id="400f4-107">説明</span><span class="sxs-lookup"><span data-stu-id="400f4-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="400f4-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="400f4-108">Return Value</span></span>  
 <span data-ttu-id="400f4-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="400f4-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="400f4-110">要件</span><span class="sxs-lookup"><span data-stu-id="400f4-110">Requirements</span></span>  
 <span data-ttu-id="400f4-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="400f4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400f4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="400f4-112">See Also</span></span>  
 [<span data-ttu-id="400f4-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="400f4-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
