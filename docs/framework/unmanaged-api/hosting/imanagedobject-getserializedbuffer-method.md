---
title: IManagedObject::GetSerializedBuffer メソッド
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53e8180fb55336eb05d0737110fd2fe07a4c5894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441602"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="1efbe-102">IManagedObject::GetSerializedBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="1efbe-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="1efbe-103">この管理オブジェクトの文字列形式を取得します。</span><span class="sxs-lookup"><span data-stu-id="1efbe-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1efbe-104">構文</span><span class="sxs-lookup"><span data-stu-id="1efbe-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1efbe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1efbe-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="1efbe-106">[out]シリアル化されたオブジェクトを表す文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1efbe-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1efbe-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1efbe-107">Remarks</span></span>  
 <span data-ttu-id="1efbe-108">`GetSerializedBuffer`メソッドは、クライアントにマーシャ リングするために、オブジェクトをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="1efbe-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1efbe-109">要件</span><span class="sxs-lookup"><span data-stu-id="1efbe-109">Requirements</span></span>  
 <span data-ttu-id="1efbe-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1efbe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1efbe-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1efbe-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1efbe-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1efbe-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1efbe-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1efbe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efbe-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1efbe-114">See Also</span></span>  
 [<span data-ttu-id="1efbe-115">IManagedObject インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1efbe-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
