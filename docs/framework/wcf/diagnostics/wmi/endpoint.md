---
title: "エンドポイント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# エンドポイント
エンドポイント  
  
## 構文  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## メソッド  
 Endpoint クラスは次のメソッドを定義します。  
  
|メソッド|説明|  
|----------|--------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|操作パフォーマンス カウンターのインスタンスの名前を取得します。|  
  
## プロパティ  
 Endpoint クラスには次のプロパティがあります。  
  
### Address  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 エンドポイントのアドレスを格納している URI。  
  
### AddressHeaders  
 データ型 : string array  
  
 アクセスの種類 : 読み取り専用  
  
 このエンドポイントに接続しているアドレス ヘッダーのコレクション  
  
### AddressIdentity  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 エンドポイントの ID  
  
### AppDomainId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 エンドポイントをホストする appdomain の appdomain ID  
  
### ビヘイビアー  
 データ型 : Behavior array  
  
 アクセスの種類 : 読み取り専用  
  
 このエンドポイントが実装する動作のコレクション  
  
### バインディング  
 データ型 : Binding  
  
 アクセスの種類 : 読み取り専用  
  
 このエンドポイントが使用するバインディング  
  
### ContractName  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このエンドポイントが公開するコントラクトを指定する文字列  
  
### CounterInstanceName  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 エンドポイントのパフォーマンス カウンターのインスタンス名  
  
### ListenUri  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 エンドポイントがリッスンする URI  
  
### 名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このエンドポイントの一意の名前  
  
### ProcessId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 エンドポイントをホストするプロセスのプロセス ID  
  
### ref  
 データ型 : Contract  
  
 アクセスの種類 : 読み取り専用  
  
 このエンドポイントが公開しているコントラクト。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|