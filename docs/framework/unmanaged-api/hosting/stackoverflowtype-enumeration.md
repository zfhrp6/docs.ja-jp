---
title: "StackOverflowType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowType
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowType
helpviewer_keywords: StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64312398c95a33c2bbe136b1c4d03c06cb09aeef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="cb7ae-102">StackOverflowType 列挙型</span><span class="sxs-lookup"><span data-stu-id="cb7ae-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="cb7ae-103">スタック オーバーフローのイベントの根本原因を示す値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb7ae-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7ae-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb7ae-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="cb7ae-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb7ae-105">Members</span></span>  
  
|<span data-ttu-id="cb7ae-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb7ae-106">Member</span></span>|<span data-ttu-id="cb7ae-107">説明</span><span class="sxs-lookup"><span data-stu-id="cb7ae-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="cb7ae-108">実行エンジンによって、スタック オーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cb7ae-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="cb7ae-109">マネージ コードによって、スタック オーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cb7ae-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="cb7ae-110">アンマネージ コードによって、スタック オーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cb7ae-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb7ae-111">コメント</span><span class="sxs-lookup"><span data-stu-id="cb7ae-111">Remarks</span></span>  
 <span data-ttu-id="cb7ae-112">この情報を呼び出すことによって、ホストに渡される、 [iactiononclrevent::onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="cb7ae-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb7ae-113">要件</span><span class="sxs-lookup"><span data-stu-id="cb7ae-113">Requirements</span></span>  
 <span data-ttu-id="cb7ae-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb7ae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb7ae-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb7ae-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb7ae-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb7ae-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb7ae-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb7ae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7ae-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb7ae-118">See Also</span></span>  
 [<span data-ttu-id="cb7ae-119">ホスティングの列挙体</span><span class="sxs-lookup"><span data-stu-id="cb7ae-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
