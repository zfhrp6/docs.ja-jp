---
title: "ISymUnmanagedSymbolSearchInfo::GetSearchPath メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c896c8bc8aa852fb69f182e484243a0c379e0a1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="2510f-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath メソッド</span><span class="sxs-lookup"><span data-stu-id="2510f-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="2510f-103">検索パスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2510f-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2510f-104">構文</span><span class="sxs-lookup"><span data-stu-id="2510f-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2510f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2510f-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="2510f-106">[out]ポインター、`ULONG32`検索パスの格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="2510f-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2510f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="2510f-107">Return Value</span></span>  
 <span data-ttu-id="2510f-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="2510f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2510f-109">要件</span><span class="sxs-lookup"><span data-stu-id="2510f-109">Requirements</span></span>  
 <span data-ttu-id="2510f-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2510f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2510f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="2510f-111">See Also</span></span>  
 [<span data-ttu-id="2510f-112">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2510f-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
