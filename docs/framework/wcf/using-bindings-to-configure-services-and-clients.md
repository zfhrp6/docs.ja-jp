---
title: サービスとクライアントを構成するためのバインディングの使用
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 8271f51885c0d7800d26018b94942a7d832bf4a5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806072"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>サービスとクライアントを構成するためのバインディングの使用
バインディングとは、エンドポイントへの接続に必要な通信の詳細設定を指定するオブジェクトです。 具体的には、バインディングには構成情報が含まれており、この情報を使用してそれぞれのエンドポイントまたはクライアント チャネルで使用されるトランスポート仕様、ワイヤ形式 (メッセージ エンコード) 仕様、プロトコル仕様が定義され、クライアントまたはサービスのランタイムが作成されます。 機能している Windows Communication Foundation (WCF) サービスを作成するには、サービス内の各エンドポイントには、バインディングが必要です。 ここでは、エンドポイントにおけるバインディングの概要と定義方法、特定のバインディングの指定方法を説明します。  
  
## <a name="what-a-binding-defines"></a>バインディングの定義内容  
 バインディングの情報は、非常に基本的な情報にすることも複雑なものにすることもできます。 最も基本的なバインディングはトランスポート プロトコル (HTTP など) のみを指定したもので、これはエンドポイントへの接続に必ず使用します。 一般的に、バインディングに含まれるエンドポイントへの接続方法を示す情報は、次のカテゴリのいずれかに当てはまります。  
  
 プロトコル  
 使用されているセキュリティ機構 (信頼性の高いメッセージング機能またはトランザクション コンテキストのフロー設定のいずれか) を決定します。  
  
 Transport  
 使用する基本のトランスポート プロトコル (TCP や HTTP など) を決定します。  
  
 エンコーディング  
 メッセージ エンコード (Text/XML、バイナリ、MTOM (Message Transmission Optimization Mechanism) など) を決定します。これは、メッセージをネットワーク上のバイト ストリームとしてどのように表現するかを決定します。  
  
## <a name="system-provided-bindings"></a>システム標準のバインディング  
 WCF には、ほとんどのアプリケーションの要件とシナリオをカバーするように設計されたシステム指定のバインディングのセットが含まれています。 システム指定のバインディングの例のいくつかを次のクラスで示します。  
  
-   <xref:System.ServiceModel.BasicHttpBinding> : WS-I Basic Profile 1.1 仕様に準拠する Web サービス (ASP.NET Web サービス (ASMX) ベースのサービスなど) への接続に適した HTTP プロトコル バインディング。  
  
-   <xref:System.ServiceModel.WSHttpBinding> : Web サービス仕様のプロトコルに準拠するエンドポイントへの接続に適した HTTP プロトコル バインディング。  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: 同じコンピューター上の他の WCF エンドポイントへの接続に .NET binary エンコードとフレーム技術組み合わせて windows 名前付きパイプ トランスポートを使用します。  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: 接続を作成するキューに置かれたメッセージを他の WCF エンドポイントと .NET binary エンコードとフレーム技術メッセージ キュー (MSMQ とも呼ばれます) と組み合わせてを使用します。  
  
 詳細についてでのシステム指定のバインディングの完全な一覧については、次を参照してください。[システム指定のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)です。  
  
## <a name="custom-bindings"></a>カスタム バインディング  
 システム指定のバインディング コレクションに、サービス アプリケーションに必要な機能の適切な組み合わせが含まれていない場合は、<xref:System.ServiceModel.Channels.CustomBinding> バインディングを作成できます。 要素の詳細については、<xref:System.ServiceModel.Channels.CustomBinding>バインドを参照してください[ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)と[カスタム バインディング](../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
## <a name="using-bindings"></a>バインディングの使用  
 バインディングを使用する際には、次の 2 つの基本手順があります。  
  
1.  バインディングを選択、または定義します。 最も簡単な方法は、システム指定のバインディングを 1 つ選択し、それを既定の設定で使用することです。 また、システム指定のバインディングを選択し、そのプロパティを要件に適した値に再設定することもできます。 さらに、カスタム バインディングを作成し、すべてのプロパティを必要に応じて設定することもできます。  
  
2.  このバインディングを使用するエンドポイントを作成します。  
  
## <a name="code-and-configuration"></a>コードおよび構成  
 バインディングは、コードまたは構成を使用して定義または構成できます。 この 2 つの方法は使用するバインディングの種類に依存しません。たとえば、システム指定のバインディングまたは <xref:System.ServiceModel.Channels.CustomBinding> バインディングのどちらを使用していても関係ありません。 一般に、コードを使用すると、コンパイル時に開発者がバインディングの定義を完全に制御できます。 構成を使用する一方で、使用するには、システム管理者または WCF サービス、バインディングのパラメーターを変更するクライアントのユーザー。 この柔軟性がネットワーク WCF アプリケーションの展開条件や、特定のマシンの要件を予測する方法がありませんが多くの場合、ことをお勧めします。 バインディング (およびアドレス) 情報がコードから分離されているため、管理者はアプリケーションの再コンパイルや再配置を行わずにバインディングの詳細を変更できます。 バインディングをコードに定義した場合、構成ファイルに記述されている構成ベースの定義はすべて上書きされます。 この方法についての例は、以下のトピックを参照してください。  
  
-   [方法: マネージ アプリケーションで WCF サービスをホスト](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)コード内のバインディングを作成する例を示します。  
  
-   [方法: クライアントを構成する](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)の構成を使用してクライアントを作成する例を示します。  
  
## <a name="see-also"></a>関連項目  
 [エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [方法: 構成でサービス バインディングを指定する](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [方法: コード内でサービス バインディングを指定する](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)  
 [方法: 構成でクライアント バインディングを指定する](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
 [方法: コード内でクライアント バインディングを指定する](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
