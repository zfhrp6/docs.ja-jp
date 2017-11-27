---
title: "アドインおよび拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd09d0da70869ba193b414d8a2ce6c25cbb6b38
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="add-ins-and-extensibility"></a>アドインおよび拡張機能
<a name="top"></a> アドインには、ホスト アプリケーションのための拡張機能またはサービスが用意されています。 開発者は、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のプログラミング モデルを使用してアドインを開発し、ホスト アプリケーションでそれらをアクティブ化できます。 こうした機能は、このモデルで、ホストとアドインの間に通信パイプラインを構築することによって実現します。 このモデルは、 <xref:System.AddIn>、 <xref:System.AddIn.Hosting>、 <xref:System.AddIn.Pipeline>、 <xref:System.AddIn.Contract> の各名前空間の型を使用することによって実装されます。  
  
 この概要は、次のセクションで構成されています。  
  
-   [アドイン モデル](#addin_model)  
  
-   [アドインとホストの違い](#distinguishing_between_addins_and_hosts)  
  
-   [関連トピック](#related_topics)  
  
-   [参照](#reference)  
  
> [!NOTE]
>  CodePlex の「 [Managed Extensibility and Add-In Framework](http://go.microsoft.com/fwlink/?LinkId=121190)」 (管理された拡張機能およびアドイン フレームワーク) サイトには、その他のサンプル コードや、アドイン パイプラインのビルドに使用するツールのカスタマー テクノロジ プレビューが掲載されています。  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>アドイン モデル  
 アドイン モデルは、アドイン パイプライン (通信パイプラインとも呼ばれます) を構成する一連のセグメントで構成されます。アドイン パイプラインにより、アドインとホストの間の全通信がなされます。 このパイプラインは、アドインとそのホスト間でデータを交換するセグメントの対称通信モデルです。 ホストとアドインの間にこのようなセグメントを開発することで、アドインのバージョン管理と分離をサポートするために必要な抽象化レイヤーが得られます。  
  
 次の図に、そのパイプラインを示します。  
  
 ![追加 (& a) #45; パイプライン モデル。] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
アドイン パイプライン  
  
 これらのセグメントのアセンブリが、同じアプリケーション ドメインに含まれている必要はありません。 専用の新規アプリケーション ドメイン、既存のアプリケーション ドメイン、さらにはホストのアプリケーション ドメインにも、アドインを読み込むことができます。 同じアプリケーション ドメインに複数のアドインを読み込むことができます。これにより、リソースとセキュリティ コンテキストを他のアドインと共有できます。  
  
 アドイン モデルでは、ホストとアドインの間に分離境界 (またはリモート境界) と呼ばれるオプションの境界がサポートされており、この使用をお勧めします。 この境界をアプリケーション ドメインやプロセス境界に設定できます。  
  
 パイプラインの中間にあるコントラクト セグメントは、ホストのアプリケーション ドメインとアドインのアプリケーション ドメインの両方に読み込まれます。 コントラクトにより、ホストとアドインで相互に型を交換するために使用される仮想メソッドが定義されます。  
  
 分離境界を通過して型を渡すには、型がコントラクトかシリアル化できる型である必要があります。 コントラクトやシリアル化できる型でない型は、パイプラインのアダプター セグメントでコントラクトに変換する必要があります。  
  
 パイプラインのビュー セグメントは、コントラクトの定義に従って、ホストとアドインに共有メソッドのビューを提供する抽象基本クラスまたはインターフェイスです。  
  
 パイプライン セグメントの開発の詳細については、「 [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md)」を参照してください。  
  
 以降のセクションでは、アドイン モデルの機能について説明します。  
  
### <a name="independent-versioning"></a>独立バージョン管理  
 アドイン モデルを使用して、ホストとアドインを別々にバージョン管理できます。 つまり、アドイン モデルでは次のシナリオが有効です。  
  
-   ホストが、以前のバージョンのホスト用にビルドされたアドインを使用できるようにするアダプターの作成。  
  
-   ホストが、ホストの最新バージョンのホスト用にビルドされたアドインを使用できるようにするアダプターの作成。  
  
-   ホストが、異なるホスト用にビルドされたアドインを使用できるようにするアダプターの作成。  
  
### <a name="discovery-and-activation"></a>探索とアクティブ化  
 情報ストアに格納されている、アドインを表すコレクション内のトークンを使用して、アドインをアクティブにすることができます。 アドインは、アドインのホストのビューを定義する型によって検索されます。 アドインを定義する型によって、特定のアドインを検索することもできます。 情報ストアは、パイプライン ストアとアドイン ストアの 2 つのキャッシュ ファイルで構成されます。  
  
 情報ストアの更新とリビルドの詳細については、「 [アドイン探索](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421)」を参照してください。 アドインのアクティブ化の詳細については、「 [アドインのアクティブ化](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) 」および「 [方法: さまざまな分離とセキュリティに合わせてアドインをアクティブにする](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5)」を参照してください。  
  
### <a name="isolation-levels-and-external-processes"></a>分離レベルと外部プロセス  
 アドイン モデルでは、アドインとホスト間、アドインと他のアドイン間について、複数の分離レベルがサポートされます。分離レベルの低いものから順に、次のレベルがあります。  
  
-   アドインが、ホストと同じアプリケーション ドメインで実行される。 この場合、さまざまなアプリケーション ドメインを使用することで得られる分離とアンロードの機能が使用できなくなるため、このレベルは推奨されません。  
  
-   ホストで使用されるアプリケーション ドメインとは異なる 1 つのアプリケーション ドメインに、複数のアドインが読み込まれる。  
  
-   それぞれのアドインが専用のアプリケーション ドメインに排他的に読み込まれる。 これが最も一般的な分離レベルです。  
  
-   外部プロセスの同じアプリケーション ドメインに複数のアドインが読み込まれる。  
  
-   外部プロセスの専用のアプリケーション ドメインに、それぞれのアドインが排他的に読み込まれる。 これが最も分離レベルの高いシナリオです。  
  
 外部プロセスの使用の詳細については、「 [方法: さまざまな分離とセキュリティに合わせてアドインをアクティブにする](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5)」を参照してください。  
  
### <a name="lifetime-management"></a>有効期間管理  
 アドイン モデルはアプリケーション ドメインとプロセス境界を横断するため、オブジェクトの解放と再要求を実行するにはガベージ コレクションだけでは不十分です。 アドイン モデルには、トークンと参照カウントを使用した有効期間管理機能があるため、通常は追加のプログラミングは必要ありません。 詳細については、「 [有効期間管理](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)」を参照してください。  
  
 [ページのトップへ](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>アドインとホストの違い  
 アドインとホストの違いは、アドインをアクティブにするものがホストであるということのみです。 ホストは、2 つのうち大きな方であることもあれば (ワード プロセッシング アプリケーションとスペル チェック機能の場合など)、小さな方であることもあります (メディア プレーヤーを埋め込んだインスタント メッセージング クライアントの場合など)。 アドイン モデルでは、クライアントとサーバーの両方のシナリオでアドインがサポートされます。 サーバー アドインの例としては、電子メール サーバーにウイルス スキャン、スパム フィルター、IP 保護を適用するアドインなどがあります。 クライアント アドインの例としては、ワード プロセッサ向けの参照アドイン、グラフィック プログラムやゲームなどの特殊機能、ローカルの電子メール クライアント用のウイルス スキャン機能などがあります。  
  
 [ページのトップへ](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md)|ホスト アプリケーションからアドインへのセグメントの通信パイプラインについて説明します。 チュートリアルのトピックでは、コード例を示して、パイプラインの構築方法と、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]のパイプラインへのセグメントの配置方法について説明しています。|  
|[アプリケーション ドメインとアセンブリ](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|セキュリティ、信頼性、バージョン管理、およびアセンブリのための分離の境界を提供するアプリケーション ドメイン間の関係について説明します。|  
  
 [ページのトップへ](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>参照  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [ページのトップへ](#top)