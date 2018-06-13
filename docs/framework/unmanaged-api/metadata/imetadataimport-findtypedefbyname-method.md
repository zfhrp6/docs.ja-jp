---
title: IMetaDataImport::FindTypeDefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b4aad1cf1d3eb2dec249686f2897e6f393ab7e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445479"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="53254-102">IMetaDataImport::FindTypeDefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="53254-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="53254-103">トークンの TypeDef メタデータへのポインターを取得、<xref:System.Type>指定した名前です。</span><span class="sxs-lookup"><span data-stu-id="53254-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53254-104">構文</span><span class="sxs-lookup"><span data-stu-id="53254-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53254-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="53254-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="53254-106">[in]TypeDef トークンを取得する対象の型の名前。</span><span class="sxs-lookup"><span data-stu-id="53254-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="53254-107">[in]外側のクラスを表す TypeDef または TypeRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="53254-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="53254-108">検索する型が入れ子になったクラスでない場合は、この値を NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="53254-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="53254-109">[out]一致する TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="53254-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53254-110">要件</span><span class="sxs-lookup"><span data-stu-id="53254-110">Requirements</span></span>  
 <span data-ttu-id="53254-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="53254-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53254-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53254-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53254-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="53254-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53254-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53254-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53254-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="53254-115">See Also</span></span>  
 [<span data-ttu-id="53254-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53254-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="53254-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53254-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
