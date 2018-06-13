---
title: CoUninitializeCor 関数
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 305a8d7b5a800c46ed814b1e654947859dc9bd03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427812"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="6b369-102">CoUninitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="6b369-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="6b369-103">`CoUninitializeCor` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="6b369-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b369-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b369-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b369-105">コメント</span><span class="sxs-lookup"><span data-stu-id="6b369-105">Remarks</span></span>  
 <span data-ttu-id="6b369-106">共通言語ランタイムは、プロセスからアンロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6b369-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="6b369-107">実行中のプロセスからランタイムを完全に削除するには、そのプロセスをシャット ダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b369-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b369-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b369-108">See Also</span></span>  
 [<span data-ttu-id="6b369-109">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="6b369-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
