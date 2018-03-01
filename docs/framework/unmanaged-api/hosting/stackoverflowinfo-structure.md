---
title: "StackOverflowInfo 構造体"
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
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 12a880a7c30277d382bff2b46ebe10720880e907
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="d61b0-102">StackOverflowInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="d61b0-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="d61b0-103">スローされた例外をオーバーフローが原因でオーバーフローが発生しましたが、情報の種類を格納します。</span><span class="sxs-lookup"><span data-stu-id="d61b0-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d61b0-104">構文</span><span class="sxs-lookup"><span data-stu-id="d61b0-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="d61b0-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d61b0-105">Members</span></span>  
  
|<span data-ttu-id="d61b0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d61b0-106">Member</span></span>|<span data-ttu-id="d61b0-107">説明</span><span class="sxs-lookup"><span data-stu-id="d61b0-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="d61b0-108">値、 [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)オーバーフローの種類を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="d61b0-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="d61b0-109">Win32 へのポインター`EXCEPTION_POINTERS`例外のマシンに依存しない説明を含む例外レコードと時、例外のプロセッサ コンテキストのコンピューターに依存する説明を含むコンテキスト レコードを含むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d61b0-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d61b0-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d61b0-110">Remarks</span></span>  
 <span data-ttu-id="d61b0-111">A`StackOverflowInfo`にオブジェクトが渡される、 [iactiononclrevent::onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)メソッド`Event_StackOverflow`イベント。</span><span class="sxs-lookup"><span data-stu-id="d61b0-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d61b0-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="d61b0-112">Requirements</span></span>  
 <span data-ttu-id="d61b0-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d61b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d61b0-114">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d61b0-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d61b0-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d61b0-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d61b0-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d61b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d61b0-117">参照</span><span class="sxs-lookup"><span data-stu-id="d61b0-117">See Also</span></span>  
 [<span data-ttu-id="d61b0-118">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="d61b0-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
