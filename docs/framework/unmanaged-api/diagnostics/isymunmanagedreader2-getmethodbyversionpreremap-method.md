---
title: "ISymUnmanagedReader2::GetMethodByVersionPreRemap メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0745428c6e9a51c5c7fa413838cf65eb907eea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="16468-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="16468-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="16468-103">指定したメソッドのトークンと、エディット コンティニュ バージョン番号、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="16468-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="16468-104">バージョン番号は 1 から開始し、エディット コンティニュの操作の結果として、メソッドが変更されるたびにインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="16468-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16468-105">構文</span><span class="sxs-lookup"><span data-stu-id="16468-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16468-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16468-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="16468-107">[in]メソッドのメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="16468-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="16468-108">[in]メソッドのバージョン。</span><span class="sxs-lookup"><span data-stu-id="16468-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="16468-109">[out]返されたへのポインター [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="16468-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16468-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="16468-110">Return Value</span></span>  
 <span data-ttu-id="16468-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="16468-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16468-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="16468-112">Requirements</span></span>  
 <span data-ttu-id="16468-113">**ヘッダー:** CorSym.idl です。</span><span class="sxs-lookup"><span data-stu-id="16468-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="16468-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16468-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16468-115">参照</span><span class="sxs-lookup"><span data-stu-id="16468-115">See Also</span></span>  
 [<span data-ttu-id="16468-116">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16468-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
