---
title: "EmitAssembly メソッド"
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
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f012ea89fec0e64bc1639e6c47fb79249c25411a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="501c3-102">EmitAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="501c3-102">EmitAssembly Method</span></span>
<span data-ttu-id="501c3-103">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="501c3-103">Creates the assembly.</span></span> <span data-ttu-id="501c3-104">アセンブリ ファイルを除く他のすべてのファイルが閉じられた後は、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="501c3-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="501c3-105">非バインド モジュールを生成するときに、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="501c3-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="501c3-106">構文</span><span class="sxs-lookup"><span data-stu-id="501c3-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="501c3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="501c3-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="501c3-108">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="501c3-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="501c3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="501c3-109">Return Value</span></span>  
 <span data-ttu-id="501c3-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="501c3-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="501c3-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="501c3-111">Requirements</span></span>  
 <span data-ttu-id="501c3-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="501c3-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501c3-113">参照</span><span class="sxs-lookup"><span data-stu-id="501c3-113">See Also</span></span>  
 [<span data-ttu-id="501c3-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="501c3-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="501c3-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="501c3-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="501c3-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="501c3-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
