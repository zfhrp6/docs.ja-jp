---
title: IReferenceIdentity インターフェイス
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432104"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="a711e-102">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a711e-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="a711e-103">コード オブジェクトの一意のシグネチャへの参照を表します。</span><span class="sxs-lookup"><span data-stu-id="a711e-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a711e-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a711e-104">Methods</span></span>  
  
|<span data-ttu-id="a711e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a711e-105">Method</span></span>|<span data-ttu-id="a711e-106">説明</span><span class="sxs-lookup"><span data-stu-id="a711e-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="a711e-107">新しいインターフェイス ポインターを取得`IReferenceIdentity`これと同じであるインスタンス`IReferenceIdentity`、指定した属性の変更を除きです。</span><span class="sxs-lookup"><span data-stu-id="a711e-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="a711e-108">インターフェイス ポインターを取得、`IEnumIDENTITY_ATTRIBUTE`インスタンスに関連付けられた属性を含む`IReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="a711e-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="a711e-109">指定した名前空間の指定した名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a711e-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="a711e-110">指定した名前空間と、指定された値を指定した名前を持つ属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="a711e-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a711e-111">要件</span><span class="sxs-lookup"><span data-stu-id="a711e-111">Requirements</span></span>  
 <span data-ttu-id="a711e-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a711e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a711e-113">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a711e-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a711e-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a711e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a711e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a711e-115">See Also</span></span>  
 [<span data-ttu-id="a711e-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a711e-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="a711e-117">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a711e-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
