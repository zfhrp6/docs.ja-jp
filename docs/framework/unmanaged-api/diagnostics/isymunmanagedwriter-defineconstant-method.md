---
title: ISymUnmanagedWriter::DefineConstant メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c7cf800dafa9f3e213a012f49c73d51c78e7074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427406"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="20e80-102">ISymUnmanagedWriter::DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="20e80-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="20e80-103">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="20e80-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e80-104">構文</span><span class="sxs-lookup"><span data-stu-id="20e80-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20e80-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20e80-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="20e80-106">[in]ポインター、`WCHAR`定数名を定義します。</span><span class="sxs-lookup"><span data-stu-id="20e80-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="20e80-107">[in]定数の値です。</span><span class="sxs-lookup"><span data-stu-id="20e80-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="20e80-108">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="20e80-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="20e80-109">[in]定数の型のシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="20e80-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20e80-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="20e80-110">Return Value</span></span>  
 <span data-ttu-id="20e80-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="20e80-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e80-112">要件</span><span class="sxs-lookup"><span data-stu-id="20e80-112">Requirements</span></span>  
 <span data-ttu-id="20e80-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="20e80-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e80-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="20e80-114">See Also</span></span>  
 [<span data-ttu-id="20e80-115">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20e80-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="20e80-116">DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="20e80-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
