---
title: "ISymUnmanagedWriter::UsingNamespace メソッド"
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
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d02a36a43e8a831fbbef051f5898696d4d8e04c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="274b8-102">ISymUnmanagedWriter::UsingNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="274b8-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="274b8-103">現在開かれている構文スコープ内で指定した名前空間の完全修飾名を使用していることを指定します。</span><span class="sxs-lookup"><span data-stu-id="274b8-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="274b8-104">名前空間は、現在開いているスコープから継承するすべてのスコープ内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="274b8-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="274b8-105">現在のスコープを閉じると、名前空間の使用も停止されます。</span><span class="sxs-lookup"><span data-stu-id="274b8-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="274b8-106">構文</span><span class="sxs-lookup"><span data-stu-id="274b8-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="274b8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="274b8-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="274b8-108">[in]名前空間の完全修飾名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="274b8-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="274b8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="274b8-109">Return Value</span></span>  
 <span data-ttu-id="274b8-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="274b8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="274b8-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="274b8-111">Requirements</span></span>  
 <span data-ttu-id="274b8-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="274b8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="274b8-113">参照</span><span class="sxs-lookup"><span data-stu-id="274b8-113">See Also</span></span>  
 [<span data-ttu-id="274b8-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="274b8-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
