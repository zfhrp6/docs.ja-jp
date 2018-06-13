---
title: ISymUnmanagedReader::GetMethodByVersion メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef5888c33e9532e5fc132fe571d59699d6f80c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425178"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="ccfe6-102">ISymUnmanagedReader::GetMethodByVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="ccfe6-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="ccfe6-103">メソッドのトークンと編集、コピーのバージョン番号を指定、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="ccfe6-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="ccfe6-104">バージョン番号は 1 から開始し、編集、コピー操作の結果として、メソッドが変更されるたびにインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="ccfe6-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccfe6-105">構文</span><span class="sxs-lookup"><span data-stu-id="ccfe6-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccfe6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccfe6-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="ccfe6-107">[in]メソッド トークンです。</span><span class="sxs-lookup"><span data-stu-id="ccfe6-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="ccfe6-108">[in]メソッドのバージョン。</span><span class="sxs-lookup"><span data-stu-id="ccfe6-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ccfe6-109">[out]返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccfe6-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccfe6-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="ccfe6-110">Return Value</span></span>  
 <span data-ttu-id="ccfe6-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ccfe6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccfe6-112">要件</span><span class="sxs-lookup"><span data-stu-id="ccfe6-112">Requirements</span></span>  
 <span data-ttu-id="ccfe6-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ccfe6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfe6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccfe6-114">See Also</span></span>  
 [<span data-ttu-id="ccfe6-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccfe6-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
