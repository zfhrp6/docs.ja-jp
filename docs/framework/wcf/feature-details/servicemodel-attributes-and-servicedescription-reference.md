---
title: "ServiceModel 属性および ServiceDescription 参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dbaa6f3df2bd4dcbde199f867686b3e05ae235f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>ServiceModel 属性および ServiceDescription 参照
*説明ツリー*型の階層は、(以降で、<xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType>クラス)、サービスのすべての側面を同時に記述します。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、説明ツリーを使用して、有効なサービス ランタイムの構築、Web サービス記述言語 (WSDL: Web Services Description Language)、XML スキーマ定義言語 (XSD: XML Schema Definition language)、およびクライアントが接続して使用できるサービスに関するポリシー アサーション (メタデータ) の公開、説明ツリーの値を表すさまざまなコードと構成ファイルの生成を行います。  
  
 ここでは、サービス コントラクトからコントラクトに関連するプロパティが取得されるしくみ、およびこれらのプロパティが実装され、説明ツリーに追加されるしくみについて説明します。 属性値が動作プロパティに変換された後、動作が説明ツリーに挿入される場合もあります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]説明ツリーの値は、メタデータに変換する方法を参照してください。 [ServiceDescription と WSDL 参照](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)です。  
  
## <a name="mapping-operations-to-the-description-tree"></a>説明ツリーへの操作のマッピング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションでは、サービス コントラクトが、属性を使用してインターフェイスまたはクラスとそのメソッドを操作のグループとしてマークするインターフェイス (またはクラス) によってモデル化されます。 <xref:System.ServiceModel.ServiceHost> クラスを開くと、サービス コントラクトと実装が構成情報に反映され、構成情報とマージされて、説明ツリーに挿入されます。  
  
 操作のモデルの 2 種類があります。*パラメーター*モデルおよび*メッセージ コントラクト*モデル。 パラメーター モデルでは、<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> クラスによってマークされたパラメーターまたは戻り値の型を持たないマネージ メソッドを使用します。 このモデルでは、開発者がパラメーターと戻り値のシリアル化を制御しますが、サービスとそのコントラクトの説明ツリーの設定に使用する値は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって生成されます。  
  
 構成ファイルで指定されたバインディングは、<xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> プロパティに直接読み込まれます。  
  
|ServiceBehaviorAttribute プロパティ|影響を受ける説明ツリーの値|  
|---------------------------------------|-------------------------------------|  
|名前|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|名前空間|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|すべての操作の <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> プロパティを設定します。|  
|MaxItemsInObjectGraph|すべての操作の <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> プロパティを設定します。|  
  
|ServiceContractAttribute プロパティ|影響を受ける説明ツリーの値|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|すべての操作の <xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A> に追加される <xref:System.ServiceModel.Description.MessageDescription>、<xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> と、場合によっては子の保護レベル。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]保護レベルの階層を参照してください[について保護レベル](../../../../docs/framework/wcf/understanding-protection-level.md)です。|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute 値|影響を受ける説明ツリーの値|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|OperationContractAttribute 値|影響を受ける説明ツリーの値|  
|--------------------------------------|-------------------------------------|  
|アクション|出力メッセージまたは入力メッセージの <xref:System.ServiceModel.Description.MessageDescription.Action%2A>。コントラクトまたはコールバック コントラクトによって異なります。|  
|AsyncPattern|true の場合は、<xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> と <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|<xref:System.ServiceModel.Description.MessageDescription> の 1 つの <xref:System.ServiceModel.Description.OperationDescription.Messages%2A> にマップします。|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|名前|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> と、場合によっては子の保護レベル。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]保護レベルの階層を参照してください[について保護レベル](../../../../docs/framework/wcf/understanding-protection-level.md)です。|  
|ReplyAction|出力メッセージまたは入力メッセージの <xref:System.ServiceModel.Description.MessageDescription.Action%2A>。コントラクトまたはコールバック コントラクトによって異なります。|  
  
|FaultContractAttribute 値|影響を受ける説明ツリーの値|  
|----------------------------------|-------------------------------------|  
|アクション|<xref:System.ServiceModel.Description.FaultDescription.Action%2A>。コントラクトまたはコールバック コントラクトによって異なります。|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|名前|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|名前空間|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|DataContractFormatAttribute 値|影響を受ける説明ツリーの値|  
|---------------------------------------|-------------------------------------|  
|用途|操作の <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> に <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 値が設定されます。|  
  
|XmlSerializerFormatAttribute 値|影響を受ける説明ツリーの値|  
|----------------------------------------|-------------------------------------|  
|スタイル|操作の <xref:System.ServiceModel.XmlSerializerFormatAttribute> に、この <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> プロパティが設定されます。|  
|用途|操作の <xref:System.ServiceModel.XmlSerializerFormatAttribute> に、<xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> が設定されます。|  
  
|TransactionFlowAttribute 値|影響を受ける説明ツリーの値|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> プロパティに操作の動作として追加されます。|  
  
|MessageContractAttribute 値|影響を受ける説明ツリーの値|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|MessageHeaderAttribute 値|影響を受ける説明ツリーの値|  
|----------------------------------|-------------------------------------|  
|Actor|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>対応するヘッダーの<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>対応するヘッダーの<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|名前|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>対応するヘッダーの<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|名前空間|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>対応するヘッダーの<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>対応するヘッダーの<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>対応するヘッダーの<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|MessageBodyMemberAttribute 値|影響を受ける説明ツリーの値|  
|--------------------------------------|-------------------------------------|  
|名前|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>対応する部分<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|名前空間|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>対応する部分<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|順序|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A>対応する部分<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>対応する部分<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|MessageHeaderArrayAttribute 値|影響を受ける説明ツリーの値|  
|---------------------------------------|-------------------------------------|  
|アクター|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|名前|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|名前空間|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|MessagePropertyAttribute 値|影響を受ける説明ツリーの値|  
|------------------------------------|-------------------------------------|  
|名前|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|MessageParameterAttribute 値|影響を受ける説明ツリーの値|  
|-------------------------------------|-------------------------------------|  
|名前|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>対応する部分<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]説明ツリーの値は、メタデータに変換する方法を参照してください。 [ServiceDescription と WSDL 参照](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ServiceDescription と WSDL 参照](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
