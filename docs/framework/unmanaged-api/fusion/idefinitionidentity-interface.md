---
title: IDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 401c23e44cc473d0a27a82a00343852693cb0f2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="80466-102">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80466-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="80466-103">現在のスコープで、アプリケーションを定義するコードの一意のシグネチャを表します。</span><span class="sxs-lookup"><span data-stu-id="80466-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80466-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="80466-104">Methods</span></span>  
  
|<span data-ttu-id="80466-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="80466-105">Method</span></span>|<span data-ttu-id="80466-106">説明</span><span class="sxs-lookup"><span data-stu-id="80466-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="80466-107">新しいインターフェイス ポインターを取得`IDefinitionIdentity`これと同じであるオブジェクト`IDefinitionIdentity`、指定した属性の変更を除きです。</span><span class="sxs-lookup"><span data-stu-id="80466-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="80466-108">インターフェイス ポインターを取得、 [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)オブジェクトに関連付けられた属性を含む`IDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="80466-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="80466-109">指定した名前空間内の指定した名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="80466-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="80466-110">指定した値を指定した名前空間で指定した名前を持つ属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="80466-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80466-111">要件</span><span class="sxs-lookup"><span data-stu-id="80466-111">Requirements</span></span>  
 <span data-ttu-id="80466-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="80466-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80466-113">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="80466-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="80466-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80466-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80466-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="80466-115">See Also</span></span>  
 [<span data-ttu-id="80466-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80466-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
