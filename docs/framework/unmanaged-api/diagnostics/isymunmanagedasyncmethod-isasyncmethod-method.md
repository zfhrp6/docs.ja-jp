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
ms.openlocfilehash: ce91552d7468579d9941c1da75c4d281999d66fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="707c7-102">ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="707c7-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="707c7-103">か、メソッドが非同期の情報を持つかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="707c7-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="707c7-104">このメソッドが戻る場合`FALSE`し、このインターフェイスで、他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="707c7-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="707c7-105">すべての戻り値は`E_UNEXPECTED`ここでします。</span><span class="sxs-lookup"><span data-stu-id="707c7-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="707c7-106">構文</span><span class="sxs-lookup"><span data-stu-id="707c7-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="707c7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="707c7-107">Parameters</span></span>  
  
|<span data-ttu-id="707c7-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="707c7-108">Parameter</span></span>|<span data-ttu-id="707c7-109">説明</span><span class="sxs-lookup"><span data-stu-id="707c7-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="707c7-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="707c7-110">Return Value</span></span>  
 <span data-ttu-id="707c7-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="707c7-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707c7-112">要件</span><span class="sxs-lookup"><span data-stu-id="707c7-112">Requirements</span></span>  
 <span data-ttu-id="707c7-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="707c7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707c7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="707c7-114">See Also</span></span>  
 [<span data-ttu-id="707c7-115">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="707c7-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
