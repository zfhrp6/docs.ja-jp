---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 691a46e20339b659b5df3136d4dca6c03a69d3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="6a0a3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="6a0a3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="6a0a3-103">非同期操作を開始する開始メソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="6a0a3-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a0a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="6a0a3-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a0a3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a0a3-105">Parameters</span></span>  
  
|<span data-ttu-id="6a0a3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a0a3-106">Parameter</span></span>|<span data-ttu-id="6a0a3-107">説明</span><span class="sxs-lookup"><span data-stu-id="6a0a3-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="6a0a3-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="6a0a3-108">Return Value</span></span>  
 <span data-ttu-id="6a0a3-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="6a0a3-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a0a3-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="6a0a3-110">Requirements</span></span>  
 <span data-ttu-id="6a0a3-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a0a3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0a3-112">参照</span><span class="sxs-lookup"><span data-stu-id="6a0a3-112">See Also</span></span>  
 [<span data-ttu-id="6a0a3-113">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a0a3-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
