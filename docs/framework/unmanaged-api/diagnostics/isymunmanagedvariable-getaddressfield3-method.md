---
title: "ISymUnmanagedVariable::GetAddressField3 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1dfeb3f02b0c767dfc200a625fa4c617692dc11f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="bd23d-102">ISymUnmanagedVariable::GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="bd23d-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="bd23d-103">この変数のアドレスの 3 番目のフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="bd23d-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="bd23d-104">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bd23d-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd23d-105">構文</span><span class="sxs-lookup"><span data-stu-id="bd23d-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd23d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bd23d-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bd23d-107">[out]ポインター、 `ULONG32` 3 番目のフィールドのアドレスを受け取る。</span><span class="sxs-lookup"><span data-stu-id="bd23d-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd23d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bd23d-108">Return Value</span></span>  
 <span data-ttu-id="bd23d-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="bd23d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd23d-110">要件</span><span class="sxs-lookup"><span data-stu-id="bd23d-110">Requirements</span></span>  
 <span data-ttu-id="bd23d-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bd23d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd23d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd23d-112">See Also</span></span>  
 [<span data-ttu-id="bd23d-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bd23d-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="bd23d-114">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="bd23d-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="bd23d-115">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="bd23d-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="bd23d-116">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="bd23d-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
