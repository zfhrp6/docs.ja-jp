---
title: "SetAssemblyProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0245b6b1e30174bb3496d3d6ab674ccc00fb9fee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="ec016-102">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="ec016-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="ec016-103">アセンブリ レベルのプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ec016-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec016-104">構文</span><span class="sxs-lookup"><span data-stu-id="ec016-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec016-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec016-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ec016-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="ec016-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ec016-107">プロパティを定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="ec016-107">File that defines the property.</span></span> <span data-ttu-id="ec016-108">場合、NULL を指定できます`AssemblyID`はバインドされていない netmodule を示しません。</span><span class="sxs-lookup"><span data-stu-id="ec016-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="ec016-109">変更するためのオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="ec016-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="ec016-110">オプションの新しい値。</span><span class="sxs-lookup"><span data-stu-id="ec016-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec016-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ec016-111">Return Value</span></span>  
 <span data-ttu-id="ec016-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="ec016-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec016-113">要件</span><span class="sxs-lookup"><span data-stu-id="ec016-113">Requirements</span></span>  
 <span data-ttu-id="ec016-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="ec016-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec016-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec016-115">See Also</span></span>  
 [<span data-ttu-id="ec016-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec016-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ec016-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec016-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ec016-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="ec016-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
