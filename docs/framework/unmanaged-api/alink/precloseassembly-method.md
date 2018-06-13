---
title: PreCloseAssembly メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82421fa83a6f0d24492d70f961e731b679c25728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400719"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="33925-102">PreCloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="33925-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="33925-103">アセンブリ ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="33925-103">Closes the assembly file.</span></span> <span data-ttu-id="33925-104">閉じると、その他のすべてのファイルがアセンブリ ファイルを閉じる前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="33925-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="33925-105">非バインド モジュールのこのメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="33925-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33925-106">構文</span><span class="sxs-lookup"><span data-stu-id="33925-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33925-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33925-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="33925-108">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="33925-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33925-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="33925-109">Return Value</span></span>  
 <span data-ttu-id="33925-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="33925-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33925-111">要件</span><span class="sxs-lookup"><span data-stu-id="33925-111">Requirements</span></span>  
 <span data-ttu-id="33925-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="33925-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33925-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="33925-113">See Also</span></span>  
 [<span data-ttu-id="33925-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33925-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="33925-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33925-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="33925-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="33925-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
