---
title: "BucketParameters 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: BucketParameters
api_location: mscoree.dll
api_type: COM
f1_keywords: BucketParameters
helpviewer_keywords: BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7626ce6b2b6278be7cd9989718c13f7c98e4ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="0b9ef-102">BucketParameters 構造体</span><span class="sxs-lookup"><span data-stu-id="0b9ef-102">BucketParameters Structure</span></span>
<span data-ttu-id="0b9ef-103">現在の例外イベントに関連付けられているイベントと、パラメーターの型名を格納します。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b9ef-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b9ef-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="0b9ef-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="0b9ef-105">Members</span></span>  
  
|<span data-ttu-id="0b9ef-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0b9ef-106">Member</span></span>|<span data-ttu-id="0b9ef-107">説明</span><span class="sxs-lookup"><span data-stu-id="0b9ef-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="0b9ef-108">`true`、この構造体の残りの部分が無効である場合それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="0b9ef-109">イベントの種類の名前です。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="0b9ef-110">現在の例外イベントに関連付けられているパラメーターを指定の文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b9ef-111">要件</span><span class="sxs-lookup"><span data-stu-id="0b9ef-111">Requirements</span></span>  
 <span data-ttu-id="0b9ef-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b9ef-113">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="0b9ef-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0b9ef-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b9ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b9ef-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b9ef-115">See Also</span></span>  
 [<span data-ttu-id="0b9ef-116">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="0b9ef-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
