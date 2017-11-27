---
title: "ISymUnmanagedWriter::OpenMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61d63fb96635e34e07c3997c1aad838e67c70742
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="7a91a-102">ISymUnmanagedWriter::OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="7a91a-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="7a91a-103">シンボル情報は生成先のメソッドを開きます。</span><span class="sxs-lookup"><span data-stu-id="7a91a-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="7a91a-104">特定のメソッドでは、シーケンス ポイント、パラメーター、および構文のスコープを定義する呼び出しの現在のメソッドになります。</span><span class="sxs-lookup"><span data-stu-id="7a91a-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="7a91a-105">メソッド全体を囲む暗黙的な構文のスコープがあります。</span><span class="sxs-lookup"><span data-stu-id="7a91a-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="7a91a-106">以前に閉じられたメソッドを再び開くには、そのメソッドの以前に定義されたシンボルが消去されます。</span><span class="sxs-lookup"><span data-stu-id="7a91a-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="7a91a-107">一度に 1 つだけの open メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="7a91a-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a91a-108">構文</span><span class="sxs-lookup"><span data-stu-id="7a91a-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a91a-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a91a-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="7a91a-110">[in]開かれるメソッドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="7a91a-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a91a-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a91a-111">Return Value</span></span>  
 <span data-ttu-id="7a91a-112">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="7a91a-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a91a-113">要件</span><span class="sxs-lookup"><span data-stu-id="7a91a-113">Requirements</span></span>  
 <span data-ttu-id="7a91a-114">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a91a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a91a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a91a-115">See Also</span></span>  
 [<span data-ttu-id="7a91a-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a91a-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="7a91a-117">CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="7a91a-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="7a91a-118">OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="7a91a-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
