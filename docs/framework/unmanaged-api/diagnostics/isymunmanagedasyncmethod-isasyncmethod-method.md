---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f5bf8252986ffa90ea5380d5342595cb91e5419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424942"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="d0a2f-102">ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="d0a2f-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="d0a2f-103">か、メソッドが非同期の情報を持つかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="d0a2f-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="d0a2f-104">このメソッドが戻る場合`FALSE`し、このインターフェイスで、他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="d0a2f-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="d0a2f-105">すべての戻り値は`E_UNEXPECTED`ここでします。</span><span class="sxs-lookup"><span data-stu-id="d0a2f-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a2f-106">構文</span><span class="sxs-lookup"><span data-stu-id="d0a2f-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0a2f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0a2f-107">Parameters</span></span>  
  
|<span data-ttu-id="d0a2f-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0a2f-108">Parameter</span></span>|<span data-ttu-id="d0a2f-109">説明</span><span class="sxs-lookup"><span data-stu-id="d0a2f-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="d0a2f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d0a2f-110">Return Value</span></span>  
 <span data-ttu-id="d0a2f-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="d0a2f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a2f-112">要件</span><span class="sxs-lookup"><span data-stu-id="d0a2f-112">Requirements</span></span>  
 <span data-ttu-id="d0a2f-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d0a2f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a2f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0a2f-114">See Also</span></span>  
 [<span data-ttu-id="d0a2f-115">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0a2f-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
