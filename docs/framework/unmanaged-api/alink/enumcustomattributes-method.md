---
title: "EnumCustomAttributes メソッド"
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
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d616babb47ac0282ef56d119ab448a94fd24c7c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="05fa5-102">EnumCustomAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="05fa5-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="05fa5-103">アセンブリ レベルのカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="05fa5-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05fa5-104">構文</span><span class="sxs-lookup"><span data-stu-id="05fa5-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05fa5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05fa5-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="05fa5-106">列挙子のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="05fa5-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="05fa5-107">列挙する属性の型。</span><span class="sxs-lookup"><span data-stu-id="05fa5-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="05fa5-108">使用して`mdTokenNill`すべての属性です。</span><span class="sxs-lookup"><span data-stu-id="05fa5-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="05fa5-109">カスタム属性のトークンを受信します。</span><span class="sxs-lookup"><span data-stu-id="05fa5-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="05fa5-110">サイズを指定`rCustomValues`配列。</span><span class="sxs-lookup"><span data-stu-id="05fa5-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="05fa5-111">必要に応じてトークンの値の数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="05fa5-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05fa5-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="05fa5-112">Return Value</span></span>  
 <span data-ttu-id="05fa5-113">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="05fa5-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05fa5-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="05fa5-114">Requirements</span></span>  
 <span data-ttu-id="05fa5-115">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="05fa5-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fa5-116">参照</span><span class="sxs-lookup"><span data-stu-id="05fa5-116">See Also</span></span>  
 [<span data-ttu-id="05fa5-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05fa5-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="05fa5-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05fa5-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="05fa5-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="05fa5-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
