---
title: "CoUninitializeCor 関数"
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
- CoUninitializeCor
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b9f50892b44cf8ce22cc126fe22323c8b0bbe6be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="couninitializecor-function"></a><span data-ttu-id="ce104-102">CoUninitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="ce104-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="ce104-103">`CoUninitializeCor` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="ce104-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce104-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce104-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce104-105">コメント</span><span class="sxs-lookup"><span data-stu-id="ce104-105">Remarks</span></span>  
 <span data-ttu-id="ce104-106">共通言語ランタイムは、プロセスからアンロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce104-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="ce104-107">実行中のプロセスからランタイムを完全に削除するには、そのプロセスをシャット ダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce104-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce104-108">参照</span><span class="sxs-lookup"><span data-stu-id="ce104-108">See Also</span></span>  
 [<span data-ttu-id="ce104-109">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="ce104-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
