---
title: "CustomPeerResolverService 内部 : クライアント登録 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# CustomPeerResolverService 内部 : クライアント登録
メッシュ内の各ノードは、`Register` 関数を介してエンドポイント情報をリゾルバー サービスに公開します。  リゾルバー サービスは、登録レコードとしてこの情報を保存します。  このレコードには、ノードの一意の識別子 \(RegistrationID\) およびエンドポイント情報 \`\(PeerNodeAddress\) が格納されます。  
  
## 古くなったレコードと有効期限  
 ノードがメッシュからの離脱時に `Unregister` 関数を呼び出し、それによってリゾルバー サービスで登録エントリが削除されるのが理想的ですが、  `Unregister` を呼び出す前に、ノードがシャットダウンしたりアクセスできなくなったりするために、古い登録レコードが残ることがあります。  
  
 リゾルバー サービス内の古くなったレコードは、接続障害の原因となる場合があります。  メッシュへの接続時に、ノードがリゾルバー サービスから古い接続情報を受け取った場合、メッシュへの参加に時間がかかることがあります。  古いレコードはメモリも消費します。  効率的なクリーンアップ処理がなければ、登録の保存に使用したキャッシュがオーバーフローしてリゾルバー サービスがクラッシュする可能性があります。  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> は、各レコードを有効期限 \(DateTime\) でマークし、レコードの一部としてその情報を保存します。  サービスは、有効期限を使用してレコードを識別します。  カスタム実装でも同様な処理が必要です。  
  
## RefreshInterval および CleanupInterval  
 `RefreshInterval` の <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> プロパティは、サービスの登録ルックアップ テーブルで登録レコードが有効である期間を定義します。  特定のレコードについて、このプロパティで指定された時間が経過すると、そのレコードは古くなり、削除対象としてマークされます。  
  
 `CleanupInterval` の <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> プロパティは、古くなったレコードの検索と削除の頻度をサービスに指示します。  `CleanupInterval` は、サービスに設定されている `RefreshInterval` 以上の時間に設定する必要があります。  
  
 独自のリゾルバー サービスを実装するためには、古い登録レコードを削除するメンテナンス関数を作成する必要があります。  これにはいくつかの方法があります。  
  
-   定期的な管理 : 定期的に鳴るようにタイマーを設定し、データ ストアを調べて古いレコードを削除します。  <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> では、この方法を使用します。  
  
-   パッシブ削除 : 古くなったレコードを一定間隔で検索する代りに、サービスが既に別の関数を実行中の場合に古くなったレコードを識別し、削除できます。  この方法では、リゾルバー クライアントからの要求に対する応答時間が遅くなる可能性がありますが、タイマーの必要がなくなるほか、一部のノードが `Unregister` を呼び出さずに離脱することが予想される場合には効果的です。  
  
## RegistrationLifetime および Refresh  
 リゾルバー サービスに登録されると、ノードはサービスから <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> オブジェクトを受け取ります。  このオブジェクトには、`RegistrationLifetime` プロパティが含まれます。このプロパティは、登録の期限が切れてリゾルバー サービスによって削除されるまでに、どれだけの時間があるかを示します。  たとえば、`RegistrationLifetime` が 2 分である場合、レコードが古くならず、削除されないようにするためには、ノードは 2 分以内に `Refresh` を呼び出す必要があります。  リゾルバー サービスは `Refresh` 要求を受け取ると、レコードを検索し、有効期限をリセットします。  Refresh は、<xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> プロパティのある `RegistrationLifetime` オブジェクトを返します。  
  
## 参照  
 [ピア リゾルバー](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)