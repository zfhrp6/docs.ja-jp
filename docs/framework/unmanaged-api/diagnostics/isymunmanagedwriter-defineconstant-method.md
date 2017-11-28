---
title: "ISymUnmanagedWriter::DefineConstant メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineConstant
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 910f2e753849b955a398f2175342b2f94849fba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="6c63c-102">ISymUnmanagedWriter::DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="6c63c-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="6c63c-103">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c63c-104">構文</span><span class="sxs-lookup"><span data-stu-id="6c63c-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c63c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6c63c-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6c63c-106">[in]ポインター、`WCHAR`定数名を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="6c63c-107">[in]定数の値です。</span><span class="sxs-lookup"><span data-stu-id="6c63c-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="6c63c-108">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c63c-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="6c63c-109">[in]定数の型のシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="6c63c-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c63c-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="6c63c-110">Return Value</span></span>  
 <span data-ttu-id="6c63c-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="6c63c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c63c-112">要件</span><span class="sxs-lookup"><span data-stu-id="6c63c-112">Requirements</span></span>  
 <span data-ttu-id="6c63c-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c63c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c63c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c63c-114">See Also</span></span>  
 [<span data-ttu-id="6c63c-115">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c63c-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="6c63c-116">DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="6c63c-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
