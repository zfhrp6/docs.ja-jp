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
ms.openlocfilehash: f354058e0de944bbce9d128d3f4baa9b941fda08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="5eaf5-102">EmitInternalExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="5eaf5-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="5eaf5-103">アセンブリに追加された型を出力します。</span><span class="sxs-lookup"><span data-stu-id="5eaf5-103">Emits types added to the assembly.</span></span> <span data-ttu-id="5eaf5-104">既知の内部型が追加された後は、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5eaf5-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eaf5-105">構文</span><span class="sxs-lookup"><span data-stu-id="5eaf5-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5eaf5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5eaf5-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5eaf5-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="5eaf5-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5eaf5-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5eaf5-108">Return Value</span></span>  
 <span data-ttu-id="5eaf5-109">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="5eaf5-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eaf5-110">要件</span><span class="sxs-lookup"><span data-stu-id="5eaf5-110">Requirements</span></span>  
 <span data-ttu-id="5eaf5-111">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="5eaf5-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eaf5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5eaf5-112">See Also</span></span>  
 [<span data-ttu-id="5eaf5-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5eaf5-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5eaf5-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5eaf5-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5eaf5-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="5eaf5-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
