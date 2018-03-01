---
title: "ISymUnmanagedBinder::GetReaderFromStream メソッド"
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
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 36d4d0067cd638eb39ce82eb042242b7b08d3647
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="03e10-102">ISymUnmanagedBinder::GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="03e10-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="03e10-103">メタデータ インターフェイスおよびをシンボル ストアを格納するストリームを指定して、正しい返します[ISymUnmanagedReader](isymunmanagedreader-interface.md)デバッグは読み取りを構造体は、特定のシンボル ストアからシンボルします。</span><span class="sxs-lookup"><span data-stu-id="03e10-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e10-104">構文</span><span class="sxs-lookup"><span data-stu-id="03e10-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03e10-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03e10-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="03e10-106">[in]メタデータ インポート インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="03e10-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="03e10-107">[in]シンボル ストアを格納しているストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="03e10-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="03e10-108">[out]設定されているポインターに返された[ISymUnmanagedReader](isymunmanagedreader-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="03e10-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03e10-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="03e10-109">Return Value</span></span>  
 <span data-ttu-id="03e10-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="03e10-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e10-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="03e10-111">Requirements</span></span>  
 <span data-ttu-id="03e10-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03e10-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e10-113">参照</span><span class="sxs-lookup"><span data-stu-id="03e10-113">See Also</span></span>  
 [<span data-ttu-id="03e10-114">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03e10-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
