---
title: "CorSerializationType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSerializationType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSerializationType
helpviewer_keywords: CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f6650298364f7deb60d553ee21f5028f5cbe7400
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType 列挙型
共通言語ランタイムによってオブジェクトをシリアル化する方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|オブジェクトのシリアル化が定義されていません。|  
|`SERIALIZATION_TYPE_BOOLEAN`|ブール型としてオブジェクトをシリアル化します。|  
|`SERIALIZATION_TYPE_CHAR`|オブジェクトは、文字型としてシリアル化します。|  
|`SERIALIZATION_TYPE_I1`|オブジェクトは、1 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U1`|オブジェクトは 1 バイトの符号なし整数としてシリアル化されます。|  
|`SERIALIZATION_TYPE_I2`|オブジェクトは、2 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U2`|オブジェクトは 2 バイトの符号なし整数としてシリアル化されます。|  
|`SERIALIZATION_TYPE_I4`|オブジェクトは、4 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U4`|オブジェクトは、4 バイトの符号なし整数としてシリアル化されます。|  
|`SERIALIZATION_TYPE_I8`|オブジェクトは、8 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U8`|オブジェクトは 8 バイトの符号なし整数としてシリアル化されます。|  
|`SERIALIZATION_TYPE_R4`|オブジェクトは、4 バイト浮動小数点としてシリアル化します。|  
|`SERIALIZATION_TYPE_R8`|オブジェクトは、8 バイト浮動小数点としてシリアル化します。|  
|`SERIALIZATION_TYPE_STRING`|オブジェクトは、System.String 型としてシリアル化します。|  
|`SERIALIZATION_TYPE_SZARRAY`|オブジェクトは、1 次元、としてシリアル化 0 下限値の配列。|  
|`SERIALIZATION_TYPE_TYPE`|オブジェクトは、ジェネリック型としてシリアル化します。|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|オブジェクトは、タグが付けられたオブジェクトとしてシリアル化します。|  
|`SERIALIZATION_TYPE_FIELD`|オブジェクトは、フィールドとしてシリアル化します。|  
|`SERIALIZATION_TYPE_PROPERTY`|オブジェクトのプロパティとしてシリアル化します。|  
|`SERIALIZATION_TYPE_ENUM`|オブジェクトの列挙体としてシリアル化します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
