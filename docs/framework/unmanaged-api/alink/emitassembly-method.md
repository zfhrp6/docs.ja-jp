---
title: "EmitAssembly メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssembly
helpviewer_keywords: EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3471c4ad2d06443e0f05dc344be5f791817f2d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="c62c4-102">EmitAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="c62c4-102">EmitAssembly Method</span></span>
<span data-ttu-id="c62c4-103">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c62c4-103">Creates the assembly.</span></span> <span data-ttu-id="c62c4-104">アセンブリ ファイルを除く他のすべてのファイルが閉じられた後は、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c62c4-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="c62c4-105">非バインド モジュールを生成するときに、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="c62c4-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c62c4-106">構文</span><span class="sxs-lookup"><span data-stu-id="c62c4-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c62c4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c62c4-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c62c4-108">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="c62c4-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c62c4-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c62c4-109">Return Value</span></span>  
 <span data-ttu-id="c62c4-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="c62c4-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c62c4-111">要件</span><span class="sxs-lookup"><span data-stu-id="c62c4-111">Requirements</span></span>  
 <span data-ttu-id="c62c4-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="c62c4-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62c4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c62c4-113">See Also</span></span>  
 [<span data-ttu-id="c62c4-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c62c4-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c62c4-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c62c4-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c62c4-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="c62c4-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
