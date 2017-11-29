---
title: "PreCloseAssembly メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.PreCloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: PreCloseAssembly
helpviewer_keywords: PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d940cbdeddc7030c679fae8c8694bb3542123b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="81ca4-102">PreCloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="81ca4-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="81ca4-103">アセンブリ ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="81ca4-103">Closes the assembly file.</span></span> <span data-ttu-id="81ca4-104">閉じると、その他のすべてのファイルがアセンブリ ファイルを閉じる前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="81ca4-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="81ca4-105">非バインド モジュールのこのメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="81ca4-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ca4-106">構文</span><span class="sxs-lookup"><span data-stu-id="81ca4-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81ca4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81ca4-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="81ca4-108">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="81ca4-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81ca4-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="81ca4-109">Return Value</span></span>  
 <span data-ttu-id="81ca4-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="81ca4-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81ca4-111">要件</span><span class="sxs-lookup"><span data-stu-id="81ca4-111">Requirements</span></span>  
 <span data-ttu-id="81ca4-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="81ca4-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ca4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="81ca4-113">See Also</span></span>  
 [<span data-ttu-id="81ca4-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81ca4-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="81ca4-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81ca4-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="81ca4-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="81ca4-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
