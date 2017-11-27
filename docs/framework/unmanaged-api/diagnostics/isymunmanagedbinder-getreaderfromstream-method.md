---
title: "ISymUnmanagedBinder::GetReaderFromStream メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderFromStream
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 96bd12b69b84537415ddf2e0ae992ec179f32493
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="e2ea2-102">ISymUnmanagedBinder::GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="e2ea2-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="e2ea2-103">メタデータ インターフェイスおよびをシンボル ストアを格納するストリームを指定して、正しい返します <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> デバッグを読み取る構造は、特定のシンボル ストアからシンボルします。</span><span class="sxs-lookup"><span data-stu-id="e2ea2-103">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ea2-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2ea2-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2ea2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2ea2-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="e2ea2-106">[in]メタデータ インポート インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e2ea2-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="e2ea2-107">[in]シンボル ストアを格納しているストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e2ea2-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e2ea2-108">[out]設定されているポインターに返された <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="e2ea2-108">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2ea2-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="e2ea2-109">Return Value</span></span>  
 <span data-ttu-id="e2ea2-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="e2ea2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2ea2-111">要件</span><span class="sxs-lookup"><span data-stu-id="e2ea2-111">Requirements</span></span>  
 <span data-ttu-id="e2ea2-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e2ea2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ea2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2ea2-113">See Also</span></span>  
 [<span data-ttu-id="e2ea2-114">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e2ea2-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
