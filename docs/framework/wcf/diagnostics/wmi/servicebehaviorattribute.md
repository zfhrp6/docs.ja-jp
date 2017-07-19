---
title: "ServiceBehaviorAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## 構文  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## メソッド  
 ServiceBehaviorAttribute クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ServiceBehaviorAttribute クラスには、次のプロパティがあります。  
  
### AutomaticSessionShutdown  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 クライアントが出力セッションを閉じるときにセッションを自動的に閉じるかどうかを示します。  
  
### ConcurrencyMode  
 データ型: string  
アクセスの種類 : 読み取り専用  
  
 サービスで、1 つのスレッド、複数のスレッド、または再入呼び出しをサポートするかどうかを示します。  
  
### ConfigurationName  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サービス構成の名前。  
  
### IgnoreExtensionDataObject  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 不明なシリアル化データをネットワークで送信するかどうかを指定します。  
  
### IncludeExceptionDetailInFaults  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージ例外情報を含めるかどうかを指定します。  
  
### InstanceContextMode  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 新しいサービス オブジェクトを作成するタイミングを指定します。  
  
### MaxItemsInObjectGraph  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 1 つのシリアル化されたオブジェクトで許可される項目の最大数。  
  
### Name  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 WSDL でのサービスの名前属性。  
  
### 名前空間  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 WSDL でのサービスのターゲット名前空間。  
  
### ReleaseServiceInstanceOnTransactionComplete  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 現在のトランザクションの完了時に、サービス オブジェクトをリサイクルするかどうかを指定します。  
  
### TransactionAutoCompleteOnSessionClose  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 現在のセッションの終了時に、保留中のトランザクションを完了するかどうかを指定します。  
  
### TransactionIsolationLevel  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 トランザクションの分離レベルを指定します。  
  
### TransactionTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 トランザクションを完了しなければならない期間。  
  
### UseSynchronizationContext  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 現在の同期コンテキストを使用してスレッドの実行を選択するかどうかを指定します。  
  
### ValidateMustUnderstand  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>