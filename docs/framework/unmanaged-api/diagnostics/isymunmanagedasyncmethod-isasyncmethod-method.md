---
title: "ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 560690e95e7aa0aef37e3a708183641bd70ee97d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="c9d1f-102">ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="c9d1f-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="c9d1f-103">か、メソッドが非同期の情報を持つかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="c9d1f-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="c9d1f-104">このメソッドが戻る場合`FALSE`し、このインターフェイスで、他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c9d1f-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="c9d1f-105">すべての戻り値は`E_UNEXPECTED`ここでします。</span><span class="sxs-lookup"><span data-stu-id="c9d1f-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d1f-106">構文</span><span class="sxs-lookup"><span data-stu-id="c9d1f-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9d1f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9d1f-107">Parameters</span></span>  
  
|<span data-ttu-id="c9d1f-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9d1f-108">Parameter</span></span>|<span data-ttu-id="c9d1f-109">説明</span><span class="sxs-lookup"><span data-stu-id="c9d1f-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="c9d1f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c9d1f-110">Return Value</span></span>  
 <span data-ttu-id="c9d1f-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="c9d1f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9d1f-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="c9d1f-112">Requirements</span></span>  
 <span data-ttu-id="c9d1f-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9d1f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d1f-114">参照</span><span class="sxs-lookup"><span data-stu-id="c9d1f-114">See Also</span></span>  
 [<span data-ttu-id="c9d1f-115">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9d1f-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
