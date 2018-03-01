---
title: "CloseAssembly メソッド"
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
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 160ec53440f4ecdb924537c732a367881e75acf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="closeassembly-method"></a><span data-ttu-id="c10ed-102">CloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="c10ed-102">CloseAssembly Method</span></span>
<span data-ttu-id="c10ed-103">アセンブリの操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="c10ed-103">Finalizes assembly operations.</span></span> <span data-ttu-id="c10ed-104">新しいアセンブリまたは非バインド モジュールを開始する前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c10ed-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c10ed-105">構文</span><span class="sxs-lookup"><span data-stu-id="c10ed-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c10ed-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c10ed-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c10ed-107">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="c10ed-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c10ed-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="c10ed-108">Return Value</span></span>  
 <span data-ttu-id="c10ed-109">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="c10ed-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c10ed-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="c10ed-110">Requirements</span></span>  
 <span data-ttu-id="c10ed-111">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="c10ed-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c10ed-112">参照</span><span class="sxs-lookup"><span data-stu-id="c10ed-112">See Also</span></span>  
 [<span data-ttu-id="c10ed-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c10ed-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c10ed-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c10ed-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c10ed-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="c10ed-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
