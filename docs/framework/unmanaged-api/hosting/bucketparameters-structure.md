---
title: BucketParameters 構造体
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b5e4db8e385baefe3067755bbdc4555c5887ab6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429956"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="a5d6c-102">BucketParameters 構造体</span><span class="sxs-lookup"><span data-stu-id="a5d6c-102">BucketParameters Structure</span></span>
<span data-ttu-id="a5d6c-103">現在の例外イベントに関連付けられているイベントと、パラメーターの型名を格納します。</span><span class="sxs-lookup"><span data-stu-id="a5d6c-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5d6c-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5d6c-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="a5d6c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a5d6c-105">Members</span></span>  
  
|<span data-ttu-id="a5d6c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a5d6c-106">Member</span></span>|<span data-ttu-id="a5d6c-107">説明</span><span class="sxs-lookup"><span data-stu-id="a5d6c-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="a5d6c-108">`true`、この構造体の残りの部分が無効である場合それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="a5d6c-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="a5d6c-109">イベントの種類の名前です。</span><span class="sxs-lookup"><span data-stu-id="a5d6c-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="a5d6c-110">現在の例外イベントに関連付けられているパラメーターを指定の文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="a5d6c-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5d6c-111">要件</span><span class="sxs-lookup"><span data-stu-id="a5d6c-111">Requirements</span></span>  
 <span data-ttu-id="a5d6c-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5d6c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5d6c-113">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="a5d6c-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a5d6c-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5d6c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d6c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5d6c-115">See Also</span></span>  
 [<span data-ttu-id="a5d6c-116">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="a5d6c-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
