---
title: "SetNonAssemblyFlags メソッド"
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
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e944f285ee0925b76fdd9b95c824deee38cead2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="72522-102">SetNonAssemblyFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="72522-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="72522-103">アセンブリに固有でないフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="72522-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72522-104">構文</span><span class="sxs-lookup"><span data-stu-id="72522-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72522-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72522-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="72522-106">ALink フラグです。</span><span class="sxs-lookup"><span data-stu-id="72522-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72522-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="72522-107">Return Value</span></span>  
 <span data-ttu-id="72522-108">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="72522-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72522-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="72522-109">Requirements</span></span>  
 <span data-ttu-id="72522-110">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="72522-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72522-111">参照</span><span class="sxs-lookup"><span data-stu-id="72522-111">See Also</span></span>  
 [<span data-ttu-id="72522-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72522-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="72522-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72522-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="72522-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="72522-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
