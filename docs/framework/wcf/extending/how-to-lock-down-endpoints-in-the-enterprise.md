---
title: "方法 : 企業内のエンドポイントをロックダウンする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 方法 : 企業内のエンドポイントをロックダウンする
大規模な企業では、多くの場合、企業のセキュリティ ポリシーに準拠してアプリケーションを開発する必要があります。  ここでは、コンピューターにインストールされているすべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント アプリケーションを検証できるクライアント エンドポイント検証を開発してインストールする方法を説明します。  
  
 この場合、このエンドポイント動作は machine.config ファイルのクライアントの [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) セクションに追加されるため、検証コントロールはクライアント検証コントロールです。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、クライアント アプリケーションだけを対象に共通のエンドポイント動作を読み込み、サービス アプリケーションだけを対象に共通のサービス動作を読み込みます。  サービス アプリケーション用のこの同じ検証コントロールをインストールするには、検証コントロールがサービス動作であることが必要です。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) セクション。  
  
> [!IMPORTANT]
>  アプリケーションが部分信頼環境で実行されている場合、構成ファイルの [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) セクションに追加された <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性 \(APTCA\) でマークされていないサービス動作またはエンドポイント動作は実行されません。また、そのようになっても例外はスローされません。  検証コントロールなどの共通動作を強制的に実行するには、次のいずれかを行う必要があります。  
>   
>  \-\- 共通動作を <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークし、部分信頼アプリケーションとして展開したときに実行できるようにします。  APTCA でマークされたアセンブリを実行できないように、コンピューターでレジストリ エントリを設定できます。  
>   
>  \-\- アプリケーションが完全信頼アプリケーションとして配置されている場合に、ユーザーが部分信頼環境でアプリケーションを実行するようにコード アクセス セキュリティ設定を変更できないことを確認します。  ユーザーがこのような変更を行うことができる場合、カスタム検証コントロールは実行されず、例外もスローされません。  これを確認する方法については、「[コード アクセス セキュリティ ポリシー ツール \(Caspol.exe\)](http://go.microsoft.com/fwlink/?LinkId=248222)」の `levelfinal` オプションを参照してください。  
>   
>  詳細については、「[部分信頼のベスト プラクティス](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)」および「[サポートされている配置シナリオ](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)」を参照してください。  
  
### エンドポイント検証コントロールを作成するには  
  
1.  <xref:System.ServiceModel.Description.IEndpointBehavior> メソッドに、必要な検証手順を備えた <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> を作成します。  次にコード例を示します。  \(`InternetClientValidatorBehavior` は[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)のサンプルから取得したものです。\)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  手順 1. で作成したエンドポイント検証コントロールを登録する新しい <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を作成します。  このコード例を次に示します。  \(この例の元のコードは、「[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)」のサンプルにあります。\)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  コンパイル済みのアセンブリが厳密な名前で署名されていることを確認します。  詳細については、「[Sn.exe \(厳密名ツール\)](http://go.microsoft.com/fwlink/?LinkId=248217)」およびご使用の言語のコンパイラ コマンドを参照してください。  
  
### 検証コントロールをターゲット コンピューターにインストールには  
  
1.  適切な機構を使用してエンドポイント検証をインストールします。  企業では、グループ ポリシーと Systems Management Server \(SMS\) を使用してインストールします。  
  
2.  [Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx)を使用して、厳密な名前のアセンブリをグローバル アセンブリ キャッシュにインストールします。  
  
3.  <xref:System.Configuration?displayProperty=fullName> 名前空間の型を使用して、次の処理を行います。  
  
    1.  完全修飾型名を使用して [\<behaviorExtensions\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) セクションに拡張を追加し、要素をロックします。  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  動作要素を [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) セクションの `EndpointBehaviors` プロパティに追加して要素をロックします。  \(サービスの検証コントロールをインストールするには、検証コントロールが <xref:System.ServiceModel.Description.IServiceBehavior> であることが必要です。また、検証コントロールを `ServiceBehaviors` プロパティに追加する必要があります\)。 次のコード例は、手順 a.  と b. の後の適切な構成を示しています。厳密な名前が存在しない点だけが異なります。  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  machine.config ファイルを保存します。  次のコード例では、手順 3. にあるすべてのタスクを実行しますが、変更された machine.config ファイルのコピーはローカルに保存されます。  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## 使用例  
 次のコード例では、machine.config ファイルに共通の動作を追加し、そのコピーをディスクに保存する方法を示します。  `InternetClientValidatorBehavior` は[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)のサンプルから取得したものです。  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## .NET Framework セキュリティ  
 また、構成ファイルの要素を暗号化する必要がある場合もあります。  詳細については、「参照」を参照してください。  
  
## 参照  
 [How To: DPAPI を使用して ASP.NET 2.0 内の構成セクションを暗号化する方法](http://go.microsoft.com/fwlink/?LinkId=94954)   
 [How To: RSA を使用して ASP.NET 2.0 内の構成セクションを暗号化する方法](http://go.microsoft.com/fwlink/?LinkId=94955)