---
title: ISymUnmanagedVariable::GetEndOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0f11614c6fa15034ef5fa3d68e41a936a9ff764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427858"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="bf079-102">ISymUnmanagedVariable::GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="bf079-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="bf079-103">この変数内では、親の終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf079-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="bf079-104">場合、ローカル変数のスコープ内では、終了オフセットはスコープに対して定義されたオフセット内で分類されます。</span><span class="sxs-lookup"><span data-stu-id="bf079-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf079-105">構文</span><span class="sxs-lookup"><span data-stu-id="bf079-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf079-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf079-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bf079-107">[out]ポインター、`ULONG32`を受け取る、終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="bf079-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf079-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bf079-108">Return Value</span></span>  
 <span data-ttu-id="bf079-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="bf079-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf079-110">要件</span><span class="sxs-lookup"><span data-stu-id="bf079-110">Requirements</span></span>  
 <span data-ttu-id="bf079-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bf079-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf079-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf079-112">See Also</span></span>  
 [<span data-ttu-id="bf079-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf079-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="bf079-114">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="bf079-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
