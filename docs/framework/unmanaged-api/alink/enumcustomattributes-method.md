---
title: "EnumCustomAttributes メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location: alink.dll
api_type: COM
f1_keywords: EnumCustomAttributes
helpviewer_keywords: EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: febaba5155753e9d60a3708582f4f58bd7861ec7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="5ee3b-102">EnumCustomAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="5ee3b-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="5ee3b-103">アセンブリ レベルのカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee3b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ee3b-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ee3b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ee3b-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="5ee3b-106">列挙子のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="5ee3b-107">列挙する属性の型。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="5ee3b-108">使用して`mdTokenNill`すべての属性です。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="5ee3b-109">カスタム属性のトークンを受信します。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5ee3b-110">サイズを指定`rCustomValues`配列。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="5ee3b-111">必要に応じてトークンの値の数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ee3b-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5ee3b-112">Return Value</span></span>  
 <span data-ttu-id="5ee3b-113">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee3b-114">要件</span><span class="sxs-lookup"><span data-stu-id="5ee3b-114">Requirements</span></span>  
 <span data-ttu-id="5ee3b-115">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="5ee3b-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee3b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ee3b-116">See Also</span></span>  
 [<span data-ttu-id="5ee3b-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ee3b-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5ee3b-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ee3b-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5ee3b-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="5ee3b-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
