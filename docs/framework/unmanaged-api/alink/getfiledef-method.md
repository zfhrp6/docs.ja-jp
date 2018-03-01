---
title: "GetFileDef メソッド"
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
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 473cbaba8712ee247733ba3075c0163e259cf4dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="1c65a-102">GetFileDef メソッド</span><span class="sxs-lookup"><span data-stu-id="1c65a-102">GetFileDef Method</span></span>
<span data-ttu-id="1c65a-103">(ALink によって割り当てられたトークン) ではなくメタデータで使用される実際の FileDef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1c65a-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c65a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1c65a-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c65a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c65a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1c65a-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="1c65a-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="1c65a-107">追加されたファイルのトークン AddFile メソッドまたは AddImport メソッドから取得します。</span><span class="sxs-lookup"><span data-stu-id="1c65a-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="1c65a-108">FileDef トークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1c65a-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c65a-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="1c65a-109">Return Value</span></span>  
 <span data-ttu-id="1c65a-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="1c65a-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c65a-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="1c65a-111">Requirements</span></span>  
 <span data-ttu-id="1c65a-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="1c65a-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c65a-113">参照</span><span class="sxs-lookup"><span data-stu-id="1c65a-113">See Also</span></span>  
 [<span data-ttu-id="1c65a-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c65a-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1c65a-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c65a-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1c65a-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="1c65a-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
