---
title: "ISymUnmanagedMethod::GetScopeFromOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetScopeFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b863031cae487a2c081f23aeada1971893aa339f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="20716-102">ISymUnmanagedMethod::GetScopeFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="20716-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="20716-103">このメソッドを指定したオフセットを囲む内で最も外側の構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="20716-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="20716-104">ローカル変数の検索を開始するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="20716-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20716-105">構文</span><span class="sxs-lookup"><span data-stu-id="20716-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20716-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20716-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="20716-107">[in]A`ULONG`オフセットを格納しています。</span><span class="sxs-lookup"><span data-stu-id="20716-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="20716-108">[out]設定されているポインターに返された[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="20716-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20716-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="20716-109">Return Value</span></span>  
 <span data-ttu-id="20716-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="20716-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20716-111">要件</span><span class="sxs-lookup"><span data-stu-id="20716-111">Requirements</span></span>  
 <span data-ttu-id="20716-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="20716-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20716-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="20716-113">See Also</span></span>  
 [<span data-ttu-id="20716-114">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20716-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
