---
title: "ISymUnmanagedVariable::GetAddressKind メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressKind
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 930b55c98609e5f3bc33f30da766c4556fbe5512
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="fe426-102">ISymUnmanagedVariable::GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="fe426-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="fe426-103">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="fe426-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe426-104">構文</span><span class="sxs-lookup"><span data-stu-id="fe426-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe426-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe426-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fe426-106">[out]ポインター、`ULONG32`値を受け取る。</span><span class="sxs-lookup"><span data-stu-id="fe426-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="fe426-107">使用可能な値が定義されている、 [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="fe426-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe426-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="fe426-108">Return Value</span></span>  
 <span data-ttu-id="fe426-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="fe426-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe426-110">要件</span><span class="sxs-lookup"><span data-stu-id="fe426-110">Requirements</span></span>  
 <span data-ttu-id="fe426-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fe426-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe426-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe426-112">See Also</span></span>  
 [<span data-ttu-id="fe426-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe426-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
