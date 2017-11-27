---
title: "ISymUnmanagedWriter::CloseScope メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8df22e5f9ea2ca294f502fcebf4b2ed5cd7900d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="87d2b-102">ISymUnmanagedWriter::CloseScope メソッド</span><span class="sxs-lookup"><span data-stu-id="87d2b-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="87d2b-103">現在の構文のスコープを閉じます。</span><span class="sxs-lookup"><span data-stu-id="87d2b-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d2b-104">構文</span><span class="sxs-lookup"><span data-stu-id="87d2b-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87d2b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87d2b-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="87d2b-106">[in](バイト単位) の構文のスコープ内の最後の命令の最後のポイントのメソッドの先頭からのオフセット。</span><span class="sxs-lookup"><span data-stu-id="87d2b-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87d2b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="87d2b-107">Return Value</span></span>  
 <span data-ttu-id="87d2b-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="87d2b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87d2b-109">コメント</span><span class="sxs-lookup"><span data-stu-id="87d2b-109">Remarks</span></span>  
 <span data-ttu-id="87d2b-110">スコープが閉じられると、その中は変数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="87d2b-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="87d2b-111">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)で使用できる非透過スコープ識別子を返します[isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)を後で、スコープを定義の開始位置と終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="87d2b-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="87d2b-112">この場合、`ISymUnmanagedWriter::OpenScope` と `ISymUnmanagedWriter::CloseScope` に渡したオフセットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="87d2b-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="87d2b-113">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="87d2b-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d2b-114">要件</span><span class="sxs-lookup"><span data-stu-id="87d2b-114">Requirements</span></span>  
 <span data-ttu-id="87d2b-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="87d2b-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d2b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="87d2b-116">See Also</span></span>  
 [<span data-ttu-id="87d2b-117">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87d2b-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
