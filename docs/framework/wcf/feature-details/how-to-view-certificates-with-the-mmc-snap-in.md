---
title: '方法 : MMC スナップインを使用して証明書を参照する'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: d924121b9d9fa267fa7d1ada13c9dc5f5bf1523d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493351"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>方法 : MMC スナップインを使用して証明書を参照する
X.509 証明書は、広く使用されている資格情報です。 セキュリティで保護されたサービスやクライアントを作成する場合、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドなどのメソッドを使用して、クライアントやサービスの資格情報として使用する証明書を指定できます。 このメソッドでは、証明書を格納するストアや証明書を検索するときに使用する値など、さまざまなパラメーターが必要になります。 次の手順では、コンピューター上のストアを調べて適切な証明書を検索する方法を示します。  証明書の拇印を検索する方法の例は[方法: 証明書のサムプリントを取得 ](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md) を参照してください。  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>MMC スナップインで証明書を参照するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  `mmc` と入力して、ENTER キーを押します。 ローカル コンピューターのストアにある証明書を表示するには、管理者のロールが必要です。  
  
3.  **ファイル** メニューから **スナップインの追加/削除** をクリックします。  
  
4.  **[追加]** をクリックします。  
  
5.  **スタンドアロン スナップインの追加**ダイアログ ボックスで **証明書**を選択します。  
  
6.  **[追加]** をクリックします。  
  
7.  **証明書スナップイン**ダイアログ ボックスで **コンピューター アカウント** を選択し **次** をクリックします。 必要に応じて、**ユーザー アカウント** または　**サービス アカウント** を選択できます。 そのコンピューターの管理者でない場合は、自分のユーザー アカウントの証明書のみを管理できます。  
  
8.  **コンピューターの選択** ダイアログ ボックスで **完了** をクリックします。  
  
9. **スタンドアロン スナップインの追加** ダイアログ ボックスで **閉じる** をクリックします。  
  
10. **スナップインの追加と削除** ダイアログ ボックスで **OK** をクリックします。  
  
11. **コンソール ルート** ウィンドウで **証明書 (ローカル コンピューター)** をクリックして、コンピューターの証明書ストアを表示します。  
  
12. 任意。 必要に応じて、自分のアカウントの証明書を表示する場合は、手順 3. ～ 6. を繰り返します。 手順 7. では **コンピューター アカウント** を選択する代わりに **ユーザー アカウント** をクリックして、手順 8. ~ 10. を繰り返します。  
  
13. 任意。 **ファイル** メニューのをクリックして**保存**または**名前を付けて保存**です。 再利用できるようにコンソール ファイルを保存します。  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Internet Explorer を使用した証明書の表示  
 Internet Explorer を使用して、証明書を表示、エクスポート、インポート、または削除することもできます。  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Internet Explorer で証明書を表示するには  
  
1.  Internet Explorer で、をクリックして**ツール**をクリックし、**インターネット オプション**を表示する、**インターネット オプション** ダイアログ ボックス。  
  
2.  クリックして、**コンテンツ**タブです。  
  
3.  **証明書**をクリックして**証明書**です。  
  
4.  任意の証明書の詳細を表示し、証明書を選択し、クリックして**ビュー**です。  
  
## <a name="see-also"></a>関連項目  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [方法 : 開発中に使用する一時的な証明書を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [方法 : 証明書のサムプリントを取得する](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
