---
title: ISymUnmanagedDocument::GetCheckSum メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 660da82f1e6d6d3ea8ba084885331c895bc64542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424727"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="aed8b-102">ISymUnmanagedDocument::GetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="aed8b-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="aed8b-103">チェックサムを取得します。</span><span class="sxs-lookup"><span data-stu-id="aed8b-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="aed8b-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aed8b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aed8b-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="aed8b-106">[in]によって提供されるバッファーの長さ、`data`パラメーター</span><span class="sxs-lookup"><span data-stu-id="aed8b-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="aed8b-107">[out]サイズ (バイト単位)、チェックサムの長さ。</span><span class="sxs-lookup"><span data-stu-id="aed8b-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="aed8b-108">[out]チェックサムを受け取るバッファー。</span><span class="sxs-lookup"><span data-stu-id="aed8b-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aed8b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="aed8b-109">Return Value</span></span>  
 <span data-ttu-id="aed8b-110">メソッドが成功した場合は S_OK、それ以外の場合、エラー コード。</span><span class="sxs-lookup"><span data-stu-id="aed8b-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed8b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="aed8b-111">See Also</span></span>  
 [<span data-ttu-id="aed8b-112">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aed8b-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
