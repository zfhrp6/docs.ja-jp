---
title: "GetResolutionScope メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetResolutionScope
api_location: alink.dll
api_type: COM
f1_keywords: GetResolutionScope
helpviewer_keywords: GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11ccbce4d8e9783514050f6b41c6e32cde6c274f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="a9cd3-102">GetResolutionScope メソッド</span><span class="sxs-lookup"><span data-stu-id="a9cd3-102">GetResolutionScope Method</span></span>
<span data-ttu-id="a9cd3-103">指定した型のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="a9cd3-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9cd3-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9cd3-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9cd3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9cd3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a9cd3-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="a9cd3-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a9cd3-107">参照が必要なファイルです。</span><span class="sxs-lookup"><span data-stu-id="a9cd3-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="a9cd3-108">その型が定義されているファイルのトークン[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9cd3-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="a9cd3-109">アセンブリまたはモジュールの参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a9cd3-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9cd3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a9cd3-110">Return Value</span></span>  
 <span data-ttu-id="a9cd3-111">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="a9cd3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9cd3-112">要件</span><span class="sxs-lookup"><span data-stu-id="a9cd3-112">Requirements</span></span>  
 <span data-ttu-id="a9cd3-113">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="a9cd3-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9cd3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9cd3-114">See Also</span></span>  
 [<span data-ttu-id="a9cd3-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9cd3-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a9cd3-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9cd3-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a9cd3-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="a9cd3-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
