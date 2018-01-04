---
title: "はじめに Tutorial1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 182e82eec107c170a793d0d48bcfe5493c04d618
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-tutorial"></a>チュートリアル入門
このセクションの各トピックで、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] のプログラミング方法について簡単に説明します。 これらは、このトピックに記載されているリストの順番どおりに完了するように設計されています。 このチュートリアルを通じて [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスおよびクライアント アプリケーションの作成に必要な手順について理解することができます。 サービスは 1 つ以上のエンドポイントを公開し、それぞれのエンドポイントは 1 つ以上のサービス操作を公開します。 *エンドポイント*サービスのアドレス、サービスがある、クライアントは、サービスと機能を定義するコントラクトと通信する必要がある方法を説明する情報を含んでいるバインディングを指定します。クライアントにサービスによって提供されます。  
  
 このチュートリアルの一連のトピックを終了すると、サービスを実行し、クライアントからそのサービスを呼び出すことができるようになります。 最初の 3 つのトピックでは、サービス コントラクトを定義する方法、サービス コントラクトを実装する方法、およびサービスをホストする方法について説明します。 作成したサービスは、コンソール アプリケーション内で自己ホストされます。 また、サービスは、インターネット インフォメーション サービス (IIS) でホストすることもできます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]を参照してください方法[する方法: IIS で WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)です。 サービスはコードで構成されますが、構成ファイル内で構成することもできます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]構成ファイルを使用して参照してください[構成ファイルを使用してサービスを構成する](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)です。  
  
 次の 3 つのトピックでは、クライアント プロキシを作成する方法、クライアント アプリケーションを構成する方法、およびサービスが公開するサービス操作をクライアント プロキシを使って呼び出す方法について説明します。 サービスは、クライアント アプリケーションがサービスと通信するために必要な情報を定義したメタデータを公開します。 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] は、このメタデータにアクセスするプロセスを自動化し、それを使って、サービスのクライアント アプリケーションを構築および構成します。 使用していない場合[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]、使用することができます、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を構築し、サービスのクライアント アプリケーションを構成します。  
  
 このセクションのすべてのトピックでは、開発環境として Visual Studio 2011 を使用することを前提としています。 他の開発環境を使用する場合は、[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] に固有の指示については無視してください。  
  
> [!NOTE]
>  実行する場合は[!INCLUDE[wv](../../../includes/wv-md.md)]または開始する必要があります以降のバージョンの Windows オペレーティング システムでは、[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]しようとして、[スタート] メニュー、Visual Studio 2011 を右クリックしを選択して**管理者として実行**です。 ショートカットを作成のショートカットを右クリックして、プロパティを選択して、選択、管理者として Visual Studio 2011 を常に起動する、**互換性**タブをクリックし、確認、 **管理者としてこのプログラムを実行**チェック ボックスをオンします。 このショートカットで Visual Studio 2011 を起動すると、常に管理者として実行されます。  
  
 ハード_ディスクにダウンロードできますして実行する場合は、トピックを参照して、サンプル アプリケーションの[Windows Communication Foundation サンプル](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)です。 このトピックを参照してください、具体的には、[作業の開始](../../../docs/framework/wcf/samples/getting-started-sample.md)です。  
  
 サービスとクライアントの作成に関する詳細の詳細については、次を参照してください。[基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: サービス コントラクトを定義する](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 ユーザー定義のインターフェイスを使用して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] コントラクトを作成する方法について説明します。 コントラクトは、サービスが公開する機能を定義します。  
  
 [方法: サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 サービス コントラクトを実装する方法について説明します。 定義したコントラクトはサービスのクラスと共に実装する必要があります。  
  
 [方法: 基本的なサービスをホストおよび実行する](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 サービスのエンドポイントをコードで構成する方法と、コンソール アプリケーションでサービスをホストする方法について説明します。 サービスをアクティブにするには、サービスをランタイム環境内で構成してホストする必要があります。 この環境によってサービスが作成され、サービスのコンテキストと有効期間が制御されます。  
  
 [方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスから [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント プロキシを作成するために使用するメタデータを取得する方法について説明します。 このプロセスでは、Visual Studio 2011 の "サービス参照の追加" 機能を使用します。  
  
 [方法: クライアントを構成する](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 WCF クライアントの構成方法について説明します。クライアントを構成するには、クライアントがサービスへのアクセスに使用するエンドポイントを指定する必要があります。  
  
 [方法: クライアントを使用する](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント プロキシを使用してサービス操作を呼び出す方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>関連項目  
 [Windows Communication Foundation サンプル](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [基本的なプログラミング ライフサイクル](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>参照  
 [概念](../../../docs/framework/wcf/conceptual-overview.md)  
 [ドキュメントのガイド](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Windows Communication Foundation とは](../../../docs/framework/wcf/whats-wcf.md)  
 [WCF 機能の詳細](../../../docs/framework/wcf/feature-details/index.md)
