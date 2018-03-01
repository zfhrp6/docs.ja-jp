---
title: "ISymUnmanagedReader::GetUserEntryPoint メソッド"
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
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 328f44e797a49a899545fa43d940a3b0399ee8c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="69155-102">ISymUnmanagedReader::GetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="69155-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="69155-103">存在する場合は、モジュールのユーザー エントリ ポイントとして指定されたメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="69155-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="69155-104">たとえば、このメソッドは、メイン メソッドの前に、コンパイラによって生成されたスタブではなく、ユーザーのメイン メソッド可能性があります。</span><span class="sxs-lookup"><span data-stu-id="69155-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69155-105">構文</span><span class="sxs-lookup"><span data-stu-id="69155-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69155-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69155-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="69155-107">[out]エントリ ポイントを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="69155-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69155-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="69155-108">Return Value</span></span>  
 <span data-ttu-id="69155-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="69155-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69155-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="69155-110">Requirements</span></span>  
 <span data-ttu-id="69155-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="69155-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69155-112">参照</span><span class="sxs-lookup"><span data-stu-id="69155-112">See Also</span></span>  
 [<span data-ttu-id="69155-113">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69155-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
