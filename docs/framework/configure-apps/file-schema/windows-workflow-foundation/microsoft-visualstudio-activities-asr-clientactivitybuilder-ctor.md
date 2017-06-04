---
title: "Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor"
apilocation: 
  - "Microsoft.VisualStudio.Activities.dll"
apitype: "Assembly"
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
[Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) クラスのインスタンスを作成します。  
  
## 構文  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
  
```  
  
#### パラメーター  
  
## パラメーター値  
 *operationDescription*  
  
 操作名、戻り値の型、パラメーター情報など、生成されるワークフロー アクティビティで実行される操作を記述します。  このパラメーターの値には **null** を指定しないでください。  これは、メッセージ コントラクトを使用し、1 つのメッセージと共に引数を受け取る同期操作を示す必要があります。  これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。  
  
 *configurationName*  
  
 エンドポイント構成名を指定します。  このパラメーターの値は **null** または空にしないでください。  これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。  
  
 *proxyNamespace*  
  
 操作のサービスの名前空間を指定します。  このパラメーターの値は **null** または空にしないでください。  これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。  
  
## 参照  
 [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)