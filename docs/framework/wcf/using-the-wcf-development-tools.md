---
title: WCF 開発ツールの使用
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: bfe71c8f4ee515e1895f27166bcb5931806dabea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-wcf-development-tools"></a>WCF 開発ツールの使用
このセクションの説明の開発に役立つ Visual Studio 開発ツール、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス。  
  
 基礎としてテンプレートを Visual Studio を使用するにはすばやく独自のサービスをビルドしを使用して[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービスの自動ホストと[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]をデバッグし、サービスをテストするクライアントをテストします。 これらのツールによって、高速でシームレスなデバッグとテストのサイクルが実現し、初期の段階においてホスト モデルのコミットが必要なくなります。  
  
## <a name="the-wcf-developer-tools"></a>WCF の開発者用ツール  
 [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Visual Studio で、定義済みの Visual Studio プロジェクトと項目テンプレートを使用するには迅速に構築[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービスや周辺アプリケーションです。  
  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービスの自動ホスト (WcfSvcHost.exe) では、Visual Studio デバッガーを自動的にホストし、実装しているサービスをテストする (F5) を起動することができます。 その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアント (wcfTestClient.exe) または独自のクライアントを使用してサービスをテストし、潜在的なエラーを見つけて修正できます。  
  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアント (WcfTestClient.exe) は GUI ツールです。このツールを使用すると、任意の型のパラメーターを入力し、その入力をサービスに送信して、サービスから返される応答を表示できます。 このツールを [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホストと組み合わせて使用すると、シームレスにサービスをテストできるようになります。  
  
 [XML からのデータ型クラスの生成](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 クリップボードに格納されている XML データは、コード ページに貼り付けることができます。 データで定義されているクラスは、コード型に変換されます。  
  
## <a name="using-the-tools-without-administrator-privilege"></a>管理特権を必要としないツールの使用  
 開発する管理者特権のないユーザーを有効にする[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]、ACL (アクセス制御リスト) が作成されたサービス名前空間の"http://+:8731/Design_Time_Addresses"Visual Studio のインストール中にします。 この ACL は (UI) に設定され、コンピューターにログオンしているすべての対話ユーザーが含まれます。 管理者は、この ACL にユーザーを追加または削除したり、追加のポートを開いたりできます。この ACL によって、既定の構成で、WCF テンプレートまたは WF テンプレートでデータを送受信できるようになります。 また、ユーザーは、管理特権が付与されていなくても、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホスト (wcfSvcHost.exe) を使用できるようになります。  
  
 システム特権のある管理者アカウントで [!INCLUDE[wv](../../../includes/wv-md.md)] の Netsh.exe ツールを使用すると、アクセスを変更できます。 Netsh.exe の使用例を次に示します。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe の詳細については、次を参照してください。 [Netsh.exe ツールとコマンド ライン スイッチを使用する方法](http://go.microsoft.com/fwlink/?LinkId=97877)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
