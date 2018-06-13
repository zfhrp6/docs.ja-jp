---
title: ISymUnmanagedReader::GetMethodVersion メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d850363940ff53135fc66ec057ee67822fa40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424665"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="79cc3-102">ISymUnmanagedReader::GetMethodVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="79cc3-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="79cc3-103">メソッドのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="79cc3-103">Gets the method version.</span></span> <span data-ttu-id="79cc3-104">メソッドのバージョンでは、1 から開始され、メソッドが再コンパイルされるたびに増分が。</span><span class="sxs-lookup"><span data-stu-id="79cc3-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="79cc3-105">再コンパイルは、メソッドに変更することがなく発生します。</span><span class="sxs-lookup"><span data-stu-id="79cc3-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79cc3-106">構文</span><span class="sxs-lookup"><span data-stu-id="79cc3-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79cc3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79cc3-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="79cc3-108">[in]バージョンを取得する方法です。</span><span class="sxs-lookup"><span data-stu-id="79cc3-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="79cc3-109">[out]メソッドのバージョンを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="79cc3-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79cc3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="79cc3-110">Return Value</span></span>  
 <span data-ttu-id="79cc3-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="79cc3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79cc3-112">要件</span><span class="sxs-lookup"><span data-stu-id="79cc3-112">Requirements</span></span>  
 <span data-ttu-id="79cc3-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="79cc3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79cc3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="79cc3-114">See Also</span></span>  
 [<span data-ttu-id="79cc3-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79cc3-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
