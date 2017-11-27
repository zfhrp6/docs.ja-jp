---
title: "Windows ストア アプリのネットワーク分離"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b6c0665a379f02a74bd0f3631aa26b41dd6ece5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="network-isolation-for-windows-store-apps"></a>Windows ストア アプリのネットワーク分離
<xref:System.Net>、<xref:System.Net.Http>、<xref:System.Net.Http.Headers> の各名前空間のクラスは、Windows ストア アプリまたはデスクトップ アプリを開発するために使用できます。 Windows ストア アプリで使用する場合、これらの名前空間のクラスは、[!INCLUDE[win8](../../../includes/win8-md.md)]で使用されるアプリケーション セキュリティ モデルの一部であるネットワーク分離の影響を受けます。 システムでネットワーク アクセスが許可されるように、Windows ストア アプリのアプリ マニフェストで適切なネットワーク機能を有効にする必要があります。  
  
## <a name="checklist-for-network-isolation"></a>ネットワーク分離のチェックリスト  
 Windows ストア アプリに対してネットワークの分離が適切に構成されているかどうかを、このチェックリストを使って確認してください。  
  
1.  アプリが必要とするネットワーク アクセス要求の方向を確認します。 これには、クライアント側から開始される送信要求と、受信側が送信を要求していない受信要求とがあります。両方の種類のネットワーク要求を組み合わせたものもあります。  
  
2.  アプリの通信相手となるネットワーク リソースの種類を確認します。 アプリの通信相手は、ホーム ネットワークまたは職場ネットワーク上の信頼済みリソースである場合があります。 または、インターネット上のリソースと通信することが必要な場合があります。 その両方の種類のネットワーク リソースにアクセスする場合もあります。  
  
3.  アプリ マニフェストで、必要最小限のネットワーク分離機能を構成します。  
  
4.  アプリを展開して実行し、トラブルシューティングのためのネットワーク分離ツールを使用してテストします。  
  
 ネットワーク機能の構成と、ネットワーク分離のトラブルシューティングに使用する分離ツールの詳細については、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 開発者向けドキュメントで、[ネットワーク分離の機能を構成する方法](http://go.microsoft.com/fwlink/?LinkID=228265)に関するページを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Web サービスに接続します。](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [ガイドラインとネットワーク分離のためのチェックリスト](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [クイック スタート: は、HttpClient を使用して接続します。](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [HttpClient のハンドラーを使用する方法](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [HttpClient の接続をセキュリティで保護する方法](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [HttpClient のサンプル](http://go.microsoft.com/fwlink/?LinkId=242550)
