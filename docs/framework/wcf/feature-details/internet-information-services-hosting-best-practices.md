---
title: "インターネット インフォメーション サービス ホスティングのベスト プラクティス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8593b9ceb579f33ba3b37975d88b37f3f5ab628
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="internet-information-services-hosting-best-practices"></a>インターネット インフォメーション サービス ホスティングのベスト プラクティス
このトピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスのホスティングに関するベスト プラクティスについて概説します。  
  
## <a name="implementing-wcf-services-as-dlls"></a>WCF サービスの DLL としての実装  
 Web アプリケーションの \bin ディレクトリに展開される DLL として [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを実装すると、Web アプリケーション モデルの外部 (IIS を展開できないテスト環境など) でサービスを再利用できるようになります。  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS でホストされるアプリケーションでのサービス ホスト  
 IIS ホスト環境によってネイティブにサポートされていないネットワーク トランスポートで待機する新しいサービス ホストを作成する場合は、強制自己ホスト API を使用しないでください (たとえば、TCP サービスをホストする [!INCLUDE[iis601](../../../../includes/iis601-md.md)]。TCP 通信は、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] でネイティブにサポートされていません)。 この方法はお勧めしません。 強制的に作成されたサービス ホストは、IIS ホスト環境内で認識されないからです。 重要な点は、IIS がホスト アプリケーション プールがアイドル状態であるかどうかを判断するときに、強制的に作成されたサービスによって実行される処理が IIS によって考慮されないことです。 この結果、強制的に作成されたサービス ホストを持つアプリケーションは、IIS ホスト プロセスを積極的に廃棄する IIS ホスト環境を持つことになります。  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI と IIS でホストされるエンドポイント  
 IIS でホストされるサービスのエンドポイントは、絶対アドレスではなく、相対 URI (Uniform Resource Identifier) を使用して構成する必要があります。 これにより、エンドポイント アドレスが、ホスト アプリケーションに属する URI アドレスのセット内に確実に含まれ、メッセージに基づくアクティベーションが正常に行われるようになります。  
  
## <a name="state-management-and-process-recycling"></a>状態管理とプロセスのリサイクル  
 IIS ホスト環境は、メモリにローカル状態を保持しないサービスに最適化されています。 IIS は、さまざまな外部および内部イベントに応答してホスト プロセスをリサイクルするため、メモリのみに格納される揮発性の状態はすべて失われます。 IIS でホストされるサービスは、それぞれの状態をプロセスの外部 (データベースなど)、またはアプリケーションのリサイクル イベントが発生した場合に簡単に再作成できるメモリ内キャッシュに格納する必要があります。  
  
> [!NOTE]
>  メッセージ レイヤーの信頼性とセキュリティを確保するために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって使用されるプロトコルは、揮発性のメモリ内状態を利用します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるセッションとセキュリティ セッションは、アプリケーションのリサイクルにより、予期しないときに終了する場合があります。 これらのプロトコルを利用する、IIS でホストされるアプリケーションでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって提供されるセッション キー以外の要素 (アプリケーション レイヤー構造やカスタム相関ヘッダーなど) に依存してアプリケーション レイヤーの状態を関連付けるか、ホストされるアプリケーションでの IIS プロセスのリサイクルを無効にする必要があります。  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>中間層シナリオでのパフォーマンスの最適化  
 最適なパフォーマンス、*中間層シナリオ*— 受信メッセージに応答の他のサービスを呼び出すサービス-インスタンスを作成、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 1 回、リモート サービスへのクライアントのサービスを提供し、複数再利用受信要求します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス クライアントのインスタンス化は、既存のクライアント インスタンスでのサービスの呼び出しに比べて負荷のかかる処理ですが、中間層シナリオでは、要求全体でリモート クライアントをキャッシュすることで、パフォーマンスが大幅に向上します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス クライアントはスレッド セーフであるため、複数のスレッドにわたってクライアントへのアクセスを同期する必要がありません。  
  
 また、中間層シナリオでは、`svcutil /a` オプションによって生成された非同期 API を使用してパフォーマンスを向上させます。 `/a`オプションを指定、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を生成する`BeginXXX/EndXXX`呼び出せる可能性のある実行の時間の長いリモート サービスで行われるサービス操作ごとにメソッドバック グラウンド スレッドです。  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>マルチホーム シナリオまたはマルチネーム シナリオでの WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、複数のコンピューターが共通の外部名 (http://www.contoso.com など) を共有していても、異なるホスト名によって個別にアドレス指定される (たとえば、http://www.contoso.com により、http://machine1.internal.contoso.com および http://machine2.internal.contoso.com という 2 台のコンピューターにトラフィックが送られる場合など) IIS Web ファームの内部に展開できます。 この展開シナリオは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって完全にサポートされますが、正確な (外部) ホスト名がサービスのメタデータ (Web サービス記述言語) に表示されるように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする IIS Web サイトを特別に構成する必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって生成されたサービス メタデータに正確なホスト名が確実に表示されるように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする IIS Web サイトの既定 ID を構成して、明示的なホスト名を使用します。 たとえば、www.contoso.com ファームの内部に存在するコンピューターがの IIS サイト バインディングを使用する必要があります * http:80:www.contoso.com と\*: 443:www.contoso.com HTTPS 用です。  
  
 Microsoft 管理コンソール (MMC) スナップインを使用して、IIS Web サイト バインディングを構成できます。  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>異なるユーザー コンテキストで実行されるアプリケーション プールが、一時フォルダー内の他のアカウントのアセンブリを上書きする  
 異なるユーザー コンテキストで実行されているアプリケーション プールが、一時的な [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ファイル フォルダー内の他のアカウントのアセンブリを上書きできないようにするには、アプリケーションごとに個別の ID と一時フォルダーを使用します。 たとえば、/Application1 と /Application2 という 2 つの仮想アプリケーションがある場合は、2 つの異なる ID を使用して、A と B の 2 つのアプリケーション プールを作成できます。 アプリケーション プール A は、一方のユーザー ID (user1) の下で、アプリケーション プール B は、もう一方のユーザー ID (user2) の下で実行でき、/Application1 が A を、/Application2 が B を使用するように構成します。  
  
 Web.config を使用して、一時フォルダーを構成できる\< system.web/compilation/@tempFolder>。 /Application1、"c:\tempForUser1"であることができ、アプリケーション 2 の"c:\tempForUser2"であることができます。 これらのフォルダーに対応する書き込みアクセス許可を 2 つの ID に与えます。  
  
 これで、user2 は、(c:\tempForUser1 の下にある) /Application2 のコード生成フォルダーを変更できなくなります。  
  
## <a name="enabling-asynchronous-processing"></a>非同期処理の有効化  
 既定では、IIS 6.0 以前でホストされている [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス宛てのメッセージは同期的に処理されます。 ASP.NET は、独自のスレッド (ASP.NET のワーカー スレッド) で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を呼び出し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は別のスレッドを使用してその要求を処理します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、その処理が完了するまで ASP.NET のワーカー スレッドに保持されます。 このため、要求は同期的に処理されます。 要求を非同期で処理すると、要求の処理に必要なスレッド数が減るため、優れたスケーラビリティが得られます。つまり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、要求の処理中に ASP.NET のスレッドで保持されません。 入力方向の要求をサーバー上で開くことを調整する方法がないために、IIS 6.0 を実行しているマシンの非同期動作の使用は推奨されません*Denial Of Service* (DOS) 攻撃です。 IIS 7.0 以降では、同時要求スロットルが導入されています`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`。 この新しいスロットルにより、非同期処理を安全に使用することができます。  IIS 7.0 の既定では、非同期のハンドラーとモジュールが登録されます。 この機能が無効になっている場合は、アプリケーションの Web.config ファイルで要求の非同期処理を手動で有効にすることができます。 使用する設定は、`aspNetCompatibilityEnabled` 設定によって異なります。 `aspNetCompatibilityEnabled` を `false` に設定している場合は、次の構成スニペットに示すように、`System.ServiceModel.Activation.ServiceHttpModule` を構成します。  
  
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
  
## <a name="see-also"></a>参照  
 [サービス ホスト サンプル](http://msdn.microsoft.com/en-us/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
