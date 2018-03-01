---
title: "ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo メソッド"
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
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ecddc85ba473b4cff20331013b283ad12cf9bbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="36859-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="36859-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="36859-103">シンボル検索情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="36859-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36859-104">構文</span><span class="sxs-lookup"><span data-stu-id="36859-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36859-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36859-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="36859-106">[in]A`ULONG32`のサイズを示す`rgpSearchInfo`です。</span><span class="sxs-lookup"><span data-stu-id="36859-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="36859-107">[out]ポインター、`ULONG32`検索情報の格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="36859-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="36859-108">[out]設定されているポインターに返された[ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="36859-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36859-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="36859-109">Return Value</span></span>  
 <span data-ttu-id="36859-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="36859-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36859-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="36859-111">Requirements</span></span>  
 <span data-ttu-id="36859-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="36859-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36859-113">参照</span><span class="sxs-lookup"><span data-stu-id="36859-113">See Also</span></span>  
 [<span data-ttu-id="36859-114">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36859-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
