---
title: "ISymUnmanagedVariable::GetEndOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7a2dac8425cd852c6c17ee1674710f6798d3b1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="75d68-102">ISymUnmanagedVariable::GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="75d68-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="75d68-103">この変数内では、親の終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="75d68-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="75d68-104">場合、ローカル変数のスコープ内では、終了オフセットはスコープに対して定義されたオフセット内で分類されます。</span><span class="sxs-lookup"><span data-stu-id="75d68-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75d68-105">構文</span><span class="sxs-lookup"><span data-stu-id="75d68-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75d68-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="75d68-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="75d68-107">[out]ポインター、`ULONG32`を受け取る、終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="75d68-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75d68-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="75d68-108">Return Value</span></span>  
 <span data-ttu-id="75d68-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="75d68-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75d68-110">要件</span><span class="sxs-lookup"><span data-stu-id="75d68-110">Requirements</span></span>  
 <span data-ttu-id="75d68-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="75d68-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d68-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="75d68-112">See Also</span></span>  
 [<span data-ttu-id="75d68-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75d68-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="75d68-114">GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="75d68-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
