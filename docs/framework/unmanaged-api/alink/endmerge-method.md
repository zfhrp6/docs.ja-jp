---
title: "EndMerge メソッド"
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
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58e9cecae43fb69f1ce2e90eb9d6551d287ca7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endmerge-method"></a><span data-ttu-id="e7175-102">EndMerge メソッド</span><span class="sxs-lookup"><span data-stu-id="e7175-102">EndMerge Method</span></span>
<span data-ttu-id="e7175-103">すべてのカスタム属性が生成スコープにマージされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e7175-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7175-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7175-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7175-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7175-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e7175-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="e7175-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7175-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e7175-107">Return Value</span></span>  
 <span data-ttu-id="e7175-108">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="e7175-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7175-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="e7175-109">Requirements</span></span>  
 <span data-ttu-id="e7175-110">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="e7175-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7175-111">参照</span><span class="sxs-lookup"><span data-stu-id="e7175-111">See Also</span></span>  
 [<span data-ttu-id="e7175-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7175-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e7175-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7175-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e7175-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="e7175-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
