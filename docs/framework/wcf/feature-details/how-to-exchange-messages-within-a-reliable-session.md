---
title: "方法 : 信頼されたセッション内のメッセージを変換する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6207b526aa98fd01892b493ab5b6ad6a58abc3c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>方法 : 信頼されたセッション内のメッセージを変換する

このトピックでは、信頼できるセッションを有効にするために必要な手順について説明します。ここでは、信頼できるセッションを (既定ではなく) オプションでサポートするシステム指定のバインディングを使用します。 強制的にコードを使用して、信頼できるセッションを有効にするか、構成ファイルで宣言します。 この手順は、信頼できるセッションを有効にして、送信された順序と同じ順序でメッセージが到達するを規定するために、クライアントとサービス構成ファイルを使用します。

この手順の重要な部分は、エンドポイント構成要素が含まれている、`bindingConfiguration`という名前のバインディング構成を参照する属性を`Binding1`です。 [ **\<バインディング >** ](../../../../docs/framework/misc/binding.md)構成要素を設定して、信頼できるセッションを有効にするには、この名前の参照、`enabled`の属性、 [ **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)要素を`true`です。 信頼できるセッションで順序付き配信の保証を指定するには、`ordered` 属性を `true` に設定します。

この例の元のコピーを次を参照してください。 [WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)です。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用する WSHttpBinding でサービスを構成します。

1. サービスの種類にサービス コントラクトを定義します。

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. サービス クラスにサービス コントラクトを実装します。 サービスの実装の内部アドレスやバインディングの情報が指定されていないことに注意してください。 構成ファイルからアドレスとバインディング情報を取得するコードを記述する必要はないです。

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. 作成、 *Web.config*のエンドポイントを構成するファイル、`CalculatorService`を使用して、<xref:System.ServiceModel.WSHttpBinding>有効になっているし、順次配送のために必要なメッセージの信頼できるセッションでします。

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. 作成、 *Service.svc*行を含むファイル。

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  場所、 *Service.svc*インターネット インフォメーション サービス (IIS) 仮想ディレクトリのファイルです。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用する WSHttpBinding でクライアントを構成します。

1. 使用して、 [ServiceModel メタデータ ユーティリティ ツール (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータからコードを生成するためのコマンドラインから。

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 生成されたクライアントが含まれています、`ICalculator`クライアントの実装が満たす必要があるサービス コントラクトを定義するインターフェイスです。

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. 生成されたクライアント アプリケーションは `ClientCalculator` も実装します。 アドレスとバインディング情報が、サービスの実装で任意の位置指定されていないことに注意してください。 構成ファイルからアドレスとバインディング情報を取得するコードを記述する必要はないです。

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe*もを使用するクライアントの構成を生成、<xref:System.ServiceModel.WSHttpBinding>クラスです。 構成ファイルの名前*App.config*を使用する場合[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]です。

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. インスタンスを作成、`ClientCalculator`アプリケーションでサービス操作を呼び出します。

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. クライアントをコンパイルして実行します。

## <a name="example"></a>例

システム指定のバインディングの中には、信頼できるセッションを既定でサポートするものがあります。 以下に例を示します。

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

信頼できるセッションをサポートするカスタム バインディングを作成する方法の例は、次を参照してください。[する方法: HTTPS で、カスタムの信頼できるセッション バインドを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)です。

## <a name="see-also"></a>関連項目

[信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
