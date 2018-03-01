---
title: "方法 : MMC スナップインを使用して証明書を参照する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 582eaef518e10acb4c4c356226ce0be24d1b4c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>方法 : MMC スナップインを使用して証明書を参照する
X.509 証明書は、広く使用されている資格情報です。 セキュリティで保護されたサービスやクライアントを作成する場合、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドなどのメソッドを使用して、クライアントやサービスの資格情報として使用する証明書を指定できます。 このメソッドでは、証明書を格納するストアや証明書を検索するときに使用する値など、さまざまなパラメーターが必要になります。 次の手順では、コンピューター上のストアを調べて適切な証明書を検索する方法を示します。 証明書の拇印を検索の例は、次を参照してください。[する方法: 証明書のサムプリントを取得](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)です。  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>MMC スナップインで証明書を参照するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  型`mmc`ENTER キーを押します。 ローカル コンピューターのストアにある証明書を表示するには、管理者のロールが必要です。  
  
3.  **ファイル** メニューのをクリックして**スナップインの追加/削除**です。  
  
4.  **[追加]**をクリックします。  
  
5.  **スタンドアロン スナップインの追加**ダイアログ ボックスで、**証明書**です。  
  
6.  **[追加]**をクリックします。  
  
7.  **証明書スナップイン**ダイアログ ボックスで、**コンピューター アカウント** をクリック**次**です。 必要に応じて、選択**ユーザー アカウント**または**サービス アカウント**です。 そのコンピューターの管理者でない場合は、自分のユーザー アカウントの証明書のみを管理できます。  
  
8.  **コンピューターの選択**ダイアログ ボックスで、をクリックして**完了**です。  
  
9. **スタンドアロン スナップインの追加**ダイアログ ボックスで、をクリックして**閉じる**です。  
  
10. **スナップインの追加と削除**ダイアログ ボックスで、をクリックして**OK**です。  
  
11. **コンソール ルート**ウィンドウで、をクリックして**証明書 (ローカル コンピューター)**コンピューターのストアに証明書を表示します。  
  
12. 任意。 自分のアカウントの証明書を表示するには、手順 3. ～ 6. を繰り返し、 手順 7. で選択する代わりに**コンピューター アカウント**をクリックして**ユーザー アカウント**手順 8. ~ 10. を繰り返します。  
  
13. 任意。 **ファイル** メニューのをクリックして**保存**または**名前を付けて保存**です。 再利用できるようにコンソール ファイルを保存します。  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Internet Explorer を使用した証明書の表示  
 Internet Explorer を使用して、証明書を表示、エクスポート、インポート、または削除することもできます。  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Internet Explorer で証明書を表示するには  
  
1.  Internet Explorer で、をクリックして**ツール**をクリックし、**インターネット オプション**を表示する、**インターネット オプション** ダイアログ ボックス。  
  
2.  クリックして、**コンテンツ**タブです。  
  
3.  **証明書**をクリックして**証明書**です。  
  
4.  任意の証明書の詳細を表示し、証明書を選択し、クリックして**ビュー**です。  
  
## <a name="see-also"></a>参照  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [方法 : 開発中に使用する一時的な証明書を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [方法 : 証明書のサムプリントを取得する](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
