---
title: "ISymUnmanagedWriter::SetSymAttribute メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90360d6fe5a1a95719a9bb09e5e0b6b2a70675a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="30ca9-102">ISymUnmanagedWriter::SetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="30ca9-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="30ca9-103">その名前に基づくカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="30ca9-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="30ca9-104">これらの属性は、カスタム属性のメタデータとは異なり、シンボル ストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="30ca9-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ca9-105">構文</span><span class="sxs-lookup"><span data-stu-id="30ca9-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30ca9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30ca9-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="30ca9-107">[in]属性が定義されているメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="30ca9-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="30ca9-108">[in]ポインター、`WCHAR`属性名を格納しています。</span><span class="sxs-lookup"><span data-stu-id="30ca9-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="30ca9-109">[in]A`ULONG32`のサイズを示す、`data`配列。</span><span class="sxs-lookup"><span data-stu-id="30ca9-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="30ca9-110">[in]属性の値。</span><span class="sxs-lookup"><span data-stu-id="30ca9-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30ca9-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="30ca9-111">Return Value</span></span>  
 <span data-ttu-id="30ca9-112">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="30ca9-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30ca9-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="30ca9-113">Requirements</span></span>  
 <span data-ttu-id="30ca9-114">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="30ca9-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ca9-115">参照</span><span class="sxs-lookup"><span data-stu-id="30ca9-115">See Also</span></span>  
 [<span data-ttu-id="30ca9-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30ca9-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
