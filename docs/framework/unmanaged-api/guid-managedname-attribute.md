---
title: "GUID_ManagedName 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "GUID_ManagedName"
apilocation: 
  - "alink.dll"
apitype: "COM"
f1_keywords: 
  - "GUID_ManagedName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GUID_ManagedName 属性"
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# GUID_ManagedName 属性
コンポーネント オブジェクト モデル \(COM\) ライブラリの管理対象名前空間名を指定するカスタム インターフェイス属性を定義します。  
  
## 構文  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### パラメーター  
 `value`  
 ライブラリの管理対象名前空間の名前。  
  
## 定義  
 `GUID_ManagedName` Cor.h のように定義されています。  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## 解説  
 カスタム インターフェイス属性は、タイプ ライブラリ内のオブジェクトのメタデータを定義します。  
  
 使用 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=fullName> または <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=fullName> 属性から管理対象の名前を取得します。  
  
 詳細については、次を参照してください。 [Interface Attributes](../Topic/Interface%20Attributes.md) Visual c での説明を参照します。  
  
## 使用例  
 次の例を使用してライブラリ定義、 `GUID_ManagedName` 属性です。  
  
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
  
## 必要条件  
 **ヘッダー:** Cor.h