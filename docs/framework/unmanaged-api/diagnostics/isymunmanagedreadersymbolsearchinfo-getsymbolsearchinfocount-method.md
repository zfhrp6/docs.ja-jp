---
title: "ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 99ee3e5a2d1f5987377ed7ac224c821cb0906757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="4cd93-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="4cd93-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="4cd93-103">シンボル検索情報の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="4cd93-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd93-104">構文</span><span class="sxs-lookup"><span data-stu-id="4cd93-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cd93-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4cd93-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="4cd93-106">out] へのポインター、`ULONG32`検索情報の格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="4cd93-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cd93-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="4cd93-107">Return Value</span></span>  
 <span data-ttu-id="4cd93-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="4cd93-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cd93-109">要件</span><span class="sxs-lookup"><span data-stu-id="4cd93-109">Requirements</span></span>  
 <span data-ttu-id="4cd93-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4cd93-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd93-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cd93-111">See Also</span></span>  
 [<span data-ttu-id="4cd93-112">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4cd93-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
