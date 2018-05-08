---
title: ワークフロー サービス内でのシリアル化の構成
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 74d9a812b9e0cd51a401fa3526c947d52413807a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-serialization-in-a-workflow-service"></a>ワークフロー サービス内でのシリアル化の構成
ワークフロー サービスは、Windows Communication Foundation (WCF) サービスと、いずれかを使用するオプションがあるため、 <xref:System.Runtime.Serialization.DataContractSerializer> (既定) または<xref:System.Xml.Serialization.XmlSerializer>です。 ワークフロー以外のサービスを記述する場合、使用するシリアライザーの型はサービスまたは操作コントラクトで指定されます。 WCF ワークフロー サービスを作成するときに、コードでは、これらのコントラクトを指定しないが、コントラクト推論で実行時に生成されます。 コントラクト推論の詳細については、次を参照してください。[ワークフロー内のコントラクトの使用](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)です。  シリアライザーは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> プロパティを使用して指定されます。 これは、次の図に示すようにデザイナーで設定できます。  
  
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
  
 ワークフロー サービスにも既知の型を指定できます。 既知の型の詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。 既知の型は、デザイナーまたはコードで指定できます。 デザイナーで既知の型を指定するには、次の図に示すように <xref:System.ServiceModel.Activities.Receive> アクティビティのプロパティ ウィンドウで KnownTypes プロパティの横の省略記号ボタンをクリックします。  
  
 ![KnownTypes プロパティ](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 これにより、既知の型を検索および指定できる型コレクション エディターが表示されます。  
  
 ![既知の型を追加する](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 クリックして、**新しいタイプの追加**リンクし、既知の型のコレクションに追加する型の選択や検索ドロップダウンを使用します。 既知の型をコードで指定するには、次の例に示すように <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> プロパティを使用します。  
  
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
  
 完全なコード例をワークフロー サービスのシリアル化を構成する方法を示すを参照してください「[ワークフロー サービス内メッセージを書式設定](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md)です。
