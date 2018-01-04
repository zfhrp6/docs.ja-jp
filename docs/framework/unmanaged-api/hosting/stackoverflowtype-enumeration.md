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
ms.workload: dotnet
ms.openlocfilehash: a04db61a16aeae24476fb0b191a3d2dc89743dee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="5dae9-102">StackOverflowType 列挙型</span><span class="sxs-lookup"><span data-stu-id="5dae9-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="5dae9-103">スタック オーバーフローのイベントの根本原因を示す値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5dae9-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dae9-104">構文</span><span class="sxs-lookup"><span data-stu-id="5dae9-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="5dae9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="5dae9-105">Members</span></span>  
  
|<span data-ttu-id="5dae9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5dae9-106">Member</span></span>|<span data-ttu-id="5dae9-107">説明</span><span class="sxs-lookup"><span data-stu-id="5dae9-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="5dae9-108">実行エンジンによって、スタック オーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5dae9-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="5dae9-109">マネージ コードによって、スタック オーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5dae9-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="5dae9-110">アンマネージ コードによって、スタック オーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5dae9-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dae9-111">コメント</span><span class="sxs-lookup"><span data-stu-id="5dae9-111">Remarks</span></span>  
 <span data-ttu-id="5dae9-112">この情報を呼び出すことによって、ホストに渡される、 [iactiononclrevent::onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5dae9-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dae9-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="5dae9-113">Requirements</span></span>  
 <span data-ttu-id="5dae9-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dae9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dae9-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5dae9-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5dae9-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5dae9-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5dae9-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dae9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dae9-118">参照</span><span class="sxs-lookup"><span data-stu-id="5dae9-118">See Also</span></span>  
 [<span data-ttu-id="5dae9-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="5dae9-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
