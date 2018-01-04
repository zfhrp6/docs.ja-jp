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
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列挙型
記述する値が含まれています、<xref:System.Type>呼び出しで使用される、ジェネリック型のパラメーター [imetadataemit 2::definegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)です。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`gpVarianceMask`|パラメーターの分散は、インターフェイスやデリゲートのジェネリック パラメーターにのみ適用されます。|  
|`gpNonVariant`|差異のないことを示します。|  
|`gpCovariant`|共分散を示します。|  
|`gpContravariant`|反変性を示します。|  
|`gpSpecialConstraintMask`|いずれかに特殊な制約を適用できます<xref:System.Type>パラメーター。|  
|`gpNoSpecialConstraint`|制約が適用されないことを示す、<xref:System.Type>パラメーター。|  
|`gpReferenceTypeConstraint`|示します、<xref:System.Type>パラメーターは参照型である必要があります。|  
|`gpNotNullableValueTypeConstraint`|示します、<xref:System.Type>パラメーターが null 値を指定できません値の型にする必要があります。|  
|`gpDefaultConstructorConstraint`|示します、<xref:System.Type>パラメーターがパラメーターを受け取らない既定パブリック コンス トラクターを持つ必要があります。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
