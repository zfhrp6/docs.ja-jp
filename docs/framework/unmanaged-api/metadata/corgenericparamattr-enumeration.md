---
title: "CorGenericParamAttr 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGenericParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGenericParamAttr
helpviewer_keywords: CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e40613d790baed5bd89bee1e1f5ca57043bfe76a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="5412a-102">CorGenericParamAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="5412a-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="5412a-103">記述する値が含まれています、<xref:System.Type>呼び出しで使用される、ジェネリック型のパラメーター [imetadataemit 2::definegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="5412a-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5412a-104">構文</span><span class="sxs-lookup"><span data-stu-id="5412a-104">Syntax</span></span>  
  
```  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="5412a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="5412a-105">Members</span></span>  
  
|<span data-ttu-id="5412a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5412a-106">Member</span></span>|<span data-ttu-id="5412a-107">説明</span><span class="sxs-lookup"><span data-stu-id="5412a-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="5412a-108">パラメーターの分散は、インターフェイスやデリゲートのジェネリック パラメーターにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5412a-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="5412a-109">差異のないことを示します。</span><span class="sxs-lookup"><span data-stu-id="5412a-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="5412a-110">共分散を示します。</span><span class="sxs-lookup"><span data-stu-id="5412a-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="5412a-111">反変性を示します。</span><span class="sxs-lookup"><span data-stu-id="5412a-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="5412a-112">いずれかに特殊な制約を適用できます<xref:System.Type>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5412a-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="5412a-113">制約が適用されないことを示す、<xref:System.Type>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5412a-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="5412a-114">示します、<xref:System.Type>パラメーターは参照型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5412a-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="5412a-115">示します、<xref:System.Type>パラメーターが null 値を指定できません値の型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5412a-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="5412a-116">示します、<xref:System.Type>パラメーターがパラメーターを受け取らない既定パブリック コンス トラクターを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="5412a-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5412a-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="5412a-117">Requirements</span></span>  
 <span data-ttu-id="5412a-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5412a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5412a-119">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5412a-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5412a-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5412a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5412a-121">参照</span><span class="sxs-lookup"><span data-stu-id="5412a-121">See Also</span></span>  
 [<span data-ttu-id="5412a-122">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="5412a-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
