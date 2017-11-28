---
title: "インターネット インフォメーション サービスでホストされる WCF サービスの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42c30c5f83f8245531a357c2d0b179deb87a2845
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>インターネット インフォメーション サービスでホストされる WCF サービスの配置
IIS (インターネット インフォメーション サービス) でホストされている [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスの開発と展開には、次のタスクが含まれます。  
  
-   IIS、ASP.NET、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、および [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティブ化コンポーネントが正しくインストールおよび登録されていることを確認します。  
  
-   新しい IIS アプリケーションを作成するか、既存の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションを再利用します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス用の .svc ファイルを作成します。  
  
-   IIS アプリケーションにサービス実装を展開します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構成します。  
  
 IIS によってホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの作成に関する詳細なチュートリアルについては、「 [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)」を参照してください。  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS、ASP.NET、および WCF が正しくインストールおよび登録されていることの確認  
 IIS でホストされる[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービスを正常に機能させるには、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 、IIS、および ASP.NET をインストールする必要があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ( [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]の一部として)、ASP.NET、および IIS のインストール手順は、使用しているオペレーティング システムのバージョンによって異なります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] および [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のインストール [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]、「 [Microsoft .NET Framework 4.0 (Web インストーラー)](http://go.microsoft.com/fwlink/?LinkId=201185)」を参照してください。 IIS のインストール手順については、「 [IIS のインストール](http://go.microsoft.com/fwlink/?LinkId=201188)」を参照してください。  
  
 IIS が既にコンピューターにインストールされている場合は、 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] のインストール プロセスにより、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が IIS に自動登録されます。 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]の後に IIS をインストールした場合は、追加の手順に従って、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を IIS と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]に登録する必要があります。 使用しているオペレーティング システムに応じて、次のように実行します。  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]、Windows 7、および[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: を使用して、 [ServiceModel 登録ツール (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md)ツールを登録して[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]iis: このツールを使用する入力**ServiceModelReg.exe/i/x**でVisual Studio コマンド プロンプトでします。 このコマンド プロンプトを開くには、[スタート] ボタンをクリックし、 **[すべてのプログラム]**, **[Microsoft Visual Studio 2012]**, **[Visual Studio ツール]**の順にポイントし、 **[Visual Studio コマンド プロンプト]**をクリックします。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]のサブコンポーネントの Windows Communication Foundation アクティベーション コンポーネントをインストールします。 これを行う、コントロール パネルで、をクリックして**プログラム追加と削除**し**追加\/Windows コンポーネントの削除**です。 **Windows コンポーネント ウィザード**がアクティブになります。  
  
-   Windows 7:  
  
 最後に、ASP.NET が .NET Framework Version 4 を使用するように設定されていることを確認する必要があります。 これには、–i オプションを指定して ASPNET_Regiis ツールを実行します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ASP.NET IIS 登録ツール](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>新しい IIS アプリケーションの作成、または既存の ASP.NET アプリケーションの再利用  
 IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、IIS アプリケーションの内部に存在する必要があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのみをホストする新しい IIS アプリケーションを作成できます。 または、既に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンテンツ (.aspx ページや ASP.NET Web サービス (ASMX) など) をホストしている既存のアプリケーションに [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] サービスを展開することもできます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 、「 [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)」を参照してください。  
  
 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] とそれ以降のバージョンでは、隔離されているオブジェクト指向プログラミング アプリケーションは定期的に再起動されることに注意してください。 既定値は 1740 分です。 サポートされている最大値は 71,582 分です。 この再起動は、無効にできます。 このプロパティ[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 、「 [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968)」を参照してください。  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>WCF サービス用の .svc ファイルの作成  
 IIS でホストされる[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、IIS アプリケーションの内部で特別なコンテンツ ファイル (.svc ファイル) として表現されます。 これは、ASMX ページが、IIS アプリケーションの内部で .asmx ファイルとして表現されるのと同様です。 .svc ファイルには、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ホスト インフラストラクチャで、着信メッセージに応えてホスト対象サービスをアクティブ化できるようにする、[@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)固有の処理ディレクティブ ( [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ) が含まれます。 .svc ファイルの最も一般的な構文を次のステートメントに示します。  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 この構文には、 [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) ディレクティブと単一の属性 `Service`が含まれます。 `Service` 属性の値は、サービス実装の共通言語ランタイム (CLR: Common Language Runtime) 型名です。 このディレクティブを使用することは、次のコードを使用してサービス ホストを作成することと基本的に同じです。  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 サービスのベース アドレスの一覧を作成するなど、追加のホスト構成を実行することもできます。 カスタム <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、このディレクティブをカスタム ホスト ソリューション用に拡張することもできます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする IIS アプリケーションは、 <xref:System.ServiceModel.ServiceHost> インスタンスの作成とライフタイムの管理を実行しません。 管理対象の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ホスト インフラストラクチャは、.svc ファイルに対する最初の要求を受け取ったときに、必要な <xref:System.ServiceModel.ServiceHost> インスタンスを動的に作成します。 このインスタンスは、コードによって明示的に閉じられるか、アプリケーションがリサイクルされるときまで解放されません。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 、「 [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)」を参照してください。  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>IIS アプリケーションへのサービス実装の展開  
 IIS でホストされる[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]と同一の動的なコンパイル モデルを使用します。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]の場合と同様に、IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実装コードは、次のようないくつかの方法でさまざまな場所に展開できます。  
  
-   グローバル アセンブリ キャッシュ (GAC: Global Assembly Cache) またはアプリケーションの \bin ディレクトリに配置される、プリコンパイルされた .dll ファイルとして展開します。 プリコンパイルされたバイナリは、新しいバージョンのクラス ライブラリが展開されるまで更新されません。  
  
-   アプリケーションの \App_Code ディレクトリに配置される、コンパイル解除されたソース ファイルとして展開します。 このディレクトリに配置されたソース ファイルは、アプリケーションの最初の要求を処理するときに動的に要求されます。 \App_Code ディレクトリ内のファイルを変更すると、次の要求を受け取ったときにアプリケーション全体がリサイクルされ、再コンパイルされます。  
  
-   .svc ファイルに直接格納される、コンパイル解除されたコードとして展開します。 実装コードでは、後に、サービスの .svc ファイルでは、インラインであることができます、@ServiceHostディレクティブです。 インライン コードを変更すると、次の要求を受け取ったときにアプリケーションがリサイクルされ、再コンパイルされます。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] コンパイル モデル [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 、「 [ASP.NET コンパイルの概要](http://go.microsoft.com/fwlink/?LinkId=94773)」を参照してください。  
  
## <a name="configure-the-wcf-service"></a>WCF サービスの構成  
 IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの構成は、アプリケーションの Web.config ファイルに格納されます。 IIS でホストされるサービスは、IIS の外部でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同じ構成要素と構文を使用します。 ただし、次の制約は、IIS ホスト環境に固有です。  
  
-   IIS でホストされるサービスのベース アドレス。  
  
-   ホストしているアプリケーション[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS の外部でのサービスは、一連のベース アドレス Uri を渡すことによって、ホストするサービスのベース アドレスを制御できます、<xref:System.ServiceModel.ServiceHost>コンス トラクターを提供したりして、 [\<ホスト >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)サービスの構成内の要素。 IIS でホストされるサービスは、それぞれのベース アドレスを制御できません。IIS でホストされるサービスのベース アドレスは、その .svc ファイルのアドレスです。  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS でホストされるサービスのエンドポイント アドレス  
 IIS でホストされるときのエンドポイント アドレスは、常にサービスを表す .svc ファイルのアドレスを基準にした相対アドレスと見なされます。 たとえば、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのベース アドレスが http://localhost/Application1/MyService.svc で、次のエンドポイント構成を伴う場合  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 "http://localhost/Application1/MyService.svc/anotherEndpoint" に到達できるエンドポイントが得られます。  
  
 同様に、相対アドレスとして空の文字列を使用するエンドポイント構成要素では、ベース アドレスである http://localhost/Application1/MyService.svc に到達できるエンドポイントが得られます。  
  
```xml  
<endpoint address="" ... />  
```  
  
 IIS でホストされるサービスのエンドポイントには、常に相対エンドポイント アドレスを使用する必要があります。 完全修飾されたエンドポイント アドレス (http://localhost/MyService.svc など) を指定すると、エンドポイント アドレスが、エンドポイントを公開するサービスをホストする IIS アプリケーションを指さない場合、サービスの展開エラーになる可能性があります。 ホストされるサービスに相対エンドポイント アドレスを使用すると、このような競合が回避されます。  
  
### <a name="available-transports"></a>利用可能なトランスポート  
 IIS 5.1 および[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でホストされる [!INCLUDE[iis601](../../../../includes/iis601-md.md)] サービスが使用できるのは、HTTP ベースの通信のみに制限されています。 これらの IIS プラットフォームでホストされるサービスで、非 HTTP バインドを使用するように構成すると、サービスをアクティブ化するときにエラーが発生します。 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]でサポートされるトランスポートには、既存の MSMQ アプリケーションとの後方互換性を実現する HTTP、Net.TCP、Net.Pipe、Net.MSMQ、msmq.formatname があります。  
  
### <a name="http-transport-security"></a>HTTP トランスポート セキュリティ  
 IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでは、サービスを格納する IIS 仮想ディレクトリで設定がサポートされている場合、HTTP トランスポート セキュリティ (基本認証、ダイジェスト認証、Windows 統合認証などの HTTPS および HTTP 認証) を利用できます。 ホストされるエンドポイントのバインディングでの HTTP トランスポート セキュリティ設定は、そのエンドポイントを格納する IIS 仮想ディレクトリでのトランスポート セキュリティ設定と一致する必要があります。  
  
 たとえば、HTTP ダイジェスト認証を使用するように構成された [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイントは、HTTP ダイジェスト認証を許可するように構成された IIS 仮想ディレクトリに存在する必要があります。 IIS の設定と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイントの設定の組み合わせが一致しない場合、サービスをアクティブ化するときにエラーが発生します。  
  
## <a name="see-also"></a>関連項目  
 [インターネット インフォメーション サービスをホストしています。](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
