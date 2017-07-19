---
title: "ワークフロー サービス内でのシリアル化の構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# ワークフロー サービス内でのシリアル化の構成
ワークフロー サービスは [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスであるため、<xref:System.Runtime.Serialization.DataContractSerializer> \(既定\) または <xref:System.Xml.Serialization.XmlSerializer> を使用するオプションがあります。ワークフロー以外のサービスを記述する場合、使用するシリアライザーの型はサービスまたは操作コントラクトで指定されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ワークフロー サービスを作成する場合、これらのコントラクトはコードで指定せずに、コントラクト推論で実行時に生成されます。コントラクト推論[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー内でのコントラクトの使用](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)」を参照してください。シリアライザーは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> プロパティを使用して指定されます。これは、次の図に示すようにデザイナーで設定できます。  
  
 ![シリアライザーの設定](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 シリアライザーは、次の例に示すようにコードで設定することもできます。  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
  
```  
  
 ワークフロー サービスにも既知の型を指定できます。既知の型[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[既知のデータ コントラクト型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」を参照してください。既知の型は、デザイナーまたはコードで指定できます。デザイナーで既知の型を指定するには、次の図に示すように <xref:System.ServiceModel.Activities.Receive> アクティビティのプロパティ ウィンドウで KnownTypes プロパティの横の省略記号ボタンをクリックします。  
  
 ![KnownTypes プロパティ](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 これにより、既知の型を検索および指定できる型コレクション エディターが表示されます。  
  
 ![既知の型の追加](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 **\[新しい型の追加\]** リンクをクリックし、ドロップダウンを使用して既知の型コレクションに追加する型を選択または検索します。既知の型をコードで指定するには、次の例に示すように <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> プロパティを使用します。  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
  
```  
  
 ワークフロー サービスのシリアル化の構成方法を示す完全なコード例を確認するには、「[ワークフロー サービスでのメッセージの書式設定](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md)」を参照してください。