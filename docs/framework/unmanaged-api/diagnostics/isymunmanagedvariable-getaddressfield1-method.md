---
title: ISymUnmanagedVariable::GetAddressField1 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f9e0e234a8f77ef35ad93302fe8fc676cf9dbaeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="6ee98-102">ISymUnmanagedVariable::GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="6ee98-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="6ee98-103">この変数の最初のアドレス フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="6ee98-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="6ee98-104">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6ee98-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee98-105">構文</span><span class="sxs-lookup"><span data-stu-id="6ee98-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ee98-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ee98-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6ee98-107">[out]ポインター、`ULONG32`最初のアドレス フィールドを受け取る。</span><span class="sxs-lookup"><span data-stu-id="6ee98-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ee98-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="6ee98-108">Return Value</span></span>  
 <span data-ttu-id="6ee98-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="6ee98-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ee98-110">要件</span><span class="sxs-lookup"><span data-stu-id="6ee98-110">Requirements</span></span>  
 <span data-ttu-id="6ee98-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ee98-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee98-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ee98-112">See Also</span></span>  
 [<span data-ttu-id="6ee98-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ee98-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="6ee98-114">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="6ee98-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="6ee98-115">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="6ee98-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="6ee98-116">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="6ee98-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
