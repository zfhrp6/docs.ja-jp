---
title: "ISymUnmanagedWriter::CloseScope メソッド"
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
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d47be1d220729ed32fcf77a77e611003085c15d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="bbbc4-102">ISymUnmanagedWriter::CloseScope メソッド</span><span class="sxs-lookup"><span data-stu-id="bbbc4-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="bbbc4-103">現在の構文のスコープを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bbbc4-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbc4-104">構文</span><span class="sxs-lookup"><span data-stu-id="bbbc4-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbbc4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbbc4-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="bbbc4-106">[in](バイト単位) の構文のスコープ内の最後の命令の最後のポイントのメソッドの先頭からのオフセット。</span><span class="sxs-lookup"><span data-stu-id="bbbc4-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbbc4-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="bbbc4-107">Return Value</span></span>  
 <span data-ttu-id="bbbc4-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="bbbc4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbbc4-109">コメント</span><span class="sxs-lookup"><span data-stu-id="bbbc4-109">Remarks</span></span>  
 <span data-ttu-id="bbbc4-110">スコープが閉じられると、その中は変数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="bbbc4-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="bbbc4-111">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)で使用できる非透過スコープ識別子を返します[isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)を後で、スコープを定義の開始位置と終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="bbbc4-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="bbbc4-112">この場合、`ISymUnmanagedWriter::OpenScope` と `ISymUnmanagedWriter::CloseScope` に渡したオフセットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="bbbc4-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="bbbc4-113">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="bbbc4-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbbc4-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="bbbc4-114">Requirements</span></span>  
 <span data-ttu-id="bbbc4-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bbbc4-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbc4-116">参照</span><span class="sxs-lookup"><span data-stu-id="bbbc4-116">See Also</span></span>  
 [<span data-ttu-id="bbbc4-117">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbbc4-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
