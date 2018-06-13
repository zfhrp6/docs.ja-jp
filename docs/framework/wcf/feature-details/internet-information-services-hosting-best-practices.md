---
title: インターネット インフォメーション サービス ホスティングのベスト プラクティス
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 119f14df9d46883a33272903558d83128501b293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495763"
---
# <a name="internet-information-services-hosting-best-practices"></a>インターネット インフォメーション サービス ホスティングのベスト プラクティス
このトピックでは、Windows Communication Foundation (WCF) サービスをホストするためのベスト プラクティスについて説明します。  
  
## <a name="implementing-wcf-services-as-dlls"></a>WCF サービスの DLL としての実装  
 WCF を実装する Web アプリケーションの \bin ディレクトリに配置されている DLL としてのサービスは、再利用する、サービス モデルの外部の Web アプリケーション、たとえば、インターネット インフォメーション サービス (IIS) が展開できないテスト環境でを使用できます。  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS でホストされるアプリケーションでのサービス ホスト  
 IIS ホスト環境によってネイティブにサポートされていないネットワーク トランスポートで待機する新しいサービス ホストを作成する場合は、強制自己ホスト API を使用しないでください (たとえば、TCP サービスをホストする [!INCLUDE[iis601](../../../../includes/iis601-md.md)]。TCP 通信は、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] でネイティブにサポートされていません)。 この方法はお勧めしません。 強制的に作成されたサービス ホストは、IIS ホスト環境内で認識されないからです。 重要な点は、IIS がホスト アプリケーション プールがアイドル状態であるかどうかを判断するときに、強制的に作成されたサービスによって実行される処理が IIS によって考慮されないことです。 この結果、強制的に作成されたサービス ホストを持つアプリケーションは、IIS ホスト プロセスを積極的に廃棄する IIS ホスト環境を持つことになります。  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI と IIS でホストされるエンドポイント  
 IIS でホストされるサービスのエンドポイントは、絶対アドレスではなく、相対 URI (Uniform Resource Identifier) を使用して構成する必要があります。 これにより、エンドポイント アドレスが、ホスト アプリケーションに属する URI アドレスのセット内に確実に含まれ、メッセージに基づくアクティベーションが正常に行われるようになります。  
  
## <a name="state-management-and-process-recycling"></a>状態管理とプロセスのリサイクル  
 IIS ホスト環境は、メモリにローカル状態を保持しないサービスに最適化されています。 IIS は、さまざまな外部および内部イベントに応答してホスト プロセスをリサイクルするため、メモリのみに格納される揮発性の状態はすべて失われます。 IIS でホストされるサービスは、それぞれの状態をプロセスの外部 (データベースなど)、またはアプリケーションのリサイクル イベントが発生した場合に簡単に再作成できるメモリ内キャッシュに格納する必要があります。  
  
> [!NOTE]
>  メッセージ レイヤーの信頼性とセキュリティの WCF を使用するプロトコルは、揮発性メモリの状態の使用します。 WCF の信頼できるセッションとセキュリティ セッションは、アプリケーションのリサイクルにより予期せず終了する可能性があります。 これらのプロトコルの使用する IIS でホストされるアプリケーション場合、アプリケーション レイヤーの状態 (アプリケーション レイヤー構造やカスタム相関ヘッダーなど) または無効化を相互に関連付けるために WCF に用意されているセッション キー以外のものに依存する、または必要があります。IIS プロセスのリサイクル、ホストされるアプリケーションをします。  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>中間層シナリオでのパフォーマンスの最適化  
 最適なパフォーマンス、*中間層シナリオ*— 受信メッセージに応答の他のサービスを呼び出すサービス-リモート サービスに WCF サービスのクライアントを 1 回インスタンス化し、複数の受信の間で再利用要求します。 サービスの呼び出しの既存のクライアント インスタンスの相対コストのかかる操作は、WCF サービスのクライアントをインスタンス化して、中間層シナリオでは、要求間でリモート クライアントをキャッシュすることによってパフォーマンスが大幅を生成します。 WCF サービスのクライアントにはスレッド セーフであるがあるため、複数のスレッドにわたってクライアントへのアクセスを同期する必要はありません。  
  
 また、中間層シナリオでは、`svcutil /a` オプションによって生成された非同期 API を使用してパフォーマンスを向上させます。 `/a`オプションを指定、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を生成する`BeginXXX/EndXXX`呼び出せる可能性のある実行の時間の長いリモート サービスで行われるサービス操作ごとにメソッドバック グラウンド スレッドです。  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>マルチホーム シナリオまたはマルチネーム シナリオでの WCF  
 コンピューターのセットが共通の外部名を共有、IIS Web ファームの内部で WCF サービスを展開することができます (などhttp://www.contoso.com)は異なるホスト名によって個別にアドレス指定が、(たとえば、 http://www.contoso.com 2 つの異なるコンピューターにトラフィックを送る可能性があります名前付きhttp://machine1.internal.contoso.comとhttp://machine2.internal.contoso.com)です。 この展開シナリオでは、WCF で完全にサポートされる、サービスのメタデータ (Web Services Description Language) に正しい (外部) ホスト名を表示する WCF サービスをホストする IIS Web サイトの特別な構成が必要です。  
  
 生成 WCF サービス メタデータに正しいホスト名が表示されていることを確認するのには、明示的なホスト名を使用する WCF サービスをホストする IIS Web サイトの既定の id を構成します。 たとえば、www.contoso.com ファームの内部に存在するコンピューターがの IIS サイト バインディングを使用する必要があります * http:80:www.contoso.com と\*: 443:www.contoso.com HTTPS 用です。  
  
 Microsoft 管理コンソール (MMC) スナップインを使用して、IIS Web サイト バインディングを構成できます。  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>異なるユーザー コンテキストで実行されるアプリケーション プールが、一時フォルダー内の他のアカウントのアセンブリを上書きする  
 異なるユーザー コンテキストで実行されているアプリケーション プールが、一時的な [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ファイル フォルダー内の他のアカウントのアセンブリを上書きできないようにするには、アプリケーションごとに個別の ID と一時フォルダーを使用します。 たとえば、/Application1 と /Application2 という 2 つの仮想アプリケーションがある場合は、2 つの異なる ID を使用して、A と B の 2 つのアプリケーション プールを作成できます。 アプリケーション プール A は、一方のユーザー ID (user1) の下で、アプリケーション プール B は、もう一方のユーザー ID (user2) の下で実行でき、/Application1 が A を、/Application2 が B を使用するように構成します。  
  
 Web.config を使用して、一時フォルダーを構成できる\< system.web/compilation/@tempFolder>。 /Application1、"c:\tempForUser1"であることができ、アプリケーション 2 の"c:\tempForUser2"であることができます。 これらのフォルダーに対応する書き込みアクセス許可を 2 つの ID に与えます。  
  
 これで、user2 は、(c:\tempForUser1 の下にある) /Application2 のコード生成フォルダーを変更できなくなります。  
  
## <a name="enabling-asynchronous-processing"></a>非同期処理の有効化  
 既定では、IIS 6.0 であること、およびそれ以前にホストされる WCF サービスに送信されたメッセージに同期的に処理されます。 ASP.NET が独自のスレッド (ASP.NET のワーカー スレッド) で WCF を呼び出すし、WCF では、別のスレッドを使用して要求を処理します。 WCF は、その処理が完了するまで ASP.NET のワーカー スレッドに保持されます。 このため、要求は同期的に処理されます。 – WCF を保持しません ASP.NET のスレッドを要求の処理中の要求を処理するために必要なスレッドの数が減るために、スケーラビリティを要求を非同期的に処理できます。 入力方向の要求をサーバー上で開くことを調整する方法がないために、IIS 6.0 を実行しているマシンの非同期動作の使用は推奨されません*Denial Of Service* (DOS) 攻撃です。 IIS 7.0 以降では、同時要求スロットルが導入されています: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`。 この新しいスロットルにより、非同期処理を安全に使用することができます。  IIS 7.0 の既定では、非同期のハンドラーとモジュールが登録されます。 この機能が無効になっている場合は、アプリケーションの Web.config ファイルで要求の非同期処理を手動で有効にすることができます。 使用する設定は、`aspNetCompatibilityEnabled` 設定によって異なります。 `aspNetCompatibilityEnabled` を `false` に設定している場合は、次の構成スニペットに示すように、`System.ServiceModel.Activation.ServiceHttpModule` を構成します。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />      
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"   
           preCondition="integratedMode,runtimeVersionv2.0"   
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 `aspNetCompatibilityEnabled` を `true` に設定している場合は、次の構成スニペットに示すように、`System.ServiceModel.Activation.ServiceHttpHandlerFactory` を構成します。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />      
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"   
               path="*.svc"   
               verb="*"   
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"           
               />  
    </handlers>      
  </system.webServer>  
```  
  
## <a name="see-also"></a>関連項目  
 [サービス ホスト サンプル](http://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
