---
title: ホスティング サービス
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: d4fb974cdfec87606f13b5cbd83be2c86f2a1ae5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807854"
---
# <a name="hosting-services"></a>ホスティング サービス
アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。 Windows Communication Foundation (WCF) サービスは、マネージ コードをサポートする任意の Windows プロセスで実行する設計されています。  
  
 WCF には、サービス指向アプリケーションを構築するための統一されたプログラミング モデルが用意されています。 このプログラミング モデルには一貫性があり、サービスが展開されるランタイム環境に影響されません。 これは実際には、ホスト オプションにかかわらず、サービスのコードがほぼ同じになることを意味しています。  
  
 これらのホスト オプションの範囲は、コンソール アプリケーション内部での実行から、Windows サービスのようなサーバー環境、インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行までさまざまです。 開発者は、サービスの展開要件を満たすホスト環境を選択します。 このような要件は、アプリケーションを展開するプラットフォーム、メッセージの送受信を行うトランスポート、適切な可用性を保証するために必要なプロセスのリサイクルや管理、その他、管理上または信頼性上の要件から導き出されます。 ホスト オプションの情報とガイドラインについて、次のセクションで説明します。  
  
## <a name="hosting-options"></a>ホスト オプション  
  
#### <a name="self-hosting-in-a-managed-application"></a>マネージ アプリケーションにおける自己ホスト  
 任意のマネージ アプリケーションでは、WCF サービスをホストすることができます。 これは、展開に必要なインフラストラクチャが最小限になるため、最も柔軟なオプションです。 マネージ アプリケーション コード内にサービスのコードを埋め込み、続いて <xref:System.ServiceModel.ServiceHost> のインスタンスを作成して開き、サービスを有効にします。 詳細については、次を参照してください。[する方法: マネージ アプリケーションで WCF サービスをホスト](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)です。  
  
 このオプションにより、2 つの一般的なシナリオ: Windows Presentation Foundation (WPF) または Windows フォーム (WinForms) に基づいて、WCF サービスのコンソール アプリケーションとなどのリッチ クライアント アプリケーション内で実行中です。 アプリケーションの開発フェーズ中には、通常は役にはコンソール アプリケーション内部の WCF サービスをホストしているです。 コンソール アプリケーションにより、アプリケーション内部で起こっている状況を見極めるための情報のデバッグやトレースが容易になり、新しい場所にアプリケーションをコピーして移動することも簡単に行うことができます。 このホスト オプションを使用すると、 [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] や WinForms アプリケーションなど、外部と通信を行うリッチ クライアント アプリケーションの作成も容易になります。 など、ピア ツー ピア コラボレーションのクライアントを使用する[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]ユーザー インターフェイスにし、また他のクライアントに接続して、情報を共有できるようにする WCF サービスをホストします。  
  
#### <a name="managed-windows-services"></a>マネージ Windows サービス  
 このホスト オプションがいるため、サービスのプロセス有効期間はサービス コントロール マネージャー (SCM) によって制御されます (旧 NT サービス) をマネージ Windows サービスとして WCF サービスをホストするアプリケーション ドメイン (AppDomain) に登録することで構成されていますWindows サービスです。 自己ホスト オプションと同様、この種類のホスト環境では、ホスト コードをアプリケーションの一部として記述する必要があります。 サービスは Windows サービスとして、実装、WCF サービスとしてから継承することによって、<xref:System.ServiceProcess.ServiceBase>クラスだけでなく、WCF のサービス コントラクト インターフェイスを提供します。 次に <xref:System.ServiceModel.ServiceHost> を作成し、オーバーライドされた <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドで開き、オーバーライドされた <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドで閉じます。 また、 <xref:System.Configuration.Install.Installer> から継承されるインストーラー クラスも実装し、プログラムが Installutil.exe ツールによって Windows サービスとしてインストールされるようにする必要があります。 詳細については、次を参照してください。[する方法: マネージ Windows サービスで WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)です。 マネージ Windows サービスのホスト オプションによって有効になっているシナリオは、実行時間の長い WCF サービスがメッセージにアクティブになっているセキュリティで保護された環境では、IIS の外部でホストされているのです。 サービスの有効期限は代わりにオペレーティング システムによって制御されます。 このホスト オプションは Windows のすべてのバージョンで使用できます。  
  
#### <a name="internet-information-services-iis"></a>インターネット インフォメーション サービス (IIS)  
 IIS ホスト オプションは [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] と統合され、プロセスのリサイクル、アイドル シャットダウン、処理状況の監視、メッセージに基づくアクティベーションなど、このテクノロジによって提供される機能を使用します。 [!INCLUDE[wxp](../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] オペレーティング システムでは、高可用性と高スケーラビリティが求められる Web サービス アプリケーションのホストには、このオプションが適切なソリューションとなります。 IIS では、顧客がエンタープライズ クラスのサーバー製品に求める統合された管理性も提供されます。 このホスト オプションでは、IIS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。 IIS を構成する方法の詳細については、WCF サービスをホストする参照してください[する方法: IIS で WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)です。  
  
 IIS でホストされるサービスは HTTP トランスポートしか使用できません。 IIS 5.1 の実装では、 [!INCLUDE[wxp](../../../includes/wxp-md.md)]にいくつかの制限がありました。 上で WCF サービスの IIS 5.1 によって提供されるメッセージに基づくアクティベーション[!INCLUDE[wxp](../../../includes/wxp-md.md)]からの通信にポート 80 を使用して同じコンピューター上の他の自己ホスト型 WCF サービスをブロックします。 WCF サービスによってホストされている場合は、他のアプリケーションと同じ AppDomain/アプリケーション プール/ワーカー プロセスで実行できます[!INCLUDE[iis601](../../../includes/iis601-md.md)]で[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]です。 が、WCF と[!INCLUDE[iis601](../../../includes/iis601-md.md)]どちらもカーネル モードの HTTP スタック (HTTP.sys) を使用する[!INCLUDE[iis601](../../../includes/iis601-md.md)]IIS 5.1 とは異なり、同じコンピューターで実行されている他の自己ホスト型 WCF サービスとポート 80 を共有することができます。  
  
#### <a name="windows-process-activation-service-was"></a>Windows プロセス アクティブ化サービス (WAS)  
 Windows プロセス アクティブ化サービス (WAS) とは、 [!INCLUDE[lserver](../../../includes/lserver-md.md)] でも使用できる [!INCLUDE[wv](../../../includes/wv-md.md)]用の新しいプロセス アクティブ化機構です。 よく知られている [!INCLUDE[iis601](../../../includes/iis601-md.md)] のプロセス モデル (アプリケーション プールとメッセージ ベースのプロセス アクティベーション) とホスト機能 (迅速な障害保護、状態の監視、プロセスのリサイクルなど) はそのままですが、HTTP に対する依存性がアクティベーション アーキテクチャから解消されています。 [!INCLUDE[iisver](../../../includes/iisver-md.md)] では、WAS を使用して HTTP 経由でのメッセージ ベースのアクティベーションを実現しています。 追加の WCF コンポーネントは、TCP、MSMQ、名前付きパイプなど、WCF をサポートするその他のプロトコルを介してメッセージ ベースのアクティブ化を提供する、WAS にも接続します。 これにより、IIS のプロセスのリサイクル、迅速な障害保護、一般的な構成システムなど、これまで HTTP ベースのアプリケーションのみで利用可能だった IIS 機能を、通信プロトコルを使用するアプリケーションでも使用できるようになりました。  
  
 このホスト オプションでは、WAS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。 構成する方法の詳細についてをホストしていたは、次を参照してください。[する方法: WAS で WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)です。  
  
## <a name="choosing-a-hosting-environment"></a>ホスト環境の選択  
 次の表に、各ホスト オプションに関連する主な利点とシナリオの要点をまとめます。  
  
|ホスト環境|一般的なシナリオ|主な利点と制限|  
|-------------------------|----------------------|----------------------------------|  
|マネージ アプリケーション ("自己ホスト")|コンソール アプリケーションの開発時に使用します。<br />-リッチな WinForm と[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]サービスにアクセスするクライアント アプリケーション。|柔軟なです。<br />展開が容易です。<br />-サービスのエンタープライズ ソリューションです。|  
|Windows サービス (従来 NT サービスと呼ばれていたもの)|-IIS の外部でホストされている実行時間の長い WCF サービス。|サービス プロセスの有効期間がないメッセージでアクティブ化される、オペレーティング システムによって制御されます。<br />-すべてのバージョンの Windows でサポートされています。<br />環境をセキュリティで保護します。|  
|IIS 5.1、 [!INCLUDE[iis601](../../../includes/iis601-md.md)]|のサイド バイ サイドで WCF を実行しているサービス[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]HTTP プロトコルを使用してインターネット上のコンテンツ。|プロセスをリサイクルします。<br />-アイドル シャット ダウンします。<br />-正常性の監視を処理します。<br />-メッセージ ベースのアクティブ化します。<br />HTTP のみ。|  
|Windows プロセス アクティブ化サービス (WAS)|-さまざまなトランスポート プロトコルを使用してインターネットに IIS をインストールしなくても、WCF サービスを実行します。|IIS は必要ありません。<br />プロセスをリサイクルします。<br />-アイドル シャット ダウンします。<br />-正常性の監視を処理します。<br />-メッセージ ベースのアクティブ化します。<br />-HTTP、TCP、名前付きパイプ、および MSMQ で動作します。|  
|IIS 7.0|のサービス WCF を実行している[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]コンテンツ。<br />-さまざまなトランスポート プロトコルを使用してインターネットで WCF サービスを実行します。|-がの利点があります。<br />-統合された[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]および IIS コンテンツ。|  
  
 ホスト環境の選択は、その展開先の Windows のバージョン、メッセージの送信に必要なトランスポート、および必要となるプロセスとアプリケーション ドメインのリサイクルの種類に依存します。 次の表に、これらの要件に関連するデータをまとめます。  
  
|ホスト環境|プラットフォームの可用性|サポートされるトランスポート|プロセスと AppDomain のリサイクル|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|マネージ アプリケーション ("自己ホスト")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|×|  
|Windows サービス (従来 NT サービスと呼ばれていたもの)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|×|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|[はい]|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|[はい]|  
|Windows プロセス アクティブ化サービス (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|[はい]|  
  
 信頼されていないホストからサービスや拡張機能を実行すると、セキュリティが損なわれるので注意してください。 また、偽装して <xref:System.ServiceModel.ServiceHost> を開くと、アプリケーションは、ユーザーの <xref:System.Security.Principal.WindowsIdentity> をキャッシュするなどして、ユーザーがログオフしていないことを確認する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [システム要件](../../../docs/framework/wcf/wcf-system-requirements.md)  
 [基本的なプログラミング ライフサイクル](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [方法 : IIS で WCF サービスをホストする](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [方法 : WAS で WCF サービスをホストする](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [方法 : マネージ Windows サービスで WCF サービスをホストする](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [方法: マネージ アプリケーションで WCF サービスをホストする](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
