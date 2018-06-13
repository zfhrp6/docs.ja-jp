---
title: 'エンドポイント : アドレス、バインディング、およびコントラクト'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 0909d1d10ab8932f27f7ca6cba6207d57fa4f4cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493749"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>エンドポイント : アドレス、バインディング、およびコントラクト
使用して、Windows Communication Foundation (WCF) サービスとすべての通信が行われる、*エンドポイント*サービス。 エンドポイントは、WCF サービスによって提供される機能へのアクセスをクライアントに提供します。  
  
 各エンドポイントは、次の 4 つのプロパティで構成されます。  
  
-   そのエンドポイントの場所を示すアドレス。  
  
-   クライアントがエンドポイントと通信する方法を指定するバインディング。  
  
-   利用可能な操作を識別するためのコントラクト。  
  
-   エンドポイントのローカル実装の詳細を指定する一連の動作。  
  
 このトピックでは、このエンドポイントの構造体について説明し、WCF オブジェクト モデルでの表現方法について説明します。  
  
## <a name="the-structure-of-an-endpoint"></a>エンドポイントの構造  
 各エンドポイントの構造は次のとおりです。  
  
-   アドレス : アドレスは、エンドポイントを一意に識別し、サービスの潜在的ユーザーにそのエンドポイントの場所を示します。 WCF オブジェクト モデルで表されます、<xref:System.ServiceModel.EndpointAddress>クラスです。 <xref:System.ServiceModel.EndpointAddress> クラスには次のものが含まれます。  
  
    -   <xref:System.ServiceModel.EndpointAddress.Uri%2A> プロパティは、サービスのアドレスを表します。  
  
    -   <xref:System.ServiceModel.EndpointAddress.Identity%2A> プロパティは、サービスのセキュリティ ID とオプションのメッセージ ヘッダーのコレクションを表します。 オプションのメッセージ ヘッダーは、エンドポイントの識別またはエンドポイントとの対話のための、より詳細なアドレス指定情報を追加するために使用されます。  
  
     詳細については、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。  
  
-   バインディング : バインディングは、エンドポイントとの通信方法を指定します。 バインディングには、以下の項目が含まれます。  
  
    -   使用するトランスポート プロトコル (例 : TCP や HTTP)。  
  
    -   メッセージに使用するエンコーディング (例 : テキストやバイナリ)。  
  
    -   必要なセキュリティ要件 (例 : SSL メッセージ セキュリティや SOAP メッセージ セキュリティ)。  
  
     詳細については、次を参照してください。 [WCF のバインディングの概要](../../../../docs/framework/wcf/bindings-overview.md)です。 バインディングは、WCF オブジェクト モデルで抽象基本クラスで表される<xref:System.ServiceModel.Channels.Binding>です。 ほとんどのシナリオでは、システム指定のバインディングを使用できます。 詳細については、次を参照してください。[システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)です。  
  
-   コントラクト : コントラクトは、エンドポイントがクライアントに公開する機能を示します。 コントラクトは、以下の項目を指定します。  
  
    -   クライアントから呼び出すことができる操作。  
  
    -   メッセージの形式。  
  
    -   操作を呼び出すために必要な入力パラメーターまたはデータの型。  
  
    -   クライアントが予期できる処理メッセージまたは応答メッセージの種類。  
  
     詳細については、コントラクトを定義する、次を参照してください。[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)です。  
  
-   動作 : エンドポイントの動作を使用すると、サービス エンドポイントのローカル動作をカスタマイズできます。 エンドポイントの動作は、構築、WCFruntime プロセスに参加してこれを実現します。 エンドポイントの動作の一例は、<xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> プロパティです。このプロパティにより、SOAP アドレスまたは Web サービス記述言語 (WSDL) アドレスとは異なるリッスン アドレスを指定できます。 詳細については、次を参照してください。 [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)です。  
  
## <a name="defining-endpoints"></a>エンドポイントの定義  
 サービスのエンドポイントは、コードを使用して強制的に指定するか、構成を介して宣言として指定することができます。 詳細については、次を参照してください。[する方法: 構成でサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)と[する方法: コードでサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 このセクションでは、バインディング、エンドポイント、およびアドレスの目的を説明し、バインディングとエンドポイントの構成方法および `ClientVia` 動作と `ListenUri` プロパティの使用方法を示します。  
  
 [アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 WCF でのエンドポイントを指定する方法について説明します。  
  
 [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)  
 バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定する方法について説明します。  
  
 [コントラクト](../../../../docs/framework/wcf/feature-details/contracts.md)  
 コントラクトでサービスのメソッドが定義されるしくみについて説明します。  
  
 [方法 : 構成にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 構成にサービス エンドポイントを作成する方法について説明します。  
  
 [方法 : コード内にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 コード内にサービス エンドポイントを作成する方法について説明します。  
  
 [方法 : Svcutil.exe を使用してコンパイル済みサービス コードを検証する](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 使用してサービスをホストせず、サービスの実装と構成のエラーを検出する方法について説明、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。  
  
## <a name="see-also"></a>関連項目  
 [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)
