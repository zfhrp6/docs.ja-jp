---
title: "ISymUnmanagedSourceServerModule::GetSourceServerData メソッド"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f75ffbe3980a6c7587912a1cf099ef87888132a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="ecc23-102">ISymUnmanagedSourceServerModule::GetSourceServerData メソッド</span><span class="sxs-lookup"><span data-stu-id="ecc23-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="ecc23-103">モジュールのソース サーバーのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="ecc23-103">Returns the source server data for the module.</span></span> <span data-ttu-id="ecc23-104">使用して、呼び出し元がリソースを解放する必要があります`CoTaskMemFree`です。</span><span class="sxs-lookup"><span data-stu-id="ecc23-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc23-105">構文</span><span class="sxs-lookup"><span data-stu-id="ecc23-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecc23-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecc23-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="ecc23-107">[out]ポインター、`ULONG32`元サーバーのデータのバイト単位のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="ecc23-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="ecc23-108">[out]返されたへのポインター`pDataByteCount`値。</span><span class="sxs-lookup"><span data-stu-id="ecc23-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecc23-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ecc23-109">Return Value</span></span>  
 <span data-ttu-id="ecc23-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ecc23-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc23-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="ecc23-111">Requirements</span></span>  
 <span data-ttu-id="ecc23-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ecc23-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc23-113">参照</span><span class="sxs-lookup"><span data-stu-id="ecc23-113">See Also</span></span>  
 [<span data-ttu-id="ecc23-114">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecc23-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
