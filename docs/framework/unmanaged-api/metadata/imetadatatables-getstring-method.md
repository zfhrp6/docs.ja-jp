---
title: "IMetaDataTables::GetString メソッド"
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
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c2c0df58d1de7cc7c1eedfdea6c0e698cbd9cb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="df20a-102">IMetaDataTables::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="df20a-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="df20a-103">現在参照スコープ内のテーブル列から、指定したインデックス位置文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="df20a-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df20a-104">構文</span><span class="sxs-lookup"><span data-stu-id="df20a-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df20a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df20a-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="df20a-106">[in]次の値の検索を開始する位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="df20a-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="df20a-107">[out]返される文字列値へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="df20a-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df20a-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="df20a-108">Requirements</span></span>  
 <span data-ttu-id="df20a-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="df20a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df20a-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df20a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df20a-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="df20a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df20a-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df20a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df20a-113">参照</span><span class="sxs-lookup"><span data-stu-id="df20a-113">See Also</span></span>  
 [<span data-ttu-id="df20a-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df20a-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="df20a-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df20a-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
