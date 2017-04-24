---
title: "クライアントのランタイム動作の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "システム指定のクライアントの動作 [WCF]"
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# クライアントのランタイム動作の指定
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] クライアントは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスと同様に、クライアント アプリケーションに合わせてランタイム動作を変更するように構成できます。 クライアントのランタイム動作を指定する際には、3 つの属性を使用できます。 双方向クライアント コールバック オブジェクトを使用して、 <xref:System.ServiceModel.CallbackBehaviorAttribute>と<xref:System.ServiceModel.Description.CallbackDebugBehavior>実行時の動作を変更する属性です。 その他の属性<xref:System.ServiceModel.Description.ClientViaBehavior>、論理送信先を直接のネットワーク送信先と区別するために使用できます。 さらに、双方向クライアントのコールバック型では、サービス側の動作の一部を使用できます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][サービスの実行時の動作を指定する](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)です。  
  
## <a name="using-the-callbackbehaviorattribute"></a>CallbackBehaviorAttribute の使用  
 構成するかを使用して、クライアント アプリケーションでコールバック コントラクト実装の実行動作を拡張、 <xref:System.ServiceModel.CallbackBehaviorAttribute>クラスです。 この属性としてコールバック クラスに対して同様の機能を実行する、 <xref:System.ServiceModel.ServiceBehaviorAttribute>動作とトランザクションの設定をインスタンス化を除き、クラスです。  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>クラスは、コールバック コントラクトを実装するクラスに適用する必要があります。 双方向コントラクトの実装に適用されている場合、 <xref:System.InvalidOperationException>実行時に例外がスローされます。 次のコード例は、 <xref:System.ServiceModel.CallbackBehaviorAttribute>クラスを使用するコールバック オブジェクト、 <xref:System.Threading.SynchronizationContext>マーシャ リングするスレッドを決定する、 <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A>メッセージ検証を実施するプロパティと<xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A>として例外を返すプロパティ<xref:System.ServiceModel.FaultException>デバッグ用のサービス オブジェクト。  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>CallbackDebugBehavior を使用したマネージ例外情報のフローの有効化  
 マネージ例外情報を設定してデバッグ用のサービスにクライアント コールバック オブジェクト内のフローを有効にすることができます、 <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>プロパティを`true`プログラムまたはアプリケーション構成ファイルします。  
  
 マネージ例外情報をサービスに戻すのは、セキュリティ リスクになる可能性があります。これは、例外の詳細により、非承認のサービスで使用可能な内部クライアントの実装についての情報が公開されるからです。 さらに、ですが、 <xref:System.ServiceModel.Description.CallbackDebugBehavior>プロパティをプログラムで設定することも、無効にすることを忘れがちになります<xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>を展開する場合。  
  
 セキュリティの問題にかかわるので、以下を強くお勧めします。  
  
-   値を設定、アプリケーション構成ファイルを使用して、 <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>プロパティを`true`します。  
  
-   これは、制御されたデバッグ シナリオの場合に限って行います。  
  
 
          [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に、SOAP メッセージのクライアント コールバック オブジェクトからマネージ例外情報を返すように指示するクライアント構成ファイルを次のコード例に示します。  
  
 <!-- TODO: review snippet reference [!code[SCA.CallbackContract#4](../../../samples/snippets/common/VS_Snippets_CFX/sca.callbackcontract/common/client.exe.config#4)]  -->
 <!-- TODO: review snippet reference [!code-csharp[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  -->
 <!-- TODO: review snippet reference [!code-vb[SCA.CallbackContract#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.callbackcontract/vb/client.exe.config#4)]  -->  
  
## <a name="using-the-clientviabehavior-behavior"></a>ClientViaBehavior 動作の使用  
 使用することができます、 <xref:System.ServiceModel.Description.ClientViaBehavior>トランスポート チャネルの作成対象となる統一リソース識別子を指定する動作。 この動作は、直接のネットワーク送信先が、メッセージの処理先と異なる場合に使用します。 これにより、呼び出し側のアプリケーションが最終的な送信先を知っているとは限らないとき、または送信先の `Via` ヘッダーがアドレスでないときに、複数のホップを経由するメッセージ交換が可能になります。  
  
## <a name="see-also"></a>関連項目  
 [サービスの実行時の動作を指定します。](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)