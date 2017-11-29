---
title: "ISymUnmanagedWriter::SetScopeRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetScopeRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b86df423d53c9fa3a738c603d6cc575add594cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="5ef1b-102">ISymUnmanagedWriter::SetScopeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="5ef1b-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="5ef1b-103">指定した構文のスコープのオフセット範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="5ef1b-104">スコープは、新しい現在のスコープをなり、スコープのスタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="5ef1b-105">スコープは、階層を形成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="5ef1b-106">兄弟は、重複は許可されません。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef1b-107">構文</span><span class="sxs-lookup"><span data-stu-id="5ef1b-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ef1b-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ef1b-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="5ef1b-109">[in]スコープのスコープの識別子。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="5ef1b-110">[in]メソッドの先頭から構文のスコープの最初の命令のバイト単位のオフセット。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="5ef1b-111">[in]メソッドの先頭から構文のスコープの最後の命令のバイト単位のオフセット。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ef1b-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5ef1b-112">Return Value</span></span>  
 <span data-ttu-id="5ef1b-113">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ef1b-114">コメント</span><span class="sxs-lookup"><span data-stu-id="5ef1b-114">Remarks</span></span>  
 <span data-ttu-id="5ef1b-115">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)で使用できる非透過スコープ識別子を返します`ISymUnmanagedWriter::SetScopeRange`スコープを定義の開始位置と終了は後でオフセットします。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="5ef1b-116">この場合に渡したオフセット`ISymUnmanagedWriter::OpenScope`と[isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="5ef1b-117">スコープ識別子では、現在のメソッドで有効なのみです。</span><span class="sxs-lookup"><span data-stu-id="5ef1b-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ef1b-118">要件</span><span class="sxs-lookup"><span data-stu-id="5ef1b-118">Requirements</span></span>  
 <span data-ttu-id="5ef1b-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5ef1b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef1b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ef1b-120">See Also</span></span>  
 [<span data-ttu-id="5ef1b-121">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ef1b-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
