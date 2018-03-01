---
title: "ISymUnmanagedVariable::GetAddressKind メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c4651641e3c430379b11698acf29eae450b02b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="ce6c7-102">ISymUnmanagedVariable::GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="ce6c7-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="ce6c7-103">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="ce6c7-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce6c7-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce6c7-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce6c7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce6c7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ce6c7-106">[out]ポインター、`ULONG32`値を受け取る。</span><span class="sxs-lookup"><span data-stu-id="ce6c7-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="ce6c7-107">使用可能な値が定義されている、 [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="ce6c7-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce6c7-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ce6c7-108">Return Value</span></span>  
 <span data-ttu-id="ce6c7-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ce6c7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce6c7-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="ce6c7-110">Requirements</span></span>  
 <span data-ttu-id="ce6c7-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ce6c7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6c7-112">参照</span><span class="sxs-lookup"><span data-stu-id="ce6c7-112">See Also</span></span>  
 [<span data-ttu-id="ce6c7-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce6c7-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
