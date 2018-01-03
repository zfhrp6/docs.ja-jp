---
title: "EmitInternalExportedTypes メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location: alink.dll
api_type: COM
f1_keywords: EmitInternalExportedTypes
helpviewer_keywords: EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48ad5e34b926cf3dab562f57bb9206fa0ba70e6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="6efb8-102">EmitInternalExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="6efb8-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="6efb8-103">アセンブリに追加された型を出力します。</span><span class="sxs-lookup"><span data-stu-id="6efb8-103">Emits types added to the assembly.</span></span> <span data-ttu-id="6efb8-104">既知の内部型が追加された後は、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6efb8-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efb8-105">構文</span><span class="sxs-lookup"><span data-stu-id="6efb8-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6efb8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6efb8-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6efb8-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="6efb8-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6efb8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="6efb8-108">Return Value</span></span>  
 <span data-ttu-id="6efb8-109">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="6efb8-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6efb8-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="6efb8-110">Requirements</span></span>  
 <span data-ttu-id="6efb8-111">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="6efb8-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efb8-112">参照</span><span class="sxs-lookup"><span data-stu-id="6efb8-112">See Also</span></span>  
 [<span data-ttu-id="6efb8-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6efb8-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="6efb8-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6efb8-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6efb8-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="6efb8-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
