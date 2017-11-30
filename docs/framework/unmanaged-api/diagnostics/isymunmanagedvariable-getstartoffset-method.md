---
title: "ISymUnmanagedVariable::GetStartOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b7fd3a64202224ef5a7cc348ee8e9974a664d09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="b518b-102">ISymUnmanagedVariable::GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="b518b-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="b518b-103">この変数内では、親の開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="b518b-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="b518b-104">場合、ローカル変数のスコープ内では、開始オフセットはスコープに対して定義されたオフセットに分類されます。</span><span class="sxs-lookup"><span data-stu-id="b518b-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b518b-105">構文</span><span class="sxs-lookup"><span data-stu-id="b518b-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b518b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b518b-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b518b-107">[out]ポインター、`ULONG32`を受け取る、開始オフセット。</span><span class="sxs-lookup"><span data-stu-id="b518b-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b518b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b518b-108">Return Value</span></span>  
 <span data-ttu-id="b518b-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="b518b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b518b-110">要件</span><span class="sxs-lookup"><span data-stu-id="b518b-110">Requirements</span></span>  
 <span data-ttu-id="b518b-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b518b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b518b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b518b-112">See Also</span></span>  
 [<span data-ttu-id="b518b-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b518b-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="b518b-114">GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="b518b-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
