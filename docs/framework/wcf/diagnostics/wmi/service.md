---
title: "サービス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# サービス
サービス  
  
## 構文  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## メソッド  
 Service クラスで定義されているメソッドはありません。  
  
## プロパティ  
 Service クラスには次のプロパティがあります。  
  
### BaseAddresses  
 データ型 : string 配列  
  
 アクセスの種類 : 読み取り専用  
  
 サービスによって使用されるベース アドレスです。  
  
### 動作  
 データ型 : Behavior 配列  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスに関連付けられている動作です。  
  
### ConfigurationName  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 ServiceElement\_BehaviorConfiguration  
  
### CounterInstanceName  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。  
  
### DistinguishedName  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 アドレスでのサービス名です。  
  
### Extensions  
 データ型 : string 配列  
  
 アクセスの種類 : 読み取り専用  
  
 サービス インスタンスの拡張に対するインスタンス コンテキストです。  
  
### メタデータ  
 データ型 : string 配列  
  
 アクセスの種類 : 読み取り専用  
  
 サービス メタデータの設定です。  
  
### Name  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスの一意の名前。  
  
### 名前空間  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスの名前空間です。  
  
### Opened  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 サービスが開かれた時刻です。  
  
### OutgoingChannels  
 データ型 : Channel 配列  
  
 アクセスの種類 : 読み取り専用  
  
 サービス インスタンスから送信しているチャネルです。  
  
### ProcessId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 サービスをホストするプロセスのプロセス ID です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|