---
title: "方法 : 企業内のエンドポイントをロックダウンする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c580316415a1186bbdee518e201fb4c88419a72
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>方法 : 企業内のエンドポイントをロックダウンする
大規模な企業では、多くの場合、企業のセキュリティ ポリシーに準拠してアプリケーションを開発する必要があります。 ここでは、コンピューターにインストールされているすべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント アプリケーションを検証できるクライアント エンドポイント検証を開発してインストールする方法を説明します。  
  
 この場合、検証コントロールは、クライアント検証コントロールをクライアントにこのエンドポイントの動作が追加されるため[ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) machine.config ファイル内のセクションです。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、クライアント アプリケーションだけを対象に共通のエンドポイント動作を読み込み、サービス アプリケーションだけを対象に共通のサービス動作を読み込みます。 サービス アプリケーション用のこの同じ検証コントロールをインストールするには、検証コントロールがサービス動作であることが必要です。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)セクションです。  
  
> [!IMPORTANT]
>  サービスまたはエンドポイントの動作でマークされていない、<xref:System.Security.AllowPartiallyTrustedCallersAttribute>属性 (APTCA) に追加される、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)部分的な信頼でアプリケーションを実行すると、構成ファイルのセクションが実行されませんこのエラーが発生、環境、および例外がスローされません。 検証コントロールなどの共通動作を強制的に実行するには、次のいずれかを行う必要があります。  
>   
>  -- 共通動作を <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークし、部分信頼アプリケーションとして展開したときに実行できるようにします。 APTCA でマークされたアセンブリを実行できないように、コンピューターでレジストリ エントリを設定できます。  
>   
>  -- アプリケーションが完全信頼アプリケーションとして配置されている場合に、ユーザーが部分信頼環境でアプリケーションを実行するようにコード アクセス セキュリティ設定を変更できないことを確認します。 ユーザーがこのような変更を行うことができる場合、カスタム検証コントロールは実行されず、例外もスローされません。 これを確認する方法の 1 つを参照してください、`levelfinal`オプションを使用して[コード アクセス セキュリティ ポリシー ツール (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222)です。  
>   
>  詳細については、次を参照してください。[部分的な信頼のベスト プラクティス](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)と[展開シナリオのサポートされている](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)です。  
  
### <a name="to-create-the-endpoint-validator"></a>エンドポイント検証コントロールを作成するには  
  
1.  <xref:System.ServiceModel.Description.IEndpointBehavior> メソッドに、必要な検証手順を備えた <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> を作成します。 次にコード例を示します。 (、`InternetClientValidatorBehavior`から取得した、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプルです)。  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  手順 1. で作成したエンドポイント検証コントロールを登録する新しい <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を作成します。 このコード例を次に示します。 (この例の元のコードは、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプルです)。  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  コンパイル済みのアセンブリが厳密な名前で署名されていることを確認します。 詳細については、次を参照してください。、[厳密名ツール (SN です。EXE)](http://go.microsoft.com/fwlink/?LinkId=248217)と言語のコンパイラ コマンド。  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>検証コントロールをターゲット コンピューターにインストールには  
  
1.  適切な機構を使用してエンドポイント検証をインストールします。 企業では、グループ ポリシーと Systems Management Server (SMS) を使用してインストールします。  
  
2.  厳密な名前付きアセンブリをグローバル アセンブリ キャッシュを使用して、インストール、 [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx)です。  
  
3.  <xref:System.Configuration?displayProperty=nameWithType> 名前空間の型を使用して、次の処理を行います。  
  
    1.  拡張機能を追加、 [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)セクションの完全修飾型名を使用して要素をロックします。  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  動作要素を追加、`EndpointBehaviors`のプロパティ、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)セクションし、要素をロックします。 (サービスの検証コントロールをインストールするには、検証コントロールが <xref:System.ServiceModel.Description.IServiceBehavior> であることが必要です。また、検証コントロールを `ServiceBehaviors` プロパティに追加する必要があります)。次のコード例は、手順 a. と b. の後の適切な構成を示しています。厳密な名前が存在しない点だけが異なります。  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  machine.config ファイルを保存します。 次のコード例では、手順 3. にあるすべてのタスクを実行しますが、変更された machine.config ファイルのコピーはローカルに保存されます。  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>例  
 次のコード例では、machine.config ファイルに共通の動作を追加し、そのコピーをディスクに保存する方法を示します。 `InternetClientValidatorBehavior`から取得した、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプルです。  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 また、構成ファイルの要素を暗号化する必要がある場合もあります。 詳細については、「参照」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [DPAPI を使用する暗号化の構成ファイルの要素](http://go.microsoft.com/fwlink/?LinkId=94954)  
 [RSA を使用して、暗号化のための構成ファイルの要素](http://go.microsoft.com/fwlink/?LinkId=94955)
