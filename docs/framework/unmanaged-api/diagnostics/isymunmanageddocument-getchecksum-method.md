---
title: "ISymUnmanagedDocument::GetCheckSum メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b0b2ce6facf99b44f54e8880d4436ab7fe96e50a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="57e70-102">ISymUnmanagedDocument::GetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="57e70-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="57e70-103">チェックサムを取得します。</span><span class="sxs-lookup"><span data-stu-id="57e70-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e70-104">構文</span><span class="sxs-lookup"><span data-stu-id="57e70-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57e70-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57e70-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="57e70-106">[in]によって提供されるバッファーの長さ、`data`パラメーター</span><span class="sxs-lookup"><span data-stu-id="57e70-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="57e70-107">[out]サイズ (バイト単位)、チェックサムの長さ。</span><span class="sxs-lookup"><span data-stu-id="57e70-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="57e70-108">[out]チェックサムを受け取るバッファー。</span><span class="sxs-lookup"><span data-stu-id="57e70-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57e70-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="57e70-109">Return Value</span></span>  
 <span data-ttu-id="57e70-110">メソッドが成功した場合は S_OK、それ以外の場合、エラー コード。</span><span class="sxs-lookup"><span data-stu-id="57e70-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e70-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="57e70-111">See Also</span></span>  
 [<span data-ttu-id="57e70-112">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57e70-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
