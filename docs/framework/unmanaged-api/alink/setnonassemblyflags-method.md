---
title: SetNonAssemblyFlags メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0399a135eddfd87342db63e107c8eea59a6e54d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401704"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="546a3-102">SetNonAssemblyFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="546a3-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="546a3-103">アセンブリに固有でないフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="546a3-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="546a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="546a3-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="546a3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="546a3-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="546a3-106">ALink フラグです。</span><span class="sxs-lookup"><span data-stu-id="546a3-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="546a3-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="546a3-107">Return Value</span></span>  
 <span data-ttu-id="546a3-108">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="546a3-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="546a3-109">要件</span><span class="sxs-lookup"><span data-stu-id="546a3-109">Requirements</span></span>  
 <span data-ttu-id="546a3-110">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="546a3-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546a3-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="546a3-111">See Also</span></span>  
 [<span data-ttu-id="546a3-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="546a3-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="546a3-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="546a3-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="546a3-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="546a3-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
