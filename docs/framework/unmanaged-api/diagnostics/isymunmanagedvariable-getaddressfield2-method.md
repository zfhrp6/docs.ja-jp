---
title: "ISymUnmanagedVariable::GetAddressField2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecde3a59c3a393057f3502c8ae59d789350b913f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="9f189-102">ISymUnmanagedVariable::GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="9f189-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="9f189-103">この変数の 2 番目のアドレス フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="9f189-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="9f189-104">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9f189-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f189-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f189-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f189-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f189-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9f189-107">[out]ポインター、`ULONG32`を受け取る 2 番目のアドレス フィールドです。</span><span class="sxs-lookup"><span data-stu-id="9f189-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f189-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f189-108">Return Value</span></span>  
 <span data-ttu-id="9f189-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="9f189-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f189-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="9f189-110">Requirements</span></span>  
 <span data-ttu-id="9f189-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9f189-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f189-112">参照</span><span class="sxs-lookup"><span data-stu-id="9f189-112">See Also</span></span>  
 [<span data-ttu-id="9f189-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f189-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="9f189-114">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="9f189-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="9f189-115">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="9f189-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="9f189-116">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="9f189-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
