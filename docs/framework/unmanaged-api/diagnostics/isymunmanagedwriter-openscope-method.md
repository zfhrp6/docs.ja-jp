---
title: "ISymUnmanagedWriter::OpenScope メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f56bc14b096b5086db1fc8d046ed699559381fb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="31350-102">ISymUnmanagedWriter::OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="31350-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="31350-103">現在のメソッドの構文の新しいスコープを開きます。</span><span class="sxs-lookup"><span data-stu-id="31350-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="31350-104">スコープは、新しい現在のスコープをなり、スコープのスタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="31350-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="31350-105">スコープは、階層を形成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31350-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="31350-106">兄弟は、重複は許可されません。</span><span class="sxs-lookup"><span data-stu-id="31350-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31350-107">構文</span><span class="sxs-lookup"><span data-stu-id="31350-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31350-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31350-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="31350-109">[in]メソッドの先頭からのバイト単位での構文のスコープ内の最初の命令のオフセット。</span><span class="sxs-lookup"><span data-stu-id="31350-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="31350-110">[out]ポインター、`ULONG32`スコープ識別子を受け取る。</span><span class="sxs-lookup"><span data-stu-id="31350-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31350-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="31350-111">Return Value</span></span>  
 <span data-ttu-id="31350-112">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="31350-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31350-113">コメント</span><span class="sxs-lookup"><span data-stu-id="31350-113">Remarks</span></span>  
 <span data-ttu-id="31350-114">`ISymUnmanagedWriter::OpenScope`使用できる非透過スコープ識別子を返します[isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)スコープを定義の開始位置と終了は後でオフセットします。</span><span class="sxs-lookup"><span data-stu-id="31350-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="31350-115">この場合に渡したオフセット`ISymUnmanagedWriter::OpenScope`と[isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="31350-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="31350-116">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="31350-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31350-117">要件</span><span class="sxs-lookup"><span data-stu-id="31350-117">Requirements</span></span>  
 <span data-ttu-id="31350-118">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31350-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31350-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="31350-119">See Also</span></span>  
 [<span data-ttu-id="31350-120">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31350-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
