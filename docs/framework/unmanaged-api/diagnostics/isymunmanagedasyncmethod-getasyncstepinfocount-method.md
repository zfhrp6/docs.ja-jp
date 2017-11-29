---
title: "ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 32a4e084-09b2-4946-a4a7-19a1fed9f7cc
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b2431662caa41c67746da7e21591c743896c161
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfocount-method"></a><span data-ttu-id="3f542-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="3f542-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Method</span></span>
<span data-ttu-id="3f542-103">参照してください[DefineAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="3f542-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f542-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f542-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfoCount(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f542-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f542-105">Parameters</span></span>  
  
|<span data-ttu-id="3f542-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f542-106">Parameter</span></span>|<span data-ttu-id="3f542-107">説明</span><span class="sxs-lookup"><span data-stu-id="3f542-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="3f542-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3f542-108">Return Value</span></span>  
 <span data-ttu-id="3f542-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="3f542-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f542-110">要件</span><span class="sxs-lookup"><span data-stu-id="3f542-110">Requirements</span></span>  
 <span data-ttu-id="3f542-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3f542-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f542-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f542-112">See Also</span></span>  
 [<span data-ttu-id="3f542-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f542-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
