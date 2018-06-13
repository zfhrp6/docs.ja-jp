---
title: ISymUnmanagedWriter2::DefineConstant2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6f9f198fc1115aed7b531515ab07ddc35d36ba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427337"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="3c28c-102">ISymUnmanagedWriter2::DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3c28c-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="3c28c-103">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="3c28c-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c28c-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c28c-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c28c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c28c-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3c28c-106">[in]定数の名前です。</span><span class="sxs-lookup"><span data-stu-id="3c28c-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="3c28c-107">[in]定数の値です。</span><span class="sxs-lookup"><span data-stu-id="3c28c-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="3c28c-108">[in]定数のメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="3c28c-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c28c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="3c28c-109">Return Value</span></span>  
 <span data-ttu-id="3c28c-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="3c28c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c28c-111">要件</span><span class="sxs-lookup"><span data-stu-id="3c28c-111">Requirements</span></span>  
 <span data-ttu-id="3c28c-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3c28c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c28c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c28c-113">See Also</span></span>  
 [<span data-ttu-id="3c28c-114">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c28c-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="3c28c-115">DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="3c28c-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
