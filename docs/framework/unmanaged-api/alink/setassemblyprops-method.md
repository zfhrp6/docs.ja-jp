---
title: "SetAssemblyProps メソッド"
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
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae13daab0352ad4367c7ad6e06d6c12af23c75bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="502f7-102">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="502f7-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="502f7-103">アセンブリ レベルのプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="502f7-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="502f7-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="502f7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="502f7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="502f7-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="502f7-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="502f7-107">プロパティを定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="502f7-107">File that defines the property.</span></span> <span data-ttu-id="502f7-108">場合、NULL を指定できます`AssemblyID`はバインドされていない netmodule を示しません。</span><span class="sxs-lookup"><span data-stu-id="502f7-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="502f7-109">変更するためのオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="502f7-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="502f7-110">オプションの新しい値。</span><span class="sxs-lookup"><span data-stu-id="502f7-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="502f7-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="502f7-111">Return Value</span></span>  
 <span data-ttu-id="502f7-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="502f7-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="502f7-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="502f7-113">Requirements</span></span>  
 <span data-ttu-id="502f7-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="502f7-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502f7-115">参照</span><span class="sxs-lookup"><span data-stu-id="502f7-115">See Also</span></span>  
 [<span data-ttu-id="502f7-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="502f7-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="502f7-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="502f7-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="502f7-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="502f7-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
