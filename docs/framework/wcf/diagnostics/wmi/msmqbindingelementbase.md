---
title: "MsmqBindingElementBase | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# MsmqBindingElementBase
MsmqBindingElementBase  
  
## 構文  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## メソッド  
 MsmqBindingElementBase クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 MsmqBindingElementBase クラスには、次のプロパティがあります。  
  
### CustomDeadLetterQueue  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 アプリケーションごとの配信不能キューの場所が含まれている URI です。ここには、期限切れのメッセージや、転送または配信に失敗したメッセージが配置されます。  
  
### DeadLetterQueue  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 使用する配信不能キューの型を示す列挙型の値です。  
  
### Durable  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングによって処理されるメッセージが永続的なものか不安定なものかを示す値です。  
  
### ExactlyOnce  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングで処理されるメッセージが正確に 1 回だけ受信されるかどうかを示すブール値です。  
  
### MaxRetryCycles  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 受信アプリケーションにメッセージを配信する再試行サイクルの最大数です。  
  
### ReceiveErrorHandling  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 有害メッセージの処理の設定です。  
  
### ReceiveRetryCount  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 アプリケーション キューから読み取られるメッセージの即時再試行の最大回数です。  
  
### RetryCycleDelay  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 すぐに配信できなかったメッセージを配信しようとするときの、再試行サイクルの時間遅延を示す値です。  
  
### TimeToLive  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングで処理されるメッセージの期限が切れるまで、メッセージをキュー内で保持する時間です。  
  
### UseMsmqTracing  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングにより処理されるメッセージをトレースするかどうかを示すブール値です。  
  
### UseSourceJournal  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングにより処理されるメッセージのコピーをソース ジャーナル キューに保存するかどうかを示すブール値です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.NetMsmqBinding>   
 <xref:System.ServiceModel.MsmqBindingBase>