---
title: IReferenceAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2484fa61c03b95e7cbdb452b92a68a2049701374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429518"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="78656-102">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78656-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="78656-103">現在のスコープ内のアプリケーションの一意識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="78656-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78656-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="78656-104">Methods</span></span>  
  
|<span data-ttu-id="78656-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="78656-105">Method</span></span>|<span data-ttu-id="78656-106">説明</span><span class="sxs-lookup"><span data-stu-id="78656-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="78656-107">これによって参照されているアプリケーションのコードの識別子の文字列表記にポインターを取得`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="78656-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="78656-108">これによって参照されているアプリケーションのコードの識別子を設定`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="78656-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="78656-109">インターフェイス ポインターを取得、`IEnumReferenceIdentity`インスタンスを含む、 `IReferenceIdentity` this のメンバーを表すインスタンス`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="78656-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="78656-110">このサブスクリプションのトークンの id の文字列形式へのポインターを取得`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="78656-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="78656-111">このサブスクリプションのトークンの識別子を設定`IReferenceAppId`に指定した文字列値です。</span><span class="sxs-lookup"><span data-stu-id="78656-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78656-112">要件</span><span class="sxs-lookup"><span data-stu-id="78656-112">Requirements</span></span>  
 <span data-ttu-id="78656-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78656-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78656-114">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="78656-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="78656-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78656-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78656-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="78656-116">See Also</span></span>  
 [<span data-ttu-id="78656-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78656-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="78656-118">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78656-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="78656-119">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78656-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
