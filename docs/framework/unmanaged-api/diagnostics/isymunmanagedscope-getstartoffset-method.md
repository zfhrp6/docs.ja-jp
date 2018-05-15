---
title: ISymUnmanagedScope::GetStartOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19d116825efc4eb2ec1de22f232f46f8fb0fdf18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="a1b01-102">ISymUnmanagedScope::GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="a1b01-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="a1b01-103">このスコープの開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="a1b01-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b01-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1b01-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1b01-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1b01-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a1b01-106">[out]ポインター、`ULONG32`開始オフセットを格納しています。</span><span class="sxs-lookup"><span data-stu-id="a1b01-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1b01-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1b01-107">Return Value</span></span>  
 <span data-ttu-id="a1b01-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="a1b01-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1b01-109">要件</span><span class="sxs-lookup"><span data-stu-id="a1b01-109">Requirements</span></span>  
 <span data-ttu-id="a1b01-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a1b01-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b01-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1b01-111">See Also</span></span>  
 [<span data-ttu-id="a1b01-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1b01-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="a1b01-113">GetEndOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="a1b01-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
