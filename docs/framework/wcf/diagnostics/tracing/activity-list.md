---
title: "アクティビティ リスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c3b478d88eff022d8cb28f4123291f4662644ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="activity-list"></a>アクティビティ リスト
ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] で定義されたすべてのアクティビティを示します。  
  
> [!NOTE]
>  また、ユーザー トレースをグループ化するために、アクティビティをプログラムによって定義することもできます。 詳細については、次を参照してください。[ユーザー コード トレースの出力](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)です。  
  
## <a name="servicemodel-activities"></a>ServiceModel アクティビティ  
 主要な使用シナリオに対応するすべてのアクティビティを次の表に示します。  
  
|ラベル|アクティビティ名|アクティビティの種類|説明|  
|-----------|-------------------|-------------------|-----------------|  
|A、M|アンビエント アクティビティ|N/A (ServiceModel によって制御されません)|ServiceModel コード (クライアント側またはサーバー側) を呼び出す前に、ID が TLS に設定されるアクティビティ。<br /><br /> 例 : [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] クライアントで open が呼び出されるか、serviceHost.open が呼び出されるアクティビティ。|  
|B|構成体<br /><br /> 構築する。 ContractType: '[種類]'。|構成体||  
|C|開く<br /><br /> [ClientBase &#124;です。ChannelFactory] です。 ContractType: '[種類]'。|開く||  
|I|[ClientBase &#124; を閉じるChannelFactory] です。 ContractType: '[種類]'。|閉じる||  
|M|ServiceHost を構築する。 ServiceType: '[種類]'。|構成体||  
|N|ServiceHost を開く。 ServiceType: '[種類]'。|開く||  
|Z|ServiceHost を閉じる。 ServiceType: '[種類]'。|閉じる||  
|O|'[アドレス]' でリッスンする。|ListenAt|このアクティビティと次のアクティビティはトランスポート固有です。 ListenAt アクティビティは、チャネル リスナーがリッスンするアドレスにマップされるコンテンツを表します。 MSMQ の場合は、キューが 1 つのアドレスにマップされるため、これはキューそのものです。 このアクティビティは、接続指向のトランスポートの場合は受信接続をリッスンし、MSMQ の場合は MSMQ メッセージをリッスンします。 このアクティビティは ServiceHost.Open() の間に作成され、リスナーの作成と破棄、およびすべての ReceiveBytes アクティビティへの転送に関連するトレースを格納します。|  
|P|接続 '[アドレス]' でのバイトを受信する。 MSMQ メッセージを受信する。|ReceiveBytes|このアクティビティでは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージを最終的に取得するデータが処理されます。 接続指向のトランスポートまたは http の場合は、受信バイトを待ちます。 TCP/名前付きパイプの場合は、接続が作成されるときにアクティビティが作成されるため、このアクティビティの有効期間は接続の有効期間と等しくなります。 http の場合、これはメッセージ要求の有効期間と等しく、メッセージが送信されるときにアクティビティが作成されます。 このアクティビティは、接続の作成と破棄 (該当する場合)、およびすべてのメッセージ (オブジェクト) 処理アクティビティへの転送に関連するトレースを格納します。<br /><br /> MSMQ の場合、これは MSMQ メッセージが取得されるアクティビティです。|  
|Q|メッセージ [番号] を処理する  ([番号] は、1 で始まる、単調に増加する値です)。|ProcessMessage|受信メッセージを処理します。 このアクティビティは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージ オブジェクトを形成するためのすべてのデータ (バイト、MSMQ メッセージ) が受信されると開始されます。 このアクティビティに格納されたトレースは、ヘッダー処理を扱います。<br /><br /> ディスパッチ可能なメッセージが形成されると、対応するアクティビティ ID を検索した後で ServiceHost ProcessAction アクティビティとの間で切り替わります。|  
|D、S|アクション '[アクション]' を処理する。|ProcessAction|受信時にはユーザー コードにメッセージをディスパッチし、送信時には逆の順序でメッセージをディスパッチするために、トランスポート/セキュリティ/RM スタックを通じてメッセージを処理します。<br /><br /> 「アクティビティ伝達」; を介してメッセージ ヘッダーで送信された場合、サーバーでこのアクティビティが伝達されたアクティビティ ID を使用します。それ以外の場合、新しい GUID が作成されます。<br /><br /> 要求/応答コントラクトに対する応答メッセージも、そのアクティビティで処理されます。|  
|T|'[IContract.Operation]' を実行する。|ExecuteUserCode|サービス側でディスパッチ後にユーザー コードを実行します。 このアクティビティは、ユーザー指定のコードと ServiceHost コードを区別するための境界を提供します。|  
  
## <a name="security-activities"></a>セキュリティ アクティビティ  
 セキュリティに関連するすべてのアクティビティを次の表に示します。  
  
|アクティビティ名|アクティビティの種類|説明|  
|-------------------|-------------------|-----------------|  
|セキュリティで保護されたセッションをセットアップする|SetupSecurity|クライアント側だけに存在します。 認証およびセキュリティ コンテキストの設定のためのすべての "RST*/SCT 交換" を格納します。 場合`propagateActivity` = `true`、このアクティビティは、サービスの対応するプロセス アクション RST にマージ\*/SCT アクティビティ。|  
|セキュリティで保護されたセッションを閉じる|SetupSecurity|クライアント側に存在します。 セキュリティで保護されたセッションを閉じるための "メッセージ交換のキャンセル" を格納します。 場合`propagateActivity` = `true`、このアクティビティは、サービスのプロセス アクション「キャンセル」とマージします。|  
  
 COM+ に関連するすべてのアクティビティを次の表に示します。  
  
|アクティビティ名|アクティビティの種類|説明|  
|-------------------|-------------------|-----------------|  
|COM+ インスタンスを作成する|TransferToCOMPlus|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] コードからの COM+ 呼び出しごとに 1 つのアクティビティ インスタンス|  
|これを実行すると COM +\<操作 >|TransferToCOMPlus|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] コードからの COM+ 呼び出しごとに 1 つのアクティビティ インスタンス|  
  
## <a name="wmi-activities"></a>WMI アクティビティ  
 WMI に関連するすべてのアクティビティを次の表に示します。  
  
|アクティビティ名|アクティビティの種類|説明|  
|-------------------|-------------------|-----------------|  
|WMI Get|WMIGetObject|ユーザーは、WMI からデータを取得しています。|  
|WMI Put|WmiPutInstance|ユーザーは、WMI でデータを更新しています。|
