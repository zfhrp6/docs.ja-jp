---
title: ISymUnmanagedMethod::GetParameters メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fbedb7b1c10dcc2b9b9940db10aae7e4101436b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426212"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="36456-102">ISymUnmanagedMethod::GetParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="36456-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="36456-103">このメソッドのパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="36456-103">Gets the parameters for this method.</span></span> <span data-ttu-id="36456-104">パラメーターは、メソッドのシグネチャ内で定義されている順序で返されます。</span><span class="sxs-lookup"><span data-stu-id="36456-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36456-105">構文</span><span class="sxs-lookup"><span data-stu-id="36456-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36456-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36456-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="36456-107">[in] `params` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="36456-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="36456-108">[in]ポインター、`ULONG32`パラメーターを格納するために必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="36456-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="36456-109">[out]パラメーターを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="36456-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36456-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="36456-110">Return Value</span></span>  
 <span data-ttu-id="36456-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="36456-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36456-112">要件</span><span class="sxs-lookup"><span data-stu-id="36456-112">Requirements</span></span>  
 <span data-ttu-id="36456-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="36456-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36456-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="36456-114">See Also</span></span>  
 [<span data-ttu-id="36456-115">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36456-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
