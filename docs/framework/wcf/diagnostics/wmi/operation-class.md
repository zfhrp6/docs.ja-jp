---
title: "操作クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 操作クラス
Operation  
  
## 構文  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## メソッド  
 Operation クラスで定義されているメソッドはありせん。  
  
## プロパティ  
 Operation クラスには、次のプロパティがあります。  
  
### Action  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 要求メッセージの WS\-Addressing 操作。  
  
### AsyncPattern  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 サービス コントラクトで `Begin` メソッドと `End` メソッドの組み合わせを使用して、操作が非同期的に実装されることを示します。  
  
### Behaviors  
 データ型 : Behavior 配列  
  
 アクセスの種類 : 読み取り専用  
  
 この操作に関連付けられている動作。  
  
### IsCallback  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 この操作がコールバック操作の場合、True。  
  
### IsInitiating  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 メソッドが、サーバーでセッションを開始できる操作を実装するかどうかを指定します。  
  
### IsOneWay  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 操作が応答メッセージを返すかどうかを指定します。  
  
### IsTerminating  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 操作が応答メッセージを返すかどうかを指定します。  
  
### MethodSignature  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 操作のメソッド署名。  
  
### Name  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 操作の名前。  
  
### ParameterTypes  
 データ型 : string 配列  
  
 アクセスの種類 : 読み取り専用  
  
 操作のパラメーターの型。  
  
### ReplyAction  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 操作の応答メッセージの SOAP アクションの値。  
  
### ReturnType  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 操作の戻り値の型。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.OperationDescription>