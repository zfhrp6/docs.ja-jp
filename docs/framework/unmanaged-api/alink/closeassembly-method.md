---
title: CloseAssembly メソッド
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68698aab0fd0872c6e6f67e4ec531ab0226e784f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401954"
---
# <a name="closeassembly-method"></a><span data-ttu-id="0f6da-102">CloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="0f6da-102">CloseAssembly Method</span></span>
<span data-ttu-id="0f6da-103">アセンブリの操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="0f6da-103">Finalizes assembly operations.</span></span> <span data-ttu-id="0f6da-104">新しいアセンブリまたは非バインド モジュールを開始する前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0f6da-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f6da-105">構文</span><span class="sxs-lookup"><span data-stu-id="0f6da-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f6da-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f6da-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0f6da-107">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="0f6da-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f6da-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f6da-108">Return Value</span></span>  
 <span data-ttu-id="0f6da-109">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="0f6da-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f6da-110">要件</span><span class="sxs-lookup"><span data-stu-id="0f6da-110">Requirements</span></span>  
 <span data-ttu-id="0f6da-111">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="0f6da-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f6da-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f6da-112">See Also</span></span>  
 [<span data-ttu-id="0f6da-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f6da-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0f6da-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f6da-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0f6da-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="0f6da-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
