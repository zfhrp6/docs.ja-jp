---
title: GUID_ManagedName 属性
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bae50f695de81856d4fddcb2af3d1188d896642
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430012"
---
# <a name="guidmanagedname-attribute"></a>GUID_ManagedName 属性
コンポーネント オブジェクト モデル (COM) ライブラリの管理対象名前空間名を指定するカスタム インターフェイス属性を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `value`  
 ライブラリの管理対象名前空間の名前。  
  
## <a name="definition"></a>定義  
 `GUID_ManagedName` 次の定義 Cor.h で。  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>コメント  
 カスタム インターフェイス属性は、タイプ ライブラリのオブジェクトのメタデータを定義します。  
  
 使用して<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType>または<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType>属性から管理対象の名前を取得します。  
  
 詳細については、次を参照してください。[インターフェイス属性](/cpp/windows/interface-attributes)Visual c のドキュメントを参照しています。  
  
## <a name="example"></a>例  
 次の例を使用してライブラリの定義、`GUID_ManagedName`属性。  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** Cor.h
