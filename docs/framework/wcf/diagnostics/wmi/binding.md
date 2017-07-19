---
title: "バインド | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# バインド
wmi バインディング  
  
## 構文  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## メソッド  
 Binding クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 Binding クラスには、次のプロパティがあります。  
  
### BindingElements  
 データ型 : BindingElement 配列  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングによって実装されるバインド要素のコレクションです。  
  
### CloseTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 クローズ操作が完了するまで待機する時間です。  
  
### Name  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングの名前。  
  
### 名前空間  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングの XML 名前空間。  
  
### OpenTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 オープン操作が完了するまで待機する時間です。  
  
### ReceiveTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 受信操作が完了するまで待機する時間です。  
  
### Scheme  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングに組み込まれているチャネルおよびリスナー ファクトリによって使用される URI トランスポート スキームです。  
  
### SendTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 送信操作が完了するまで待機する時間です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.Binding>