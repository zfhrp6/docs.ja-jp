---
title: "PreCloseAssembly メソッド"
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
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a4d1f2eed036552ab17b6768b7b2d84f4a52c9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="2159f-102">PreCloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2159f-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="2159f-103">アセンブリ ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2159f-103">Closes the assembly file.</span></span> <span data-ttu-id="2159f-104">閉じると、その他のすべてのファイルがアセンブリ ファイルを閉じる前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2159f-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="2159f-105">非バインド モジュールのこのメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="2159f-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2159f-106">構文</span><span class="sxs-lookup"><span data-stu-id="2159f-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2159f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2159f-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2159f-108">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="2159f-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2159f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="2159f-109">Return Value</span></span>  
 <span data-ttu-id="2159f-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="2159f-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2159f-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="2159f-111">Requirements</span></span>  
 <span data-ttu-id="2159f-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="2159f-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2159f-113">参照</span><span class="sxs-lookup"><span data-stu-id="2159f-113">See Also</span></span>  
 [<span data-ttu-id="2159f-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2159f-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2159f-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2159f-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2159f-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="2159f-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
