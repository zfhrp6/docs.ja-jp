---
title: "IReferenceIdentity インターフェイス"
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
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c9696687f292d7dcaa3d430c1e269f0fedb05e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="57124-102">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57124-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="57124-103">コード オブジェクトの一意のシグネチャへの参照を表します。</span><span class="sxs-lookup"><span data-stu-id="57124-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57124-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="57124-104">Methods</span></span>  
  
|<span data-ttu-id="57124-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="57124-105">Method</span></span>|<span data-ttu-id="57124-106">説明</span><span class="sxs-lookup"><span data-stu-id="57124-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="57124-107">新しいインターフェイス ポインターを取得`IReferenceIdentity`これと同じであるインスタンス`IReferenceIdentity`、指定した属性の変更を除きです。</span><span class="sxs-lookup"><span data-stu-id="57124-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="57124-108">インターフェイス ポインターを取得、`IEnumIDENTITY_ATTRIBUTE`インスタンスに関連付けられた属性を含む`IReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="57124-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="57124-109">指定した名前空間の指定した名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="57124-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="57124-110">指定した名前空間と、指定された値を指定した名前を持つ属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="57124-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57124-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="57124-111">Requirements</span></span>  
 <span data-ttu-id="57124-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="57124-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57124-113">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="57124-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="57124-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57124-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57124-115">参照</span><span class="sxs-lookup"><span data-stu-id="57124-115">See Also</span></span>  
 [<span data-ttu-id="57124-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57124-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="57124-117">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57124-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
