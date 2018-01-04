---
title: "ISymUnmanagedScope::GetStartOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e0328af628eec062dc9efa7012bbeff213f1b86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="60c14-102">ISymUnmanagedScope::GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="60c14-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="60c14-103">このスコープの開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="60c14-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c14-104">構文</span><span class="sxs-lookup"><span data-stu-id="60c14-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60c14-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60c14-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="60c14-106">[out]ポインター、`ULONG32`開始オフセットを格納しています。</span><span class="sxs-lookup"><span data-stu-id="60c14-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60c14-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="60c14-107">Return Value</span></span>  
 <span data-ttu-id="60c14-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="60c14-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60c14-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="60c14-109">Requirements</span></span>  
 <span data-ttu-id="60c14-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="60c14-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c14-111">参照</span><span class="sxs-lookup"><span data-stu-id="60c14-111">See Also</span></span>  
 [<span data-ttu-id="60c14-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60c14-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="60c14-113">GetEndOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="60c14-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
