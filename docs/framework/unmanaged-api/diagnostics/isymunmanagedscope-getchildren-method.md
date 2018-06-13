---
title: ISymUnmanagedScope::GetChildren メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ce2372be02bc0bae7097389d4933f1f28a4ed79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427051"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="ebd25-102">ISymUnmanagedScope::GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="ebd25-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="ebd25-103">このスコープの子を取得します。</span><span class="sxs-lookup"><span data-stu-id="ebd25-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd25-104">構文</span><span class="sxs-lookup"><span data-stu-id="ebd25-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebd25-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebd25-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="ebd25-106">[in]A`ULONG32`のサイズを示す、`children`配列。</span><span class="sxs-lookup"><span data-stu-id="ebd25-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="ebd25-107">[out]ポインター、`ULONG32`子の格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="ebd25-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="ebd25-108">[out]返された子の配列。</span><span class="sxs-lookup"><span data-stu-id="ebd25-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebd25-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ebd25-109">Return Value</span></span>  
 <span data-ttu-id="ebd25-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ebd25-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd25-111">要件</span><span class="sxs-lookup"><span data-stu-id="ebd25-111">Requirements</span></span>  
 <span data-ttu-id="ebd25-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ebd25-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd25-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebd25-113">See Also</span></span>  
 [<span data-ttu-id="ebd25-114">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ebd25-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="ebd25-115">GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="ebd25-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
