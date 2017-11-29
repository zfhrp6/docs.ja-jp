---
title: "ISymUnmanagedReader::GetSymAttribute メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f57d2c4541945d90b1695850311928884fdc9cc5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="81dfa-102">ISymUnmanagedReader::GetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="81dfa-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="81dfa-103">その名前に基づくカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dfa-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="81dfa-104">メタデータのカスタム属性とは異なり、これらのカスタム属性は、シンボル ストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="81dfa-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81dfa-105">構文</span><span class="sxs-lookup"><span data-stu-id="81dfa-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81dfa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81dfa-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="81dfa-107">[in]属性を要求する対象のオブジェクトのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="81dfa-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="81dfa-108">[in]取得する属性を示す変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dfa-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="81dfa-109">[in] `buffer` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="81dfa-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="81dfa-110">[out]属性データの長さを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dfa-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="81dfa-111">[out]属性データを受信する変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dfa-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81dfa-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="81dfa-112">Return Value</span></span>  
 <span data-ttu-id="81dfa-113">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="81dfa-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81dfa-114">要件</span><span class="sxs-lookup"><span data-stu-id="81dfa-114">Requirements</span></span>  
 <span data-ttu-id="81dfa-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="81dfa-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81dfa-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="81dfa-116">See Also</span></span>  
 [<span data-ttu-id="81dfa-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81dfa-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
