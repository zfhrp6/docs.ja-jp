---
title: "GetResolutionScope メソッド"
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
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9dc63a7165ab472e973e0bc4f3e4cbb99e5d828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="f226c-102">GetResolutionScope メソッド</span><span class="sxs-lookup"><span data-stu-id="f226c-102">GetResolutionScope Method</span></span>
<span data-ttu-id="f226c-103">指定した型のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="f226c-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f226c-104">構文</span><span class="sxs-lookup"><span data-stu-id="f226c-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f226c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f226c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f226c-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="f226c-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f226c-107">参照が必要なファイルです。</span><span class="sxs-lookup"><span data-stu-id="f226c-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="f226c-108">その型が定義されているファイルのトークン[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="f226c-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="f226c-109">アセンブリまたはモジュールの参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f226c-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f226c-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f226c-110">Return Value</span></span>  
 <span data-ttu-id="f226c-111">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="f226c-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f226c-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="f226c-112">Requirements</span></span>  
 <span data-ttu-id="f226c-113">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="f226c-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f226c-114">参照</span><span class="sxs-lookup"><span data-stu-id="f226c-114">See Also</span></span>  
 [<span data-ttu-id="f226c-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f226c-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f226c-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f226c-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f226c-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="f226c-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
