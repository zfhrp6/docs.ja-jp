---
title: ISymUnmanagedVariable::GetStartOffset メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b25d072ab96b822e79c6f87f535096550e4bb53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427064"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="852a6-102">ISymUnmanagedVariable::GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="852a6-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="852a6-103">この変数内では、親の開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="852a6-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="852a6-104">場合、ローカル変数のスコープ内では、開始オフセットはスコープに対して定義されたオフセットに分類されます。</span><span class="sxs-lookup"><span data-stu-id="852a6-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="852a6-105">構文</span><span class="sxs-lookup"><span data-stu-id="852a6-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="852a6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="852a6-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="852a6-107">[out]ポインター、`ULONG32`を受け取る、開始オフセット。</span><span class="sxs-lookup"><span data-stu-id="852a6-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="852a6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="852a6-108">Return Value</span></span>  
 <span data-ttu-id="852a6-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="852a6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="852a6-110">要件</span><span class="sxs-lookup"><span data-stu-id="852a6-110">Requirements</span></span>  
 <span data-ttu-id="852a6-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="852a6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852a6-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="852a6-112">See Also</span></span>  
 [<span data-ttu-id="852a6-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="852a6-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="852a6-114">GetEndOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="852a6-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
