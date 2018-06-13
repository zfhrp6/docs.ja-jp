---
title: インターネット インフォメーション サービスでホストされる WCF サービスの配置
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 59f18d8487deb52f5ecb5b5c814ec9bdbc74e2cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496381"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>インターネット インフォメーション サービスでホストされる WCF サービスの配置
インターネット インフォメーション サービス (IIS) でホストされている Windows Communication Foundation (WCF) サービスの展開の開発と、次のタスクで構成されます。  
  
-   IIS、ASP.NET、WCF、および WCF アクティブ化コンポーネントは正しくインストールされている、登録されていることを確認します。  
  
-   新しい IIS アプリケーションを作成するか、既存の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションを再利用します。  
  
-   WCF サービスの .svc ファイルを作成します。  
  
-   IIS アプリケーションにサービス実装を展開します。  
  
-   WCF サービスを構成します。  
  
 IIS でホストされる WCF サービスを作成する詳細なチュートリアルについては、次を参照してください。[する方法: IIS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)です。  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS、ASP.NET、および WCF が正しくインストールおよび登録されていることの確認  
 IIS でホストされる WCF サービスが正常に機能を WCF、IIS、および ASP.NET をインストールする必要があります。 WCF にインストールする手順 (の一部として、 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)])、ASP.NET と IIS が使用されているオペレーティング システムのバージョンによって異なります。 WCF のインストールの詳細については、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]を参照してください[Microsoft .NET Framework 4 の Web インストーラー](http://go.microsoft.com/fwlink/?LinkId=201185)です。 IIS のインストール手順については、「 [IIS のインストール](http://go.microsoft.com/fwlink/?LinkId=201188)」を参照してください。  
  
 インストール プロセス、 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] IIS が既にコンピューターにある場合は、IIS で WCF を自動的に登録します。 後に IIS がインストールされている場合、 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]、IIS で WCF を登録する追加の手順が必要と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]です。 使用しているオペレーティング システムに応じて、次のように実行します。  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]、Windows 7、および[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: を使用して、 [ServiceModel 登録ツール (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md)を IIS で WCF を登録するツール: このツールを使用する次のように入力します。 **ServiceModelReg.exe/i/x** Visual Studio でコマンド プロンプト。 このコマンド プロンプトを開くには、[スタート] ボタンをクリックし、 **[すべてのプログラム]**, **[Microsoft Visual Studio 2012]**, **[Visual Studio ツール]** の順にポイントし、 **[Visual Studio コマンド プロンプト]** をクリックします。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]のサブコンポーネントの Windows Communication Foundation アクティベーション コンポーネントをインストールします。 これを行う、コントロール パネルで、をクリックして**プログラム追加と削除**し**追加\/Windows コンポーネントの削除**です。 **Windows コンポーネント ウィザード**がアクティブになります。  
  
-   Windows 7:  
  
 最後に、ASP.NET が .NET Framework Version 4 を使用するように設定されていることを確認する必要があります。 これには、–i オプションを指定して ASPNET_Regiis ツールを実行します。 詳細については、次を参照してください[ASP.NET IIS 登録ツール。](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>新しい IIS アプリケーションの作成、または既存の ASP.NET アプリケーションの再利用  
 IIS でホストされる WCF サービスは、IIS アプリケーションの内部に存在する必要があります。 排他的に WCF サービスをホストする新しい IIS アプリケーションを作成することができます。 既にホストしている既存のアプリケーションに WCF サービスを展開する代わりに、[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]コンテンツ (.aspx ページや ASP.NET Web サービス (ASMX)) などです。 これらのオプションの詳細についてを参照してください、「ホスティング WCF サイド バイ サイド ASP.NET で」とのセクションでは、「ASP.NET 互換モードでは WCF サービスをホスティング」 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)です。  
  
 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] とそれ以降のバージョンでは、隔離されているオブジェクト指向プログラミング アプリケーションは定期的に再起動されることに注意してください。 既定値は 1740 分です。 サポートされている最大値は 71,582 分です。 この再起動は、無効にできます。 このプロパティの詳細については、次を参照してください。、 [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968)です。  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>WCF サービス用の .svc ファイルの作成  
 IIS でホストされる WCF サービスは、IIS アプリケーションの内部の特別なコンテンツ ファイル (.svc ファイル) として表されます。 これは、ASMX ページが、IIS アプリケーションの内部で .asmx ファイルとして表現されるのと同様です。 .Svc ファイルには、WCF 固有の処理ディレクティブが含まれています ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) インフラストラクチャをホストしている WCF 受信メッセージに応答内のホステッド サービスをアクティブ化することができます。 .svc ファイルの最も一般的な構文を次のステートメントに示します。  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 この構文には、 [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) ディレクティブと単一の属性 `Service`が含まれます。 `Service` 属性の値は、サービス実装の共通言語ランタイム (CLR: Common Language Runtime) 型名です。 このディレクティブを使用することは、次のコードを使用してサービス ホストを作成することと基本的に同じです。  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 サービスのベース アドレスの一覧を作成するなど、追加のホスト構成を実行することもできます。 カスタム <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、このディレクティブをカスタム ホスト ソリューション用に拡張することもできます。 WCF サービスをホストする IIS アプリケーションは、の作成とライフタイムの管理の責任を負いません<xref:System.ServiceModel.ServiceHost>インスタンス。 管理されている WCF ホスティング インフラストラクチャの作成、必要な<xref:System.ServiceModel.ServiceHost>インスタンスを動的に .svc ファイルに対する最初の要求を受け取ったときです。 このインスタンスは、コードによって明示的に閉じられるか、アプリケーションがリサイクルされるときまで解放されません。  
  
 .Svc ファイルの構文の詳細については、次を参照してください。 [ @ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)です。  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>IIS アプリケーションへのサービス実装の展開  
 IIS でホストされる WCF サービスと同様の動的なコンパイル モデルを使用して[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]です。 同様[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]、いくつか方法でさまざまな場所に、IIS でホストされる WCF サービスの実装コードを次のように展開することができます。  
  
-   グローバル アセンブリ キャッシュ (GAC: Global Assembly Cache) またはアプリケーションの \bin ディレクトリに配置される、プリコンパイルされた .dll ファイルとして展開します。 プリコンパイルされたバイナリは、新しいバージョンのクラス ライブラリが展開されるまで更新されません。  
  
-   アプリケーションの \App_Code ディレクトリに配置される、コンパイル解除されたソース ファイルとして展開します。 このディレクトリに配置されたソース ファイルは、アプリケーションの最初の要求を処理するときに動的に要求されます。 \App_Code ディレクトリ内のファイルを変更すると、次の要求を受け取ったときにアプリケーション全体がリサイクルされ、再コンパイルされます。  
  
-   .svc ファイルに直接格納される、コンパイル解除されたコードとして展開します。 実装コードでは、後に、サービスの .svc ファイルでは、インラインであることができます、@ServiceHostディレクティブです。 インライン コードを変更すると、次の要求を受け取ったときにアプリケーションがリサイクルされ、再コンパイルされます。  
  
 詳細については、[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]コンパイル モデルを参照してください[ASP.NET コンパイルの概要](http://go.microsoft.com/fwlink/?LinkId=94773)です。  
  
## <a name="configure-the-wcf-service"></a>WCF サービスの構成  
 IIS でホストされる WCF サービスは、アプリケーションの Web.config ファイルでの構成を格納します。 IIS でホストされるサービスは、IIS の外部でホストされる WCF サービスとして、同じ構成要素と構文を使用します。 ただし、次の制約は、IIS ホスト環境に固有です。  
  
-   IIS でホストされるサービスのベース アドレス。  
  
-   アプリケーションの IIS の外部でのホスティングの WCF サービスはベースのセットを渡すことによって、ホストするサービスのベース アドレスを制御できますアドレス Uri を<xref:System.ServiceModel.ServiceHost>コンス トラクターを提供したりして、 [\<ホスト >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)内の要素、サービスの構成。 IIS でホストされるサービスは、それぞれのベース アドレスを制御できません。IIS でホストされるサービスのベース アドレスは、その .svc ファイルのアドレスです。  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS でホストされるサービスのエンドポイント アドレス  
 IIS でホストされるときのエンドポイント アドレスは、常にサービスを表す .svc ファイルのアドレスを基準にした相対アドレスと見なされます。 たとえば、WCF サービスのベース アドレスはhttp://localhost/Application1/MyService.svc次のエンドポイント構成を使用します。  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 これにより、エンドポイントに到達できる"http://localhost/Application1/MyService.svc/anotherEndpoint"です。  
  
 同様に、エンドポイント構成要素に到達できるエンドポイントを提供する相対アドレスとして空の文字列を使用するhttp://localhost/Application1/MyService.svc、これは、ベース アドレス。  
  
```xml  
<endpoint address="" ... />  
```  
  
 IIS でホストされるサービスのエンドポイントには、常に相対エンドポイント アドレスを使用する必要があります。 完全修飾エンドポイント アドレスを提供して (たとえば、http://localhost/MyService.svc)エンドポイントのアドレスが、エンドポイントを公開するサービスをホストする IIS アプリケーションを指していない場合に、サービスの展開でエラーにつながることができます。 ホストされるサービスに相対エンドポイント アドレスを使用すると、このような競合が回避されます。  
  
### <a name="available-transports"></a>利用可能なトランスポート  
 IIS 5.1 でホストされる WCF サービスと[!INCLUDE[iis601](../../../../includes/iis601-md.md)]HTTP ベースの通信を使用してに制限されます。 これらの IIS プラットフォームでホストされるサービスで、非 HTTP バインドを使用するように構成すると、サービスをアクティブ化するときにエラーが発生します。 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]でサポートされるトランスポートには、既存の MSMQ アプリケーションとの後方互換性を実現する HTTP、Net.TCP、Net.Pipe、Net.MSMQ、msmq.formatname があります。  
  
### <a name="http-transport-security"></a>HTTP トランスポート セキュリティ  
 IIS でホストされる WCF サービスと http を使用して、トランスポート セキュリティ (たとえば、HTTPS および HTTP 認証基本、ダイジェスト、Windows 統合認証など)、サービスを格納する IIS 仮想ディレクトリはそれらをサポートしている限り、設定。 ホストされるエンドポイントのバインディングでの HTTP トランスポート セキュリティ設定は、そのエンドポイントを格納する IIS 仮想ディレクトリでのトランスポート セキュリティ設定と一致する必要があります。  
  
 たとえば、HTTP ダイジェスト認証を使用するように構成 WCF エンドポイントは、HTTP ダイジェスト認証を行うことも構成されている IIS 仮想ディレクトリになければなりません。 IIS の設定と WCF エンドポイントの設定の組み合わせが一致しないは、サービスのアクティブ化では、エラーが発生します。  
  
## <a name="see-also"></a>関連項目  
 [インターネット インフォメーション サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
