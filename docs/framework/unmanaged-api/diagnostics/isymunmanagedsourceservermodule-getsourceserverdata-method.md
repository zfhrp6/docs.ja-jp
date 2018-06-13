---
title: ISymUnmanagedSourceServerModule::GetSourceServerData メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afc041896615e906ac49eed9a7be139dff217463
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427012"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="f2de3-102">ISymUnmanagedSourceServerModule::GetSourceServerData メソッド</span><span class="sxs-lookup"><span data-stu-id="f2de3-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="f2de3-103">モジュールのソース サーバーのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="f2de3-103">Returns the source server data for the module.</span></span> <span data-ttu-id="f2de3-104">使用して、呼び出し元がリソースを解放する必要があります`CoTaskMemFree`です。</span><span class="sxs-lookup"><span data-stu-id="f2de3-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2de3-105">構文</span><span class="sxs-lookup"><span data-stu-id="f2de3-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2de3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f2de3-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="f2de3-107">[out]ポインター、`ULONG32`元サーバーのデータのバイト単位のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="f2de3-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="f2de3-108">[out]返されたへのポインター`pDataByteCount`値。</span><span class="sxs-lookup"><span data-stu-id="f2de3-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2de3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f2de3-109">Return Value</span></span>  
 <span data-ttu-id="f2de3-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f2de3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2de3-111">要件</span><span class="sxs-lookup"><span data-stu-id="f2de3-111">Requirements</span></span>  
 <span data-ttu-id="f2de3-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f2de3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2de3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2de3-113">See Also</span></span>  
 [<span data-ttu-id="f2de3-114">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2de3-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
