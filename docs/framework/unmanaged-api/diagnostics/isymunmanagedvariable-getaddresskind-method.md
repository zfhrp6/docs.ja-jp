---
title: ISymUnmanagedVariable::GetAddressKind メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18e83582a73ba3b2eb2538bcdf60984c46131768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426956"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="ec4b7-102">ISymUnmanagedVariable::GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="ec4b7-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="ec4b7-103">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4b7-104">構文</span><span class="sxs-lookup"><span data-stu-id="ec4b7-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec4b7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec4b7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ec4b7-106">[out]ポインター、`ULONG32`値を受け取る。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="ec4b7-107">使用可能な値が定義されている、 [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec4b7-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ec4b7-108">Return Value</span></span>  
 <span data-ttu-id="ec4b7-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ec4b7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4b7-110">要件</span><span class="sxs-lookup"><span data-stu-id="ec4b7-110">Requirements</span></span>  
 <span data-ttu-id="ec4b7-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ec4b7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4b7-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec4b7-112">See Also</span></span>  
 [<span data-ttu-id="ec4b7-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec4b7-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
