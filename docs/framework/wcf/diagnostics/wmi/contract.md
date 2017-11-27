---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e92c5d804fca3c04506e951a5c341c89eed1c54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="contract"></a>コントラクト
コントラクト  
  
## <a name="syntax"></a>構文  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>メソッド  
 Contract クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 Contract クラスには、次のプロパティがあります。  
  
### <a name="appdomainid"></a>AppDomainId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトをホストする appdomain の appdomain ID。  
  
### <a name="behaviors"></a>ビヘイビアー  
 データ型 : Behavior array  
  
 アクセスの種類 : 読み取り専用  
  
 このコントラクトに関連付けられている動作。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 WSDL でのコントラクトの名前。  
  
### <a name="namespace"></a>名前空間  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 WSDL での `portType` 要素の名前空間。  
  
### <a name="operations"></a>操作  
 データ型 : Operation 配列  
  
 アクセスの種類 : 読み取り専用  
  
 このコントラクトの操作。  
  
### <a name="processid"></a>ProcessId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトをホストするプロセスのプロセス ID。  
  
### <a name="ref"></a>ref  
 データ型 : Contract  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトが双方向コントラクトのときのコールバックの型。  
  
### <a name="sessionmode"></a>SessionMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトでチャネル セッションを使用するために、このコントラクトに関連付けられたバインディングが必要かどうかを示します。  
  
### <a name="type"></a>型  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトの型。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.ContractDescription>
