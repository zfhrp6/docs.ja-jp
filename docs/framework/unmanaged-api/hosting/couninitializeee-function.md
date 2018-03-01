---
title: "CoUninitializeEE 関数"
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
- CoUninitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4125a76ae50a293e35e326f775500c06120420d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="couninitializeee-function"></a><span data-ttu-id="d4be5-102">CoUninitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="d4be5-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="d4be5-103">`CoUninitializeEE`廃止されており機能は備えていません。</span><span class="sxs-lookup"><span data-stu-id="d4be5-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4be5-104">構文</span><span class="sxs-lookup"><span data-stu-id="d4be5-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d4be5-105">コメント</span><span class="sxs-lookup"><span data-stu-id="d4be5-105">Remarks</span></span>  
 <span data-ttu-id="d4be5-106">共通言語ランタイムの実行エンジンは、プロセスからアンロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d4be5-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="d4be5-107">実行エンジンの呼び出しをシャット ダウン[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4be5-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4be5-108">参照</span><span class="sxs-lookup"><span data-stu-id="d4be5-108">See Also</span></span>  
 [<span data-ttu-id="d4be5-109">CoInitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="d4be5-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="d4be5-110">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="d4be5-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
