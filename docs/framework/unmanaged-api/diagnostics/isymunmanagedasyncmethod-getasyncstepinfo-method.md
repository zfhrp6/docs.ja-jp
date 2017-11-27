---
title: "ISymUnmanagedAsyncMethod::GetAsyncStepInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ad3fb6dba7740c3c541a446205b90d6f007635a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="e7b8b-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b8b-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="e7b8b-103">参照してください[DefineAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7b8b-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7b8b-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7b8b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7b8b-105">Parameters</span></span>  
  
|<span data-ttu-id="e7b8b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7b8b-106">Parameter</span></span>|<span data-ttu-id="e7b8b-107">説明</span><span class="sxs-lookup"><span data-stu-id="e7b8b-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="e7b8b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e7b8b-108">Return Value</span></span>  
 <span data-ttu-id="e7b8b-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="e7b8b-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b8b-110">要件</span><span class="sxs-lookup"><span data-stu-id="e7b8b-110">Requirements</span></span>  
 <span data-ttu-id="e7b8b-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e7b8b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b8b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7b8b-112">See Also</span></span>  
 [<span data-ttu-id="e7b8b-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7b8b-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
