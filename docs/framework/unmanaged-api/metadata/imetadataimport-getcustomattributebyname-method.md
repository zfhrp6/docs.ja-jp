---
title: "IMetaDataImport::GetCustomAttributeByName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d234a58d95203a26e8b1cab2cb936e6ee50c2fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="63190-102">IMetaDataImport::GetCustomAttributeByName メソッド</span><span class="sxs-lookup"><span data-stu-id="63190-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="63190-103">その名前と所有者を指定、カスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="63190-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63190-104">構文</span><span class="sxs-lookup"><span data-stu-id="63190-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63190-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63190-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="63190-106">[in]カスタム属性を所有するオブジェクトを表すメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="63190-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="63190-107">[in]カスタム属性の名前です。</span><span class="sxs-lookup"><span data-stu-id="63190-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="63190-108">[out]カスタム属性の値であるデータの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="63190-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="63190-109">[out]返されるデータのバイト サイズ *`ppData`です。</span><span class="sxs-lookup"><span data-stu-id="63190-109">[out] The size in bytes of the data returned in *`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63190-110">コメント</span><span class="sxs-lookup"><span data-stu-id="63190-110">Remarks</span></span>  
 <span data-ttu-id="63190-111">所有者が同じ複数のカスタム属性を定義するには同じ名前があってもあります。</span><span class="sxs-lookup"><span data-stu-id="63190-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="63190-112">ただし、`GetCustomAttributeByName`インスタンス 1 つだけを返します。</span><span class="sxs-lookup"><span data-stu-id="63190-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="63190-113">(`GetCustomAttributeByName`を検出した最初のインスタンスが返されます)。カスタム属性のすべてのインスタンスを検索するには、呼び出し、 [imetadataimport::enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="63190-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63190-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="63190-114">Requirements</span></span>  
 <span data-ttu-id="63190-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="63190-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63190-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="63190-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63190-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="63190-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63190-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63190-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63190-119">参照</span><span class="sxs-lookup"><span data-stu-id="63190-119">See Also</span></span>  
 [<span data-ttu-id="63190-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63190-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="63190-121">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63190-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
