---
title: "GetAssemblyRefHash メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetAssemblyRefHash
api_location: alink.dll
api_type: COM
f1_keywords: GetAssemblyRefHash
helpviewer_keywords: GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99ae38025f223d669a428738783676ebc0687554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="0e872-102">GetAssemblyRefHash メソッド</span><span class="sxs-lookup"><span data-stu-id="0e872-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="0e872-103">特定のアセンブリには、ハッシュ blob を取得します。</span><span class="sxs-lookup"><span data-stu-id="0e872-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e872-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e872-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e872-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e872-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="0e872-106">ハッシュが参照するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="0e872-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="0e872-107">結果のハッシュ blob を受信します。</span><span class="sxs-lookup"><span data-stu-id="0e872-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="0e872-108">ハッシュ blob のバイト単位のサイズを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0e872-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e872-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="0e872-109">Return Value</span></span>  
 <span data-ttu-id="0e872-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="0e872-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e872-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="0e872-111">Requirements</span></span>  
 <span data-ttu-id="0e872-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="0e872-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e872-113">参照</span><span class="sxs-lookup"><span data-stu-id="0e872-113">See Also</span></span>  
 [<span data-ttu-id="0e872-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e872-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0e872-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e872-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0e872-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="0e872-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
