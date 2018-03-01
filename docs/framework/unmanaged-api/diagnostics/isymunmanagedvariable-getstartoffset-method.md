---
title: "ISymUnmanagedVariable::GetStartOffset メソッド"
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
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3fa0c710eb5de8b9a92970002336de22adb2458
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="ea4b3-102">ISymUnmanagedVariable::GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="ea4b3-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="ea4b3-103">この変数内では、親の開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="ea4b3-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="ea4b3-104">場合、ローカル変数のスコープ内では、開始オフセットはスコープに対して定義されたオフセットに分類されます。</span><span class="sxs-lookup"><span data-stu-id="ea4b3-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea4b3-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea4b3-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea4b3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea4b3-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ea4b3-107">[out]ポインター、`ULONG32`を受け取る、開始オフセット。</span><span class="sxs-lookup"><span data-stu-id="ea4b3-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea4b3-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ea4b3-108">Return Value</span></span>  
 <span data-ttu-id="ea4b3-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ea4b3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea4b3-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="ea4b3-110">Requirements</span></span>  
 <span data-ttu-id="ea4b3-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ea4b3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4b3-112">参照</span><span class="sxs-lookup"><span data-stu-id="ea4b3-112">See Also</span></span>  
 [<span data-ttu-id="ea4b3-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea4b3-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="ea4b3-114">GetEndOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="ea4b3-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
