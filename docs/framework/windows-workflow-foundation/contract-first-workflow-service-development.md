---
title: "コントラクト優先ワークフロー サービスの開発 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# コントラクト優先ワークフロー サービスの開発
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降の [!INCLUDE[wf](../../../includes/wf-md.md)] では、コントラクト優先ワークフローの開発という形で、Web サービスとワークフローの統合が向上しています。コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。このトピックでは、ワークフロー サービスのアクティビティおよびプロパティをサービス コントラクトの属性にマップする方法の概要について説明します。コントラクト優先ワークフロー サービスの作成手順の例については、「[既存のサービス コントラクトを使用するワークフロー サービスを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)」を参照してください。  
  
## このトピックの内容  
  
-   [ワークフロー属性へのサービス コントラクト属性のマップ](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#MappingAttributes)  
  
    -   [サービス コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#ServiceContract)  
  
    -   [操作コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#OperationContract)  
  
    -   [メッセージ コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#MessageContract)  
  
    -   [データ コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#DataContract)  
  
    -   [エラー コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#FaultContract)  
  
-   [サポートおよび実装に関する詳細情報](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#AdditionalSupport)  
  
    -   [サポートされていないサービス コントラクト機能](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    -   [構成済みのメッセージング アクティビティの生成](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#ActivityGeneration)  
  
##  <a name="MappingAttributes"></a> ワークフロー属性へのサービス コントラクト属性のマップ  
 次のセクションにある表では、さまざまな WCF 属性およびプロパティを示し、それらをコントラクト優先ワークフローのメッセージング アクティビティおよびプロパティにマップする方法について説明します。  
  
-   [サービス コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#ServiceContract)  
  
-   [操作コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#OperationContract)  
  
-   [メッセージ コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#MessageContract)  
  
-   [データ コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#DataContract)  
  
-   [エラー コントラクト属性](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#FaultContract)  
  
###  <a name="ServiceContract"></a> サービス コントラクト属性  
  
|プロパティ名|サポートの有無|説明|WF の検証|  
|------------|-------------|--------|------------|  
|CallbackContract|なし|コントラクトが双方向コントラクトの場合のコールバック コントラクトの型を取得または設定します。|\(なし\)|  
|ConfigurationName|なし|アプリケーション構成ファイル内でサービスを検索するために使用される名前を取得または設定します。|\(なし\)|  
|HasProtectionLevel|あり|メンバーに保護レベルが割り当てられているかどうかを示す値を取得します。|Receive.ProtectionLevel を null にすることはできません。|  
|Name|あり|Web サービス記述言語 \(WSDL\) での \<portType\> 要素の名前を取得または設定します。|Receive.ServiceContractName.LocalName が一致している必要があります。|  
|名前空間|あり|Web サービス記述言語 \(WSDL\) での \<portType\> 要素の名前空間を取得または設定します。|Receive.ServiceContractName.NameSpace が一致している必要があります。|  
|ProtectionLevel|あり|コントラクトのバインドで、ProtectionLevel プロパティの値をサポートする必要があるかどうかを指定します。|Receive.ProtectionLevel が一致している必要があります。|  
|SessionMode|なし|セッションが許可されるか、許可されないか、または必要であるかを示す値を取得または設定します。|\(なし\)|  
|TypeId|なし|派生クラスで実装すると、この属性の一意の識別子を取得します \(属性から継承\)。|\(なし\)|  
  
 ここにサブセクションの本文を挿入します。  
  
###  <a name="OperationContract"></a> 操作コントラクト属性  
  
|プロパティ名|サポートの有無|説明|WF の検証|  
|------------|-------------|--------|------------|  
|Action|あり|要求メッセージの WS\-Addressing アクションを取得または設定します。|Receive.Action が一致している必要があります。|  
|AsyncPattern|なし|サービス コントラクト内で Begin\<methodName\> メソッドと \<EndmethodName\> メソッドのペアを使用して、操作が非同期的に実装されることを示します。|\(なし\)|  
|HasProtectionLevel|あり|この操作のメッセージの暗号化、署名、または両方が必要かどうかを示す値を取得または設定します。|Receive.ProtectionLevel を null にすることはできません。|  
|IsInitiating|なし|メソッドが \(セッションが存在する場合に\) サーバー上でセッションを開始できる操作を実装するかどうかを示す値を取得または設定します。|\(なし\)|  
|IsOneWay|あり|操作が応答メッセージを返すかどうかを示す値を取得または設定します。|\(この Receive の SendReply またはこの Send の ReceiveReply がありません。\)|  
|IsTerminating|なし|応答メッセージが存在する場合に、そのメッセージの送信後にセッションを終了するようにサービス操作がサーバーに指示するかどうかを示す値を取得または設定します。|\(なし\)|  
|Name|あり|操作の名前を取得または設定します。|Receive.OperationName が一致している必要があります。|  
|ProtectionLevel|あり|操作のメッセージの暗号化、署名、または両方が必要かどうかを示す値を取得または設定します。|Receive.ProtectionLevel が一致している必要があります。|  
|ReplyAction|あり|操作の応答メッセージの SOAP アクションの値を取得または設定します。|SendReply.Action が一致している必要があります。|  
|TypeId|なし|派生クラスで実装すると、この属性の一意の識別子を取得します \(属性から継承\)。|\(なし\)|  
  
###  <a name="MessageContract"></a> メッセージ コントラクト属性  
  
|プロパティ名|サポートの有無|説明|WF の検証|  
|------------|-------------|--------|------------|  
|HasProtectionLevel|あり|メッセージに保護レベルが割り当てられているかどうかを示す値を取得します。|検証なし \(Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります\)。|  
|IsWrapped|あり|メッセージ本文にラッパー要素があるかどうかを指定する値を取得または設定します。|検証なし \(Receive.Content と Sendreply.Content がメッセージ コントラクト型と一致している必要があります\)。|  
|ProtectionLevel|なし|メッセージの暗号化、署名、または両方が必要かどうかを指定する値を取得または設定します。|\(なし\)|  
|TypeId|あり|派生クラスで実装すると、この属性の一意の識別子を取得します \(属性から継承\)。|検証なし \(Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります\)。|  
|WrapperName|あり|メッセージ本文のラッパー要素の名前を取得または設定します。|検証なし \(Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります\)。|  
|WrapperNamespace|なし|メッセージ本文のラッパー要素の名前空間を取得または設定します。|\(なし\)|  
  
###  <a name="DataContract"></a> データ コントラクト属性  
  
|プロパティ名|サポートの有無|説明|WF の検証|  
|------------|-------------|--------|------------|  
|IsReference|なし|オブジェクト参照データを保持するかどうかを示す値を取得または設定します。|\(なし\)|  
|Name|あり|型のデータ コントラクトの名前を取得または設定します。|検証なし \(Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります\)。|  
|名前空間|あり|型のデータ コントラクトの名前空間を取得または設定します。|検証なし \(Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります\)。|  
|TypeId|なし|派生クラスで実装すると、この属性の一意の識別子を取得します \(属性から継承\)。|\(なし\)|  
  
###  <a name="FaultContract"></a> エラー コントラクト属性  
  
|プロパティ名|サポートの有無|説明|WF の検証|  
|------------|-------------|--------|------------|  
|Action|あり|操作コントラクトの一部として指定された SOAP エラー メッセージのアクションを取得または設定します。|SendReply.Action が一致している必要があります。|  
|DetailType|あり|エラー情報を含むシリアル化可能なオブジェクトの型を取得します。|SendReply.Content が型と一致している必要があります。|  
|HasProtectionLevel|なし|SOAP エラー メッセージに保護レベルが割り当てられているかどうかを示す値を取得します。|\(なし\)|  
|Name|なし|Web サービス記述言語 \(WSDL\) でのエラー メッセージの名前を取得または設定します。|\(なし\)|  
|名前空間|なし|SOAP エラーの名前空間を取得または設定します。|\(なし\)|  
|ProtectionLevel|なし|SOAP エラーがバインドに要求する保護レベルを指定します。|\(なし\)|  
|TypeId|なし|派生クラスで実装すると、この属性の一意の識別子を取得します \(属性から継承\)。|\(なし\)|  
  
##  <a name="AdditionalSupport"></a> サポートおよび実装に関する詳細情報  
  
-   [サポートされていないサービス コントラクト機能](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
-   [構成済みのメッセージング アクティビティの生成](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md#ActivityGeneration)  
  
###  <a name="UnsupportedFeatures"></a> サポートされていないサービス コントラクト機能  
  
-   コントラクトでの TPL \(タスク並列ライブラリ\) タスクの使用はサポートされていません。  
  
-   サービス コントラクトの継承はサポートされていません。  
  
###  <a name="ActivityGeneration"></a> 構成済みのメッセージング アクティビティの生成  
 コントラクト優先ワークフロー サービスを使用する場合に事前構成されたメッセージ アクティビティの生成をサポートするために、2 つのパブリック静的メソッドが <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティに追加されています。  
  
-   <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=fullName>  
  
-   <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=fullName>  
  
 これらのメソッドによって生成されたアクティビティはコントラクト検証に合格する必要があるため、これらのメソッドは <xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> の検証ロジックの一部として内部で使用されます。<xref:System.ServiceModel.Activities.Receive.OperationName%2A>、<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>、<xref:System.ServiceModel.Activities.Receive.Action%2A>、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>、<xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>、および <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> はすべて、インポートされたコントラクトに一致するよう事前に構成されています。ワークフロー デザイナーにあるアクティビティのコンテンツ プロパティ ページの **\[メッセージ\]** または **\[パラメーター\]** セクションも、コントラクトと一致するように事前に構成されています。  
  
 WCF エラー コントラクトは、<xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection> に表示される、エラーごとに構成された個別の構成済み <xref:System.ServiceModel.Activities.SendReply> アクティビティ セットを返すことによって処理されます。  
  
 WF サービスで現在サポートされていない、<xref:System.ServiceModel.Description.OperationDescription> の他の部分 \(WebGet\/WebInvoke の動作、カスタム操作の動作など\) では、API は生成および構成の一環としてそれらの値を無視します。例外はスローされません。