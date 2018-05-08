---
title: 拡張機能の概要
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: 142478352c8eb1c893d8b95b960c6079f735fa06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-extensibility"></a>拡張機能の概要
Windows Communication Foundation (WCF) アプリケーション モデルは、分散アプリケーションの通信要件の大部分を解決するために設計されています。 ただし、既定のアプリケーション モデルとシステム提供の実装でサポートされないシナリオが必ず存在します。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の拡張モデルでは、アプリケーション モデル全体の置き換えに至るまでのすべてのレベルでシステム動作を変更できるようにすることによって、カスタム シナリオをサポートします。 ここでは、拡張のさまざまな領域を提示し、各領域の詳細について説明します。  
  
## <a name="areas-to-extend"></a>拡張する領域  
 次の領域を拡張できます。  
  
-   アプリケーション ランタイム。 ここでは、アプリケーションについて、メッセージのディスパッチと処理を拡張します。 この領域には、セキュリティ システム、メタデータ システム、シリアル化システム、およびアプリケーションを基になるチャネル システムに接続するためのバインディングとバインド要素も含まれます。  
  
-   チャネルとチャネル ランタイム。 ここでは、メッセージ レベルで機能するシステムを拡張し、プロトコル、トランスポート、およびエンコーディングのサポートを提供します。  
  
-   ホスト ランタイム。 ここでは、チャネルおよびアプリケーション ランタイムとのホスト アプリケーション ドメインの関係を拡張します。  
  
### <a name="extending-the-application-runtime"></a>アプリケーション ランタイムの拡張  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションでは、対応するチャネル宛てのメッセージとアプリケーション宛てのメッセージを区別します。 チャネル メッセージは、セキュリティで保護されたメッセージ交換の確立や、信頼できるセッションの確立など、特定のチャネル関連の機能をサポートします。 このメッセージは、アプリケーション ランタイムでは使用できません。このメッセージは、アプリケーション層が関係する前に処理されます。  
  
 アプリケーション メッセージは、ユーザーまたはユーザーの顧客が作成したクライアントまたはサービスの操作向けのデータを含んでいます。 このメッセージは、必要に応じて、メッセージまたはオブジェクトの形でアプリケーション レベルの拡張システムで使用できます。  
  
 すべてのメッセージはチャネル システムを通過しますが、アプリケーション メッセージだけがチャネル システムからアプリケーションに渡されます。 新しいチャネル レベルの機能を作成するには、チャネル システムを拡張する必要があります。 新しいアプリケーション レベルの機能を作成するには、サービスまたはクライアントのランタイム (それぞれディスパッチャーとチャネル ファクトリ) を拡張する必要があります。 アプリケーション ランタイムの拡張の詳細については、次を参照してください。 [ServiceHost を拡張すると、サービス モデル レイヤー](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)です。  
  
#### <a name="extending-security"></a>セキュリティの拡張  
 トークンや資格情報などのカスタム セキュリティ機構を作成するには、セキュリティ システムを拡張する必要があります。 詳細については、次を参照してください。[拡張セキュリティ](../../../docs/framework/wcf/extending/extending-security.md)です。  
  
#### <a name="extending-metadata"></a>メタデータの拡張  
 メタデータを既定以外の方法で公開するには、メタデータ システムを拡張する必要があります。 詳細については、次を参照してください。[メタデータ システムの拡張](../../../docs/framework/wcf/extending/extending-the-metadata-system.md)です。  
  
#### <a name="extending-serialization"></a>シリアル化の拡張  
 カスタム エンコーダーの作成、データ サロゲートの提供、または転送されるデータのカスタマイズに関するその他の作業を行うには、シリアル化システムを拡張する必要があります。 詳細については、次を参照してください。[を拡張するエンコーダーとシリアライザー](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)です。  
  
#### <a name="extending-bindings"></a>バインディングの拡張  
 トランスポート チャネルまたはプロトコル チャネルをアプリケーション層に関連付けるには、バインディング システムを拡張する必要があります。 詳細については、次を参照してください。[バインディングの拡張](../../../docs/framework/wcf/extending/extending-bindings.md)です。  
  
### <a name="extending-the-channel-system"></a>チャネル システムの拡張  
 プロトコルの機能またはカスタム トランスポートをサポートするチャネルを作成するを参照してください。 [、チャネル レイヤの拡張](../../../docs/framework/wcf/extending/extending-the-channel-layer.md)です。  
  
### <a name="extending-the-service-hosting-system"></a>サービス ホスト システムの拡張  
 サービス全体のアプリケーション モデルを変更するには、<xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> クラスを拡張する必要があります。 詳細については、次を参照してください。 [ServiceHost を拡張すると、サービス モデル レイヤー](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)です。  
  
 ホスト アプリケーション ドメインとサービス ホストとの関係を変更するには、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> クラスを拡張する必要があります。 詳細については、次を参照してください。[ホストを使用して ServiceHostFactory の拡張](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF の拡張](../../../docs/framework/wcf/extending/index.md)
